# Welcome to AMD Accelerated Cloud (AAC) Reference Documentation

## Getting Started
Contact your AMD Sponsor to sign up for access AMD Accelerated Cloud resources.
### How to Login to Web Interface
Go to https://aac.amd.com
### How to SSH to AAC Plano Slurm Cluster
1. From the laptop or system used to generate SSH keys for AAC User Account Registration, enter the following at the Terminal or PowerShell prompt to SSH to the AAC Plano Slurm cluster:
   ```
   ssh <your_userid>@aac1.amd.com
   ```
   The SSH keys should be accessible under `$HOME/.ssh` directory or via `PuTTy` or `Mobaterm` tools used to generate the SSH keys

## Contacting AAC Support Team
For questions or support requests, please email them to dl.dcgpu.aac.service-requests@amd.com

## July 13-14th AAC Maintenance Update Notice for AAC Users

### The AAC Web Interface has moved to https://aac.amd.com 

### How to Fix `ssh <USERID>@aac1.amd.com` failed with `Host key verification failed` message
Because the Slurm login node has changed from `dell-r08-01` to `pl1vm1pctlnode02` the host key fingerprint has changed. SSH users may see a failure to login with the a *WARNING* message such as one shown below. Please update `$HOME/.ssh/known_hosts` by *removing* the existing entries for `dell-r08-01` and retry to `SSH` to `aac1.amd.com` AAC Plano Slurm cluster login node and accept the new fingerprints:
```
ECDSA key fingerprint is SHA256:u1u0/uh0GLcs19KNHrmZIA6EDLMvJACK5y2fMkVg1fg.
ECDSA key fingerprint is MD5:76:6a:a4:34:56:c0:04:fa:7f:84:e6:85:0b:f1:65:e5.
```
#### Solution: 
1. First remove existing fingerprint of old Slurm login host: `ssh-keygen -R aac1.amd.com`
2. Login to the AAC Plano Slurm cluster: `ssh <USERID>@aac1.amd.com`
   Enter "yes" to accept new host key fingerprint at the prompt to continue to login. 

The new login node prompt of AAC Plano Slurm cluster is: `<USERID>@pl1vm1pctlnode02:~$`


