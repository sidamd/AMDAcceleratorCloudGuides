***

# Quick Start SSH to AAC Plano Slurm Cluster User Guide

***

# How to Log in to the AAC Plano Slurm Cluster
Use `ssh` to login to the AAC Plano Slurm Cluster using your registered `userid` with SSH key
```
ssh registered-userid@aac1.amd.com (for Plano Cluster)
```
To register for an account to access AAC Slurm Cluster, please generate SSH key pair and send public SSH key to get your account created. Contact your AMD Sponsor for more details.

# AAC Slurm Partition Naming Convention
The Slurm partitions are named for each Compute Node, number of CPUs, number of GPUs, number of GPU Hives, cluster interconnect, the GPU product, the Operating System distribution of the nodes as follows:

###   &lt;1&gt;CN&lt;n&gt;C&lt;m&gt;G&lt;p&gt;H&lowbar;&lt;q&gt;&lt;IC_type&gt;&lowbar;&lt;GPU_Product&gt;&lowbar;&lt;OS&gt;

where **&lt;1&gt;** is the Compute Node in cluster, **&lt;n&gt;** is total number of CPUs per node, **&lt;m&gt;** is total number of GPUs per node, **&lt;p&gt;** is total number of GPU hives per node, **&lt;q&gt;** is number of interconnect ports and **&lt;IC_type&gt;** is the cluster interconnect type, for example, IB for Infiniband, **&lt;GPU_Product&gt;** is the AMD Instinct Accelerator Product name, and **&lt;OS&gt;** is the Operating System distribution running on the nodes in the cluster.

The following are the currently configured partitions in AAC Plano Slurm cluster:
```
1CN128C8G2H_2IB_MI210_RHEL9*
1CN128C8G2H_2IB_MI210_RHEL8
1CN128C8G2H_2IB_MI210_SLES15
1CN128C8G2H_2IB_MI210_Ubuntu22
1CN96C8G1H_4IB_MI250_Ubuntu22
```
Each user will be given access permissions to specific partition(s)/queue(s).

# How to Display All Slurm Partition/Queue Information
Your account will be set up with access to specific partition(s)/queue(s).
Use `sinfo` to list all the partitions and available compute nodes
```
sinfo --format="%.32P %.5a %.10l %.16F %N"
```
The partition with an asterisk `*` is the default partition. However, a partition/queue name must be specified when submitting jobs using Slurm commands.

# How to Submit a Batch Job
Use the `sbatch` command to queue an `SBATCH` script to be executed on a specific partition, using the `-p` option to specify the partition to use:
```
sbatch -p <specific_parition_name> <path_to_the_sbatch_file>
```
# How to Create an SBATCH File
There are sample `SBATCH` scripts located in https://github.com/amddcgpuce/sbatchfiles/tree/main to submit AMD Infinity Hub applications (https://www.amd.com/en/technologies/infinity-hub) and other sample applications for 1, 2, 4 and 8 GPU workloads on single compute node which can be used as a starting point to write your own `SBATCH` script for your application.
Here's a template for an `SBATCH` file for a 1 GPU workload on AAC Plano Slurm cluster: https://github.com/amddcgpuce/sbatchfiles/blob/main/example1gpu.sbatch

*NOTE*: Please include these lines in the SBATCH file for AAC Plano Slurm cluster which load the correct OS-specific module environment corresponding to the OS running on the Compute Node. At the time of this writing, the ROCm 5.6 environment is the latest available. 
```
source /etc/profile.d/modules.sh
source /shared/share/aac1plano.modules.bash
module purge
module load rocm-5.6.0
```
The line `module load rocm-5.6.0` loads the ROCm 5.6 environment and related libraries built for ROCm 5.6.
## How to Check a Queued Job Status
Use `squeue` command shown below to view submitted job status
```
squeue --format="%.18i %.32P %.8j %.8u %.2t %.10M %.6D %R %n"
```
# How to Find Details of a Submitted or Queued Job
Use `scontrol` to show details of the job ID.
For example, to view details of job ID `21851`, use
```
scontrol show job 21851
```
# How to Allocate and SSH to a Compute Node
Use salloc to allocate a whole node from the assigned partition/queue and SSH to the allocated node.
```
salloc --exclusive --mem=0 --gres=gpu:8 –p <QUEUE_NAME>
```
Where <QUEUE_NAME> is the name of Slurm queue/partition name accessible to you 
### How to create additional SSH sessions to the Allocated Compute Node (previously using `salloc` command)
Additional SSH connections to the salloc allocated node can be started by the user
```
ssh –J –A <USERID>@aac1.amd.com  <COMPUTENODE_HOSTNAME>
```
# How to Set up ROCm Environment on the Compute Node
After `ssh` to the compute node, load the ROCm environment using:
```
module load rocm-5.6.0
```
The ROCm environment module should be loaded from each SSH session.

# How to Display the Accessible Slurm Queues
To show the <QUEUE_NAME> accessible, run sshare command
```
sshare -nm --format="Partition%32" | tr '[:lower:]' '[:upper:]'
```
## How to Enable GCC/GFORTRAN toolset 11 on RHEL8
Use `salloc -p <desired_partition>_RHEL8` to allocate and `ssh` to a Compute Node running RHEL8 OS distribution. To enable gcc-toolset-11, start a new bash shell:
```
$ scl enable gcc-toolset-11 bash
```

## How to Use Podman to run Docker Containers
To start `amddcgpuce/rocm:5.6.0-ub22` docker in interactive mode using `podman` with `$HOME` mounted as `/workdir` inside docker container
```
podman run -it --privileged -v $HOME:/workdir -v /shareddata:/shareddata -v /shared:/shared --workdir /workdir docker://amddcgpuce/rocm:5.6.0-ub22 bash
```
This will pull the docker image, start an interactive session with current work directory set to /workdir and start a bash shell.
Create work files under `/workdir` which is `$HOME` and is accessible from ALL nodes with SSH session.
To exit the docker interactive session, type: `exit <return>` to return to SSH login prompt on allocated node.

*Best practices:* Release cache space used by docker images, run: `podman system prune -a`
Keep work files OUTSIDE container under `$HOME` and use Docker as customized tools environment with packages installed specific for your application development.
Files under `$HOME` are visible on ALL Compute Nodes to resume work with Docker images on ANY allocated node.
#### *NOTE*: Podman is configured to cache Docker images on local storage on the Compute Node. Cached images will be removed periodically to free up disk space

### How to reattach to a podman container after exiting it
From SSH session on Compute Node, 
Use `podman ps –a` to get CONTAINER ID of the Exited container. 
Use `podman start <CONTAINER ID>` to start the container
Use `podman attach <CONTAINER ID>` to attach and get back to `bash` shell prompt.

### How to exit podman container and get back to Compute Node shell prompt
Type ‘exit’ to exit the interactive session with docker to the Compute Node shell prompt

## How to pull a private docker image
To pull private docker images. First login to the account:
```
podman login docker.io
```
Logout when done.
```
podman logout docker.io
```
# How to Set up Conda Environment on AAC Plano Cluster
1. Allocate and SSH to a Compute Node in the assigned partition/queue using `salloc` command.
2. Load Conda Module Environment
```
 module load anaconda3/4.12.0
```
3. Initialize the Conda Environment
NOTE: The dot in the command below to execute the shell script
```
. $CONDA_ROOT/etc/profile.d/conda.sh
```
4. Create a conda environment for Python 3.8
```
conda create --name pytorch2.0_py3.8_demo python=3.8
```
At the prompt, `Proceed ([y]/n)?` enter ‘y’ to continue creation of Conda environment 
5. Activate the conda environment
```
conda activate pytorch2.0_py3.8_demo
```
6. Pip install PyTorch for ROCm wheel
```
pip3 --no-cache-dir install torch==2.0.1 torchvision==0.15.2 -f https://repo.radeon.com/rocm/manylinux/rocm-rel-5.6/
```
# How to Allocate Multi-Node Compute Cluster
#### Allocate 2-node MI210 Cluster Ex: 2-node MI210 RHEL8
```
salloc -N 2 --cpus-per-task=16 --mem=0 --gres=gpu:8 --ntasks-per-node=8 –p <QUEUE_NAME>
Ex: salloc -N 2 --cpus-per-task=16 --mem=0 --gres=gpu:8 --ntasks-per-node=8 –p 1CN128C8G2H_2IB_MI210_RHEL8
```
#### Allocate 4-node MI210 Cluster. Ex: 4-node MI210 RHEL9
```
salloc -N 4 --cpus-per-task=16 --mem=0 --gres=gpu:8 --ntasks-per-node=8 –p <QUEUE_NAME>
Ex: salloc -N 4 --cpus-per-task=16 --mem=0 --gres=gpu:8 --ntasks-per-node=8 –p 1CN128C8G2H_2IB_MI210_RHEL9
```
#### Allocate 2-node MI250 cluster. Ex: 2-node MI250 Ubuntu 22
```
salloc -N 2 --cpus-per-task=12 --mem=0 --gres=gpu:8 --ntasks-per-node=8 –p <QUEUE_NAME>
Ex: salloc -N 2 --cpus-per-task=12 --mem=0 --gres=gpu:8 --ntasks-per-node=8 –p 1CN96C8G1H_4IB_MI250_Ubuntu22
```
#### Allocate 4-node MI250 cluster
```
salloc -N 4 --cpus-per-task=12 --mem=0 --gres=gpu:8 --ntasks-per-node=8 –p <QUEUE_NAME>
Ex: salloc -N 4 --cpus-per-task=12 --mem=0 --gres=gpu:8 --ntasks-per-node=8 –p 1CN96C8G1H_4IB_MI250_Ubuntu22
```
#### Allocate 8-node MI250 cluster
```
salloc -N 8 --cpus-per-task=12 --mem=0 --gres=gpu:8 --ntasks-per-node=8 –p <QUEUE_NAME>
Ex: salloc -N 8 --cpus-per-task=12 --mem=0 --gres=gpu:8 --ntasks-per-node=8 –p 1CN96C8G1H_4IB_MI250_Ubuntu22
```
# FAQ
#### Q What does the `Invalid account or account/partition combination specified` error mean?
It means that user does not have access to nodes behind the `<QUEUE_NAME>` specified.
The errors `salloc: error: Job submit/allocate failed: Invalid account or account/partition combination specified` and `sbatch: error: Batch job submission failed: Invalid account or account/partition combination specified` indicates a `<QUEUE_NAME>` was specified to which the user does not have access permissions
#### Q: What does the `error: invalid partition specified` error message mean?
It means that the `<QUEUE_NAME>` specified does not exist. Run `sinfo –o “%P%` to list valid queues.
#### Q: How do I fix “rocminfo: command not found” or “Command 'rocminfo' not found … Please ask your administrator.”?
Load the ROCm Environment “module load rocm-5.6.0” and retry. If issue persists, send an email to dl.dcgpu.aac.service-requests@amd.com











