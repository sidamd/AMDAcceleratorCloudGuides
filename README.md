# Welcome to AMD Accelerated Cloud (AAC) Reference Documentation

## Getting Started
Contact your AMD Sponsor to sign up for access AMD Accelerated Cloud resources.
### How to Login to Web Interface
Go to https://aac.amd.com
### How to SSH to Slurm Cluster Login Node
1. To SSH to AAC Plano Slurm Cluster, from the laptop or system used to generate SSH keys for AAC User Account Registration, enter the following at the Terminal or PowerShell prompt:
   ```
   ssh <your_userid>@aac1.amd.com
   ```
   The SSH keys should be accessible under `$HOME/.ssh` directory or via `PuTTy` or `Mobaterm` tools used to generate the SSH keys

## Contacting AAC Support Team
For questions or support requests, please email them to dl.dcgpu.aac.service-requests@amd.com

## July 13-14th AAC Maintenance Update Notice for AAC Users

### The AAC Web Interface has moved to https://aac.amd.com 

### How to Fix SSH to `aac1.amd.com` failed with `Host key verification failed` message
Because the Slurm login node has changed from `dell-r08-01` to `pl1vm1pctlnode02` the host key fingerprint has changed. SSH users may see a failure to login with the a *WARNING* message such as one shown below. Please update `$HOME/.ssh/known_hosts` by *removing* the existing entries for `dell-r08-01` and retry to `SSH` to `aac1.amd.com` AAC Plano Slurm cluster login node and accept the new fingerprints:
```
ECDSA key fingerprint is SHA256:u1u0/uh0GLcs19KNHrmZIA6EDLMvJACK5y2fMkVg1fg.
ECDSA key fingerprint is MD5:76:6a:a4:34:56:c0:04:fa:7f:84:e6:85:0b:f1:65:e5.
```

#### Example: First attempt to SSH to `aac1.amd.com` fails due to maintenance update.
```
ssh ssubrama1@aac1.amd.com
```
Failure message:
```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@       WARNING: POSSIBLE DNS SPOOFING DETECTED!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
The ECDSA host key for aac1.amd.com has changed,
and the key for the corresponding IP address 209.249.224.250
is unchanged. This could either mean that
DNS SPOOFING is happening or the IP address for the host
and its host key have changed at the same time.
Offending key for IP in /home/ssubrama1/.ssh/known_hosts:198
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
SHA256:u1u0/uh0GLcs19KNHrmZIA6EDLMvJACK5y2fMkVg1fg.
Please contact your system administrator.
Add correct host key in /home/ssubrama1/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /home/ssubrama1/.ssh/known_hosts:193
ECDSA host key for aac1.amd.com has changed and you have requested strict checking.
Host key verification failed.
```

#### Example: Remove the offending keys from $HOME/.ssh/known_hosts` and retry SSH to aac1.amd.com. Enter "yes" to accept new host key fingerprint at the prompt to continue to login. 

The new login node prompt of AAC Plano Slurm cluster is: `<USERID>@pl1vm1pctlnode02:~$`

```
ssh ssubrama1@aac1.amd.com
```
Enter `yes` to accept the new host key fingerprint to continue login.
```
The authenticity of host 'aac1.amd.com (209.249.224.250)' can't be established.
ECDSA key fingerprint is SHA256:u1u0/uh0GLcs19KNHrmZIA6EDLMvJACK5y2fMkVg1fg.
ECDSA key fingerprint is MD5:76:6a:a4:34:56:c0:04:fa:7f:84:e6:85:0b:f1:65:e5.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'aac1.amd.com' (ECDSA) to the list of known hosts.
Welcome to Ubuntu 22.04.1 LTS (GNU/Linux 5.15.0-76-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Thu Jul 13 12:31:49 PM CDT 2023

  System load:    0.0185546875        Processes:                327
  Usage of /home: 37.6% of 206.58GB   Users logged in:          2
  Memory usage:   0%                  IPv4 address for docker0: 172.17.0.1
  Swap usage:     0%                  IPv4 address for ens160:  10.194.30.21

 * Strictly confined Kubernetes makes edge and IoT secure. Learn how MicroK8s
   just raised the bar for easy, resilient and secure K8s cluster deployment.

   https://ubuntu.com/engage/secure-kubernetes-at-the-edge

ssubrama1@pl1vm1pctlnode02:~$
```


