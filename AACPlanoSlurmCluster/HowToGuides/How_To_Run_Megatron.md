# How To Run Megatron on Plano Slurm Cluster 
- Examples below use `1CN96C8G1H_4IB_MI250_Ubuntu22` slurm partition which has MI250 compute nodes.
# Setup Megatron Environment Using Conda  
Allocate and SSH to a node from the partition `1CN96C8G1H_4IB_MI250_Ubuntu22`
```
salloc --exclusive --mem=0 --gres=gpu:8 -p 1CN96C8G1H_4IB_MI250_Ubuntu22
```
In the SSH session, load ROCm 5.5.1 Environment
```
module load rocm-5.5.1
```
Load anaconda environment 
```
module load anaconda3/4.12.0 
```
```
. $CONDA_ROOT/etc/profile.d/conda.sh
```
Create conda environment `megatron` with python 3.8
```
conda create -n megatron python=3.8 -y
```
Activate the conda environment 
```
conda activate megatron
```
Install Pytorch 2.0.1 + ROCm 5.4.2 whl
```
pip3 install --no-cache-dir torch torchvision torchaudio --index-url https://download.pytorch.org/whl/rocm5.4.2
```
Clone and Install Apex from sources  
```
cd $HOME
```
```
git clone https://github.com/ROCmSoftwarePlatform/apex.git
```
```
cd apex/
```
```
python setup.py install --cpp_ext --cuda_ext
```
Install the latest DeepSpeed
```
pip3 install --no-cache-dir deepspeed
```
Install megatron dependencies 
```
pip3 install --no-cache-dir six
pip3 install --no-cache-dir regex
pip3 install --no-cache-dir pybind11
```
Create a directory for checkpoints
```
mkdir -p $HOME/checkpoints/megatron
```
# Clone `Megatron-DeepSpeed` Repository
```
cd $HOME
```
```
git clone https://github.com/microsoft/Megatron-DeepSpeed.git
```
```
cd $HOME/Megatron-DeepSpeed/
```
```
git checkout 1f640c00c115eee9cd8515db80f8c92a4c24e9ca
```
# Setup the `pretrain_gpt_distributed_slurm.sh` Script Example
Make a copy of `$HOME/Megatron-DeepSpeed/examples/pretrain_gpt_distributed.sh`
```
cp $HOME/Megatron-DeepSpeed/examples/pretrain_gpt_distributed.sh $HOME/Megatron-DeepSpeed/examples/pretrain_gpt_distributed_slurm.sh
```
Edit the newly copied script `$HOME/Megatron-DeepSpeed/examples/pretrain_gpt_distributed_slurm.sh`
```
vim $HOME/Megatron-DeepSpeed/examples/pretrain_gpt_distributed_slurm.sh
```
with the following content
- Data that will be used is Megatron-LM-v1.1.5-ZeRO3 which can be found under the `/shareddata` storage `/shareddata/DeepSpeed/Megatron-LM-v1.1.5-ZeRO3/`
- `BASE_PATH` will be pointed to the directory `/shareddata/DeepSpeed/Megatron-LM-v1.1.5-ZeRO3/`
- `DATA_PATH` will be pointed to `$BASE_PATH/my-gpt2_text_document`
- `VOCAB_FILE` will be pointed to `$BASE_PATH/gpt2-vocab.json`
- `MERGE_FILE` will be pointed to `$BASE_PATH/gpt2-merges.txt`
- `CHECKPOINT_PATH` will be pointed to the directory we created `$HOME/checkpoints/megatron`
```
#! /bin/bash

# Runs the "345M" parameter model

node_list=$(scontrol show hostnames $SLURM_JOB_NODELIST)
node_array=(${node_list})
master_node=${node_array[0]}

GPUS_PER_NODE=${SLURM_GPUS_ON_NODE}
# Change for multinode config
MASTER_ADDR=${master_node}
NNODES=${SLURM_NNODES}
NODE_RANK=${SLURM_NODEID}
WORLD_SIZE=$(($GPUS_PER_NODE*$NNODES))

BASE_PATH=/shareddata/DeepSpeed/Megatron-LM-v1.1.5-ZeRO3/
DATA_PATH=$BASE_PATH/my-gpt2_text_document
VOCAB_FILE=$BASE_PATH/gpt2-vocab.json
MERGE_FILE=$BASE_PATH/gpt2-merges.txt
CHECKPOINT_PATH=$HOME/checkpoints/megatron

DISTRIBUTED_ARGS="--nproc_per_node=$GPUS_PER_NODE --nnodes=$NNODES --rdzv_id=100 --rdzv_backend=c10d --rdzv_endpoint=${MASTER_ADDR}:29400"

torchrun $DISTRIBUTED_ARGS \
       pretrain_gpt.py \
       --num-layers 24 \
       --hidden-size 1024 \
       --num-attention-heads 16 \
       --micro-batch-size 8 \
       --global-batch-size 64 \
       --seq-length 1024 \
       --max-position-embeddings 1024 \
       --train-iters 1000 \
       --lr-decay-iters 100 \
       --save $CHECKPOINT_PATH \
       --load $CHECKPOINT_PATH \
       --data-path $DATA_PATH \
       --vocab-file $VOCAB_FILE \
       --merge-file $MERGE_FILE \
       --data-impl mmap \
       --split 949,50,1 \
       --distributed-backend nccl \
       --lr 0.00015 \
       --lr-decay-style cosine \
       --min-lr 1.0e-5 \
       --weight-decay 1e-2 \
       --clip-grad 1.0 \
       --lr-warmup-fraction .01 \
       --checkpoint-activations \
       --log-interval 100 \
       --save-interval 10000 \
       --eval-interval 1000 \
       --eval-iters 10 \
       --fp16

```
# Single Node Multi GPU/GCD Megatron Test Example
Allocate and SSH to a node from the partition `1CN96C8G1H_4IB_MI250_Ubuntu22`
```
salloc --exclusive --mem=0 --gres=gpu:8 -p 1CN96C8G1H_4IB_MI250_Ubuntu22 
```
In the SSH session, load ROCm 5.5.1 Environment
```
module load rocm-5.5.1
```
Load anaconda environment 
```
module load anaconda3/4.12.0 
```
```
. $CONDA_ROOT/etc/profile.d/conda.sh
```
Acitvate conda environment `megatron`
```
conda activate megatron 
```
Change to `$HOME/Megatron-DeepSpeed` directory
```
cd $HOME/Megatron-DeepSpeed
```
Run `pretrain_gpt_distributed_slurm.sh` on 1 node
```
srun -N 1 -n 1 bash $HOME/Megatron-DeepSpeed/examples/pretrain_gpt_distributed_slurm.sh
```
# Multinode Multi GPU/GCD Megatron Test Example
Allocate and SSH to a node from the 2-node cluster from partition 1CN96C8G1H_4IB_MI250_Ubuntu22
```
salloc --exclusive --mem=0 --gres=gpu:8 -p 1CN96C8G1H_4IB_MI250_Ubuntu22 -N 2
```
In the SSH session, load ROCm 5.5.1 Environment
```
module load rocm-5.5.1 
```
Load anaconda environment 
```
module load anaconda3/4.12.0 
```
```
. $CONDA_ROOT/etc/profile.d/conda.sh
```
Acitvate conda environment `megatron`
```
conda activate megatron 
```
Change to `$HOME/Megatron-DeepSpeed` directory
```
cd $HOME/Megatron-DeepSpeed
```
Change `--global-batch-size` to `128` in the example script `pretrain_gpt_distributed_slurm.sh`
```
vim $HOME/Megatron-DeepSpeed/examples/pretrain_gpt_distributed_slurm.sh
```
Run `pretrain_gpt_distributed_slurm.sh` on 2 nodes
```
srun -N 2 -n 2 bash $HOME/Megatron-DeepSpeed/examples/pretrain_gpt_distributed_slurm.sh
```
