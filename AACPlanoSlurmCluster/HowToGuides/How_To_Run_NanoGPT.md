# How To Build and Run NanoGPT on Plano Slurm Cluster
- https://github.com/karpathy/nanoGPT
- Examples below use `1CN128C8G2H_2IB_MI210_Ubuntu22` slurm partition which has MI210 compute nodes. 
# Setup Environment 
Allocate and SSH to a node from the partition `1CN128C8G2H_2IB_MI210_Ubuntu22`
```
salloc --exclusive --mem=0 --gres=gpu:8 -p 1CN128C8G2H_2IB_MI210_Ubuntu22
```
In the SSH session, load ROCm 5.5.1 Environment
```
module load rocm-5.5.1
```
Create conda environment 
```
module load anaconda3/4.12.0
```
```
. $CONDA_ROOT/etc/profile.d/conda.sh
```
```
conda create -n nano python=3.8 -y 
```
```
conda activate nano 
```
Install Pytorch 
```
pip3 --no-cache-dir install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/rocm5.4.2
```
Install nanoGPT dependencies
```
pip3 install --no-cache-dir numpy transformers datasets tiktoken wandb tqdm
```
Clone nanoGPT git repository 
```
git clone https://github.com/karpathy/nanoGPT.git
```
Change to `nanoGPT` directory 
```
cd $HOME/nanoGPT/
```
Prepare GPT shakespeare character dataset 
```
python3 data/shakespeare_char/prepare.py
```
Train GPT shakespeare character data 
```
python3 train.py config/train_shakespeare_char.py
```
Sample the model that was trained 
```
python3 sample.py --out_dir=out-shakespeare-char
```
# Reproducing GPT-2 
Prepare OpenWebText dataset 
```
python3 data/openwebtext/prepare.py
```
Train GPT-2 using torchrun  
```
torchrun --nnodes=1 --standalone --nproc_per_node=8 train.py config/train_gpt2.py
```
