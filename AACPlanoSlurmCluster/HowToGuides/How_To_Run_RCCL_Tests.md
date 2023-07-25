# How To Build and Run RCCL Tests on Plano Slurm Cluster
- Examples below use `1CN96C8G1H_4IB_MI250_Ubuntu22` slurm partition which has MI250 compute nodes. 
# Clone and Build RCCL Tests
Allocate and SSH to a node from the partition `1CN96C8G1H_4IB_MI250_Ubuntu22`
```
salloc --exclusive --mem=0 --gres=gpu:8 -p 1CN96C8G1H_4IB_MI250_Ubuntu22
```
In the SSH session, load ROCm 5.6.0 Environment
```
module load rocm-5.6.0 
```
Clone rccl-tests git repository 
```
cd $HOME
git clone https://github.com/ROCmSoftwarePlatform/rccl-tests.git
```
Change to `rccl-tests` directory 
```
cd $HOME/rccl-tests/
```
Compile program with MPI 
```
./install.sh --mpi --mpi_home=$MPI_HOME --rccl_home=$ROCM_PATH/rccl
```
# Single Node Multi GPU RCCL Test Example
Allocate and SSH to a node from the partition `1CN96C8G1H_4IB_MI250_Ubuntu22`
```
salloc --exclusive --mem=0 --gres=gpu:8 -p 1CN96C8G1H_4IB_MI250_Ubuntu22
```
In the SSH session, load ROCm 5.6.0 Environment
```
module load rocm-5.6.0 
```
Change to `$HOME/rccl-tests/build` directory 
```
cd $HOME/rccl-tests/build
```
Run all_reduce_perf on 8 GPUs/GCDs
```
mpirun -np 8 --mca coll_hcoll_enable 0 --mca btl ^self,vader,openib -x NCCL_IB_PCI_RELAXED_ORDERING=1 -x NCCL_NET_GDR_LEVEL=3 -x UCX_IB_PCI_RELAXED_ORDERING=on -x UCX_TLS=self,sm,rc_x -x NCCL_IB_HCA=mlx5_0:1,mlx5_2:1,mlx5_4:1,mlx5_6:1  $HOME/rccl-tests/build/all_reduce_perf -b 8 -e 16G -f 2 -g 1 -c 0
```

# Multinode Multi GPU/GCD RCCL Tests Example 
Allocate and SSH to a node from the 2-node cluster from partition `1CN96C8G1H_4IB_MI250_Ubuntu22`
```
salloc --exclusive --mem=0 --gres=gpu:8 -p 1CN96C8G1H_4IB_MI250_Ubuntu22 -N 2
```
In the SSH session, load ROCm 5.6.0 Environment
```
module load rocm-5.6.0 
```
Change to `$HOME/rccl-tests/build` directory 
```
cd $HOME/rccl-tests/build
```
Get list of nodes currently allocated
```
scontrol show hostname $SLURM_NODELIST
```
Example Output: 
```
ubb-r09-11
ubb-r09-12
```
Run all_reduce_perf on 8 GPUs/GCDs on each node of the 2-node cluster. Use `-H` option to specify the `$SLURM_NODELIST`
```
mpirun -np 16 -H ubb-r09-11:8,ubb-r09-12:8 --mca coll_hcoll_enable 0 --mca btl ^self,vader,openib -x NCCL_IB_PCI_RELAXED_ORDERING=1 -x NCCL_NET_GDR_LEVEL=3 -x UCX_IB_PCI_RELAXED_ORDERING=on -x UCX_TLS=self,sm,rc_x -x NCCL_IB_HCA=mlx5_0:1,mlx5_2:1,mlx5_4:1,mlx5_6:1  $HOME/rccl-tests/build/all_reduce_perf -b 8 -e 16G -f 2 -g 1 -c 0
```
