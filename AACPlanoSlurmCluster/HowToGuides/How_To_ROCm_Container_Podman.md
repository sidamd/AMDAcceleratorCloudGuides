# How to Use ROCm Container on AAC Using Podman
Allocate and SSH to a node from the partition of your choice
```
salloc --exclusive --mem=0 --gres=gpu:8 -p <PARTITION_NAME>
```
# How to Use Podman to run Ubuntu ROCm Docker Container
To start `amddcgpuce/rocm:5.6.1-ub22` docker in interactive mode using `podman` with `$HOME` mounted as `/workdir` inside docker container
```
podman run -it --privileged --network=host --ipc=host -v $HOME:/workdir -v /shareddata:/shareddata -v /shared:/shared --workdir /workdir docker://amddcgpuce/rocm:5.6.1-ub22 bash
```
This will pull the docker image, start an interactive session with current work directory set to /workdir and start a bash shell.

Create work files under `/workdir` which is `$HOME` and is accessible from ALL nodes with SSH session.

To exit the docker interactive session, type: `exit <return>` to return to SSH login prompt on allocated node.
# How to Use Podman to run rocblas-bench using Ubuntu ROCm Docker
To run `rocblas-bench` using the `amddcgpuce/rocm:5.6.1-ub22` docker with 1 GPU
```
podman run --privileged docker://amddcgpuce/rocm:5.6.1-ub22 /opt/rocm/bin/rocblas-bench -f gemm -r d -m 8640 -n 8640 -k 8640 --transposeB T --initialization trig_float -i 2000 --device 0
```
To run `rocblas-bench` using the `amddcgpuce/rocm:5.6.1-ub22` docker with 8 GPU
```
podman run --privileged docker://amddcgpuce/rocm:5.6.1-ub22 /opt/rocm/bin/rocblas-bench -f gemm -r d -m 8640 -n 8640 -k 8640 --transposeB T --initialization trig_float -i 2000 --parallel_devices 8
```
# How to Use Podman to run SLES 15 ROCm Docker Container
To start `amddcgpuce/rocm:5.6.1-sles15` docker in interactive mode using `podman` with `$HOME` mounted as `/workdir` inside docker container
```
podman run -it --privileged --network=host --ipc=host -v $HOME:/workdir -v /shareddata:/shareddata -v /shared:/shared --workdir /workdir docker://amddcgpuce/rocm:5.6.1-sles15 bash
```
