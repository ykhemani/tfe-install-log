# Terraform Enterprise Interactive Installation Log

---

## Configure environment variables

Configure environment variables to optionally facilitate making an ssh connection to the Terraform Enterprise (TFE) virtual machine (VM).

### Command:

```
export TFE_SSH_KEY_FILE=~/.ssh/tfe_pov.pem
export TFE_SSH_USER=tfeadmin
export TFE_VM=10.0.0.5
```

### Log:

```
$ export TFE_SSH_KEY_FILE=~/.ssh/tfe_pov.pem

$ export TFE_SSH_USER=tfeadmin

$ export TFE_VM=10.0.0.5
```

---

## Connect via ssh into VM and install TFE

### Command:

```
ssh -i ${TFE_SSH_KEY_FILE} ${TFE_SSH_USER}@${TFE_VM}
```

### Log:

```
$ ssh -i ${TFE_SSH_KEY_FILE} ${TFE_SSH_USER}@${TFE_VM}
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 5.8.0-1040-azure x86_64)

tfeadmin@yash-tfe-pov-vmss000000:~$
```

---

### Download and run the Terraform Enterprise installation script

### Command:

```
curl -s https://install.terraform.io/ptfe/stable | sudo bash
```

### Notes:

* If prompted, specify the private IP network interface.
* Service IP: leave blank
* proxy? No

### Log:

```
root@yash-tfe-pov-vmss000000:~# curl -s https://install.terraform.io/ptfe/stable | sudo bash
Determining local address
The installer will use network interface 'eth0' (with IP address '10.0.0.5')
Determining service address
The installer was unable to automatically detect the service IP address of this machine.
Please enter the address or leave blank for unspecified.
Service IP address: 
Does this machine require a proxy to access the Internet? (y/N) N
Installing docker version 20.10.7 from https://get.replicated.com/docker-install.sh
# Executing docker install script, commit: 28bc4d09b3938ea30c69407d198ee8ece52c3e12
+ sh -c apt-get update -qq >/dev/null
+ sh -c DEBIAN_FRONTEND=noninteractive apt-get install -y -qq apt-transport-https ca-certificates curl >/dev/null
+ sh -c curl -fsSL "https://download.docker.com/linux/ubuntu/gpg" | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
+ sh -c echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu focal stable" > /etc/apt/sources.list.d/docker.list
+ sh -c apt-get update -qq >/dev/null
INFO: Searching repository for VERSION '20.10.7'
INFO: apt-cache madison 'docker-ce' | grep '20.10.7.*-0~ubuntu' | head -1 | awk '{$1=$1};1' | cut -d' ' -f 3
INFO: apt-cache madison 'docker-ce-cli' | grep '20.10.7.*-0~ubuntu' | head -1 | awk '{$1=$1};1' | cut -d' ' -f 3
+ sh -c DEBIAN_FRONTEND=noninteractive apt-get install -y -qq --no-install-recommends  docker-ce-cli=5:20.10.7~3-0~ubuntu-focal docker-scan-plugin docker-ce=5:20.10.7~3-0~ubuntu-focal >/dev/null
+ version_gte 20.10
+ [ -z 20.10.7 ]
+ eval calver_compare 20.10.7 20.10
+ calver_compare 20.10.7 20.10
+ set +x
+ sh -c DEBIAN_FRONTEND=noninteractive apt-get install -y -qq docker-ce-rootless-extras=5:20.10.7~3-0~ubuntu-focal >/dev/null
+ sh -c docker version
Client: Docker Engine - Community
 Version:           20.10.7
 API version:       1.41
 Go version:        go1.13.15
 Git commit:        f0df350
 Built:             Wed Jun  2 11:56:38 2021
 OS/Arch:           linux/amd64
 Context:           default
 Experimental:      true

Server: Docker Engine - Community
 Engine:
  Version:          20.10.7
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.13.15
  Git commit:       b0f5bc3
  Built:            Wed Jun  2 11:54:50 2021
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.4.9
  GitCommit:        e25210fe30a0a703442421b0f60afac609f950a3
 runc:
  Version:          1.0.1
  GitCommit:        v1.0.1-0-g4144b63
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0

================================================================================

To run Docker as a non-privileged user, consider setting up the
Docker daemon in rootless mode for your user:

    dockerd-rootless-setuptool.sh install

Visit https://docs.docker.com/go/rootless/ to learn about rootless mode.


To run the Docker daemon as a fully privileged service, but granting non-root
users access, refer to https://docs.docker.com/go/daemon-access/

WARNING: Access to the remote API on a privileged Docker daemon is equivalent
         to root access on the host. Refer to the 'Docker daemon attack surface'
         documentation for details: https://docs.docker.com/go/attack-surface/

================================================================================

External script is finished
Synchronizing state of docker.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable docker

Running preflight checks...
[INFO] / disk usage is at 5%
[INFO] /var/lib/docker disk usage is at 5%
[INFO] Docker http proxy not set
[INFO] Docker using default seccomp profile
[INFO] Docker using standard root directory
[INFO] Docker icc (inter-container communication) enabled
[INFO] Docker open files (nofile) ulimit not set
[INFO] Docker userland proxy enabled
[INFO] Firewalld is not active
[INFO] Iptables chain INPUT default policy ACCEPT
Pulling replicated and replicated-ui images
stable-2.53.0: Pulling from replicated/replicated
Image docker.io/replicated/replicated:stable-2.53.0 uses outdated schema1 manifest format. Please upgrade to a schema2 image for better future compatibility. More information at https://docs.docker.com/registry/spec/deprecated-schema-v1/
33847f680f63: Pull complete 
bc7a51a8f001: Pull complete 
42c81fb3067e: Pull complete 
98ed03df376f: Pull complete 
5ee94cb9b8f1: Pull complete 
2d9634cc8029: Pull complete 
0942a00b4793: Pull complete 
ee908dc6dbf7: Pull complete 
4bbcafff2c34: Pull complete 
a070e14fcb20: Pull complete 
9e2d96948a09: Pull complete 
Digest: sha256:912d6bc9b57416bf33b47730ba097a2fdedb34518915d3b582d10add1ce9a51e
Status: Downloaded newer image for replicated/replicated:stable-2.53.0
docker.io/replicated/replicated:stable-2.53.0
stable-2.53.0: Pulling from replicated/replicated-ui
Image docker.io/replicated/replicated-ui:stable-2.53.0 uses outdated schema1 manifest format. Please upgrade to a schema2 image for better future compatibility. More information at https://docs.docker.com/registry/spec/deprecated-schema-v1/
33847f680f63: Already exists 
88e0454bc700: Pull complete 
33477bbb8c8c: Pull complete 
48d9b1f01b20: Pull complete 
aa82716809d1: Pull complete 
5874da70ec0d: Pull complete 
Digest: sha256:d8d0db264d0e972e5a9b6fde270ae2806bba2bec91e3572beb2407358eb1229d
Status: Downloaded newer image for replicated/replicated-ui:stable-2.53.0
docker.io/replicated/replicated-ui:stable-2.53.0
Tagging replicated and replicated-ui images
Stopping replicated and replicated-ui service
Installing replicated and replicated-ui service
Starting replicated and replicated-ui service
Created symlink /etc/systemd/system/docker.service.wants/replicated.service → /etc/systemd/system/replicated.service.
Created symlink /etc/systemd/system/docker.service.wants/replicated-ui.service → /etc/systemd/system/replicated-ui.service.
Installing replicated command alias
Installing local operator
Installing local operator with command:
curl -sSL https://get.replicated.com/operator?replicated_operator_tag=2.53.0
Pulling latest replicated-operator image
stable-2.53.0: Pulling from replicated/replicated-operator
Image docker.io/replicated/replicated-operator:stable-2.53.0 uses outdated schema1 manifest format. Please upgrade to a schema2 image for better future compatibility. More information at https://docs.docker.com/registry/spec/deprecated-schema-v1/
33847f680f63: Already exists 
e8a2ecc09b42: Pull complete 
d918d93fb42a: Pull complete 
1ef9f6951992: Pull complete 
4aefde41dc06: Pull complete 
dfe99bc54bd2: Pull complete 
932531148e85: Pull complete 
Digest: sha256:33b33b28c915cff56ddcb426847ee192eb0f7873fc44b2cd9ffa0b2a684f8e31
Status: Downloaded newer image for replicated/replicated-operator:stable-2.53.0
docker.io/replicated/replicated-operator:stable-2.53.0
Tagging replicated-operator image
Stopping replicated-operator service
Installing replicated-operator service
Starting replicated-operator service
Created symlink /etc/systemd/system/docker.service.wants/replicated-operator.service → /etc/systemd/system/replicated-operator.service.

Operator installation successful

To continue the installation, visit the following URL in your browser:

  http://<this_server_address>:8800

root@yash-tfe-pov-vmss000000:~# 
```

---

### Continue the installation in your web browser

```
https://tfe.seva.cafe:8800
```

---

### Acknowledge certificate warning.

![](screenshots/1.png?raw=true)

---

### Provide SSL Private Key and Certificate

![](screenshots/2.png?raw=true)

---

### Upload your license

![](screenshots/3.png?raw=true)

---

### Choose your installation type

In this example, we are going to do an Online Install.

![](screenshots/4.png?raw=true)

---

### Select Release Channel

If prompted, select the Stable (Default) release channel.

![](screenshots/5.png?raw=true)

Let the installer download the release.

![](screenshots/6.png?raw=true)

---

### Secure the Admin Console

Set a password for accessing the Admin Console.

![](screenshots/7.png?raw=true)

---

### Preflight Checks

The installer will confirm that the machine is ready for Terraform Enterprise.

![](screenshots/8.png?raw=true)

Press Continue.

---

## Configure Terraform Enterprise Settings

### Check the DNS for the hostname.

![](screenshots/9.png?raw=true)

---

### Set the Encryption Password

![](screenshots/10.png?raw=true)

---

### Set the Installation Type to Demo

![](screenshots/11.png?raw=true)

---

### SSL/TLS Configuration

If applicable, add the Private CA Bundle.

![](screenshots/12.png?raw=true)

---

### Capture the Backup API Token

![](screenshots/13.png?raw=true)

Press Save to continue.

---

### Restart Terraform Enterprise

Restart Terraform Enterprise as prompted once the settings are saved.

![](screenshots/14.png?raw=true)

---

Wait for Terraform Enterprise to finish starting.

![](screenshots/15.png?raw=true)

---

Once Terraform Enterprise finishes starting, you'll see that it is marked as started.

![](screenshots/16.png?raw=true)

---

## Create Local Admin User

Click Open to create an Administrative User.

![](screenshots/17.png?raw=true)

Specify Administrative User details.

![](screenshots/18.png?raw=true)

---

## Create a Terraform Enterprise Organization

![](screenshots/19.png?raw=true)

---

## Reference
* [Interative Terraform Enterprise Installation](https://www.terraform.io/docs/enterprise/install/installer.html)
