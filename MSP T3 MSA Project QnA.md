# Microservice Project Rarely Asked Question

## Day 1

### VS Code Remote Development

[Developing in WSL](https://code.visualstudio.com/docs/remote/wsl)

>The extension runs commands and other extensions directly in WSL so you can edit files located in WSL or the mounted Windows filesystem (for example /mnt/c) without worrying about pathing issues, binary compatibility, or other cross-OS challenges.

[Remote Development using SSH](https://code.visualstudio.com/docs/remote/ssh)

>The Visual Studio Code Remote - SSH extension allows you to open a remote folder on any remote machine, virtual machine, or container with a running SSH server and take full advantage of VS Code's feature set. Once connected to a server, you can interact with files and folders anywhere on the remote filesystem.

### [VS Code User Interface](https://code.visualstudio.com/docs/getstarted/userinterface)

- Editor
- Primary Side Bar
- Status Bar
- Activity Bar
- Panel

### [VS Code Keyboard shortcuts for Windows](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)

[Key Bindings for VS Code](https://code.visualstudio.com/docs/getstarted/keybindings)

>VS Code lets you perform most tasks directly from the keyboard

General

- `Ctrl+Shift+P`, `F1` Show Command Palette

Display

- `Ctrl+Shift+F` Show Search
- `Ctrl+=`, `Ctrl+-` Zoom in/out
- `Ctrl+J` Toggle Panel Visibility

Integrated terminal

- `` Ctrl+` `` Show integrated terminal

### Shell Command History

[View history of commands run in terminal](https://askubuntu.com/questions/624848/view-history-of-commands-run-in-terminal)

```sh
history
```

### Google Chrome conflict

[Malwarebytes conflict with Google Chrome](https://service.malwarebytes.com/hc/en-us/articles/17569022886803-Malwarebytes-conflict-with-Google-Chrome)

> Microsoft’s KB5027231 update installed on Windows 11 caused a conflict between Google Chrome and exploit protection, resulting in browser crashes

[Windows 11 Google Chrome after KB5027231 update](https://learn.microsoft.com/en-us/answers/questions/1312558/issue-about-not-running-windows-11-google-chrome-a)

- Make Google Chrome your default browser
- Rename the executable Chrome.exe

### Nano Editor

[Overview of nano's shortcuts](https://www.nano-editor.org/dist/latest/cheatsheet.html)

File handling

- `Ctrl+X` (`Y` `Enter`) Close buffer ( Save ), exit from nano

Deletion

- `Alt+Del`	Delete current line

### Amazon Route53

[hosted zones](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zones-working-with.html)

>A hosted zone is ***a container for records***, and records contain information about how you want to ***route traffic for a specific domain***, such as samsungsds.com, and its subdomains (cloud.samsungsds.com). A hosted zone and the corresponding domain have the same name

### [AWS Certificate Manager](https://docs.aws.amazon.com/acm/latest/userguide/acm-overview.html)

>AWS Certificate Manager (ACM) handles the complexity of creating, storing, and renewing public and private SSL/TLS X.509 certificates and keys that protect your AWS websites and applications. ACM wildcard certificates can protect an unlimited number of subdomains

[What Is An SSL/TLS Certificate?](https://aws.amazon.com/what-is/ssl-certificate/)

>An SSL/TLS certificate is a digital object that allows systems to verify the identity & subsequently establish an encrypted network connection to another system using the Secure Sockets Layer/Transport Layer Security (SSL/TLS) protocol

### [Set up the Docker repository](https://docs.docker.com/engine/install/ubuntu/#set-up-the-repository)

```sh
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

The command is used to set up the Docker repository on a Linux system. The repository is a collection of packages that can be installed using the `apt` package manager. The command works by creating a new file called `docker.list` in the `/etc/apt/sources.list.d` directory. This file contains the information that `apt` needs to know in order to find and install Docker packages.

The command is broken down into the following steps:

1. The `echo` command is used to print a string to the console. In this case, the string is a line that defines the Docker repository.
2. The `|` character is called a pipe. It is used to redirect the output of the `echo` command to the `tee` command.
3. The `tee` command is used to write the output of a command to a file and to the console. In this case, the `tee` command will write the Docker repository definition to the `docker.list` file and to the console.
4. The `sudo` command is used to run the command as root. This is necessary because the `tee` command needs to be able to write to the `/etc/apt/sources.list.d` directory.
5. The `/etc/apt/keyrings/docker.gpg` file contains the GPG key that is used to sign the Docker packages. The `signed-by` option tells `apt` to verify the signature of the packages before they are installed.
6. The `arch="$(dpkg --print-architecture)"` option tells `apt` to install the correct version of the Docker packages for the architecture of the system.
7. The `$(. /etc/os-release && echo "$VERSION_CODENAME")` option tells `apt` to install the correct version of the Docker packages for the Ubuntu version that is running on the system.
8. The `stable` option tells `apt` to install the stable version of the Docker packages.
9. The `> /dev/null` option tells `tee` to discard any output that is not written to the `docker.list` file.

Once the `docker.list` file has been created, you can use the `apt update` command to update the `apt` package cache. This will make the Docker packages available for installation. You can then install Docker using the `apt install docker-ce` command.

### [Advanced settings configuration in WSL](https://learn.microsoft.com/en-us/windows/wsl/wsl-config#wslconfig)

#### wsl.conf (per-distribution basis)

`/etc` directory (`/etc/wsl.conf`)

```text
[boot]
systemd=true
```

- ***systemd***: Enable Linux system/service manager

#### .wslconfig (globally across all distributions)

`%UserProfile%` directory (`C:\Users\<UserName>\.wslconfig`)

```text
[wsl2]
swap=8GB
swapfile=D:\\temp\\wsl-swap.vhdx
kernelCommandLine = cgroup_no_v1=all
```

- ***swap***: How much swap space to add to the WSL VM
- ***swapFile***: An absolute Windows path to the swap virtual hard disk
- ***kernelCommandLine***: Additional kernel command line arguments

  [Control groups v1 v2](https://man7.org/linux/man-pages/man7/cgroups.7.html)

### [WSL Releases](https://github.com/microsoft/WSL/releases)

## Day 2

### [Online Boutique](https://github.com/GoogleCloudPlatform/microservices-demo)

>A cloud-first microservices application to demonstrate the use of technologies like Kubernetes, Istio consists of an 11-tier microservices works on any Kubernetes cluster. The application is a web-based e-commerce app where users can browse items, add them to the cart, and purchase them

### WSL Clock Skew

```Bash
aws s3 cp
Fatal error: An error occurred (403) when calling the HeadObject operation: Forbidden
```

[WSL Clock skew issues megathread](https://github.com/microsoft/WSL/issues/10006)

>Sometimes the WSL clock can become skewed, usually ***after hibernate or sleep***

#### Potential work arounds

- Use systemd to force clock sync

```sh
sudo nano /etc/wsl.conf
```

```text
[boot]
systemd=true
```

```sh
sudo apt update && sudo apt install chrony -y
sudo systemctl restart chrony.service
```

- Set the hardware clock via a command

```Bash
sudo hwclock -s
```

- Run ntpdate on distro start up

```sh
sudo apt update && sudo apt install ntpdate -y
```

```sh
sudo nano /etc/wsl.conf
```

```Text
[boot]
command="ntpdate ntp.ubuntu.com"
```

This will force a clock reset on start up of the distro

### [Networking in Compose](https://docs.docker.com/compose/networking/)

>By default Compose sets up a single network for your app

- Each container for a service joins the default network
- both reachable by other containers on that network
- discoverable by them at a hostname identical to the container name

>Your app's network is given a name based on the "project name", which is based on the name of the directory it lives in
>You can override the project name with either the `--project-name` flag or the `COMPOSE_PROJECT_NAME` environment variable

### [Docker Error Bind: Address Already in Use](https://www.baeldung.com/linux/docker-address-already-in-use)

#### 1. In Docker, the issue “address already in use” occurs when we try to expose a container port that’s already acquired on the host machine

#### 2. Killing the Process

[LiSt Open Files](https://github.com/lsof-org/lsof)

```sh
lsof -i:8080
```

```sh
kill xxx
```

[Find Open Ports in Linux](https://www.baeldung.com/linux/find-open-ports)

#### 3. Expose Free Port

### [Understand DNS Propagation](https://world.siteground.com/kb/dns-propagation/)

>DNS propagation refers to the process of updating information on the internet’s DNS (Domain Name System) servers

Factors affecting the Domain propagation period

- Time to Live (TTL) of the DNS record, the record type
- DNS cache
- Network conditions.

[Google Admin Toolbox](https://toolbox.googleapps.com/apps/main/)

[Google Admin Toolbox Dig](https://toolbox.googleapps.com/apps/dig/)

### [Let’s Encrypt Chain of Trust](https://letsencrypt.org/certificates/)

Root Certificates

- ISRG Root X1 (RSA 4096, O = Internet Security Research Group, CN = ISRG Root X1)

Intermediate Certificates

- Let’s Encrypt R3 (RSA 2048, O = Let's Encrypt, CN = R3)

### [Services top-level element](https://docs.docker.com/compose/compose-file/05-services/#services-top-level-element)

A service is an abstract definition of a computing resource within an application which can be scaled or replaced independently from other components

- backed by a set of containers
- run by the platform according to replication requirements and placement constraints
- defined by a Docker image and set of runtime arguments

### Network Tools

#### [network statistics](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html)

```sh
netstat -nltp | grep 8080
```

-n: Display numeric addresses instead of hostnames.
-l: List only listening sockets.
-t: List only TCP sockets.
-p: Display the PID and program name of the process that owns the socket.

#### [socket statistics](https://www.networkworld.com/article/3683910/using-the-ss-command-on-linux-to-view-details-on-sockets.html)

```sh
ss | grep 8080
```

- State: The state of the socket. LISTEN state means that it is listening for incoming connections
- Recv-Q: The number of bytes in the receive queue for the socket
- Send-Q: The number of bytes in the send queue for the socket
- Local Address:Port: The local address and port of the socket
- Peer Address:Port: The address and port of the remote peer for the socket
- User: The user who owns the socket
- Inode: The inode number of the socket
- Pid/Program name: The PID and program name of the process that owns the socket

## Day 3

### My IP

Local public IP query

- [IPIFY ORG](https://api.ipify.org/)
- [Cloud Flare](https://icanhazip.com/)
- [Amazon](https://checkip.amazonaws.com/)
- [quad0](https://ifconfig.me)

```Bash
curl https://api.ipify.org/
```

```Bash
curl https://icanhazip.com/
```

```Bash
curl https://checkip.amazonaws.com/
```

```Bash
curl https://ifconfig.me/
```

### Skaffold trouble shooting

[Architecture and Design](https://skaffold.dev/docs/design/)

Skaffold has a diagnose command that can help you run diagnostics on Skaffold works in your project1. You can also use the debug command to run a pipeline in debug mode1

### DNS

#### DNS Configuration

```yaml
Google DNS:
  8.8.8.8
  8.8.4.4
Cloudflare DNS:
  1.1.1.1
  1.0.0.1
```

WSL Ubuntu

```sh
sudo vi /etc/resolv.conf
```

```text
nameserver 172.20.144.1:
```

```text
nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 1.1.1.1
nameserver 1.0.0.1
```

```text

```

```sh
sudo vi /etc/wsl.conf
```

```text
[network]
generateResolvConf = false
```

Docker Daemon

```sh
sudo vi /etc/docker/daemon.json
```

```Json
{
  "dns": [
    "8.8.8.8",
    "8.8.4.4",
    "1.1.1.1",
    "1.0.0.1",
  ]
}
```

#### DNS Cache flushing

Windows

```powershell
ipconfig /flushdns
```

```powershell
ipconfig /displaydns
```

Linux

```sh
sudo systemd-resolve --flush-caches
```

```sh
sudo systemd-resolve --statistics
```

```sh
resolvectl statistics
```

#### Solve Fail

```sh
ERROR: failed to solve: node:16.18-alpine: failed to do request: Head "https://registry-1.docker.io/v2/library/node/manifests/16.18-alpine": dial tcp: lookup registry-1.docker.io on 192.168.49.1:53: server misbehaving
```

```sh
minikube stop
minikube start
```

```sh
sudo systemctl restart docker
```

### Skaffold config minikube env

```
invalid skaffold config: getting minikube env: running [/usr/local/bin/minikube docker-env --shell none -p minikube --user=skaffold]
```

```sh
stdout: "DOCKER_TLS_VERIFY=1\nDOCKER_HOST=tcp://127.0.0.1:32776\nDOCKER_CERT_PATH=/home/ubuntu/.minikube/certs\nMINIKUBE_ACTIVE_DOCKERD=minikube\nSSH_AUTH_SOCK=\nSSH_AGENT_PID=\n"
stderr: "Host added: /home/ubuntu/.ssh/known_hosts ([127.0.0.1]:32777)\nOpenFile: open /home/ubuntu/.ssh/known_hosts: no such file or directory\n"
cause: exit status 1
```

- Skaffold was unable to get the environment variables for Minikube
- The reason for this is that the `/home/ubuntu/.ssh/known_hosts` file does not exist
- This file is used to store the SSH host keys for known hosts, and it is required by Minikube.

To fix this error, you need to create the /home/ubuntu/.ssh/known_hosts file. You can do this by running the following command:

```sh
ssh-keyscan 127.0.0.1 >> /home/ubuntu/.ssh/known_hosts
```

This command will scan the loopback address (127.0.0.1) for SSH host keys, and it will add them to the /home/ubuntu/.ssh/known_hosts file. Once you have created this file, you should be able to run skaffold dev --port-forward without any errors.

[Skaffold documentation on port forwarding](https://skaffold.dev/docs/port-forwarding/)
[Minikube documentation on the docker-env command](https://minikube.sigs.k8s.io/docs/commands/docker-env/)
[SSH documentation on the ssh-keyscan command](https://linux.die.net/man/1/ssh-keyscan)

### Kubernetes Monitoring, Logging, and Debugging

[Troubleshooting Applications](https://kubernetes.io/docs/tasks/debug/debug-application/)

[Troubleshooting Clusters](https://kubernetes.io/docs/tasks/debug/debug-cluster/)

### YAML List

[YAML indentation for Lists](https://stackoverflow.com/questions/17014460/yaml-indentation-for-array-in-hash)

## Day 4

### npm package install error

```Bash
npm install express dotenv mongoose --save
```

```Bash
npm notice Beginning October 4, 2021, all connections to the npm registry - including for package installation - must use TLS 1.2 or higher. You are currently using plaintext http to connect. Please visit the GitHub blog for more information: https://github.blog/2021-08-23-npm-registry-deprecating-tls-1-0-tls-1-1/
npm notice Beginning October 4, 2021, all connections to the npm registry - including for package installation - must use TLS 1.2 or higher. You are currently using plaintext http to connect. Please visit the GitHub blog for more information: https://github.blog/2021-08-23-npm-registry-deprecating-tls-1-0-tls-1-1/
npm ERR! Cannot read properties of null (reading 'pickAlgorithm')
npm ERR! A complete log of this run can be found in:
npm ERR!     /home/ubuntu/.npm/_logs/2023-05-18T01_13_43_994Z-debug-0.log
```

```Bash
npm set registry=https://registry.npmjs.org/
```

The npm cache is a directory on your computer where npm stores copies of the packages that you have installed. When you install a new package, npm will download the package from the npm registry and store it in the cache. The next time you try to install the same package, npm will not download the package again, but will instead use the copy that is stored in the cache.

If the npm cache becomes corrupted, it can cause problems when you try to install new packages. For example, you might get an error message like "TypeError: Cannot read properties of null (reading 'pickAlgorithm')". Clearing the npm cache will delete all of the packages that are stored in the cache and force npm to download the packages again from the npm registry. This can often fix problems with installing new packages.

To clear the npm cache, you can run the following command:

```Bash
npm cache clear --force
```

### Deleting the ingress-nginx-admission webhook configuration

```Bash
kubectl delete -A ValidatingWebhookConfiguration ingress-nginx-admission
```

A validating webhook configuration is a Kubernetes object that defines a set of rules that must be met before a resource can be created or updated. In the case of the ingress-nginx-admission webhook configuration, it ensures that any ingress resources that are created or updated conform to the rules defined by the Ingress Nginx controller.

Deleting the ingress-nginx-admission webhook configuration will allow you to create or update ingress resources without having to comply with the rules defined by the Ingress Nginx controller. This may be useful if you want to create or update ingress resources that do not conform to the rules defined by the Ingress Nginx controller.

However, it is important to note that deleting the ingress-nginx-admission webhook configuration may make your ingress resources more vulnerable to attacks. This is because the Ingress Nginx controller provides a number of security features that are designed to protect your ingress resources from attacks. By deleting the ingress-nginx-admission webhook configuration, you will be disabling these security features.

Therefore, it is important to weigh the risks and benefits before deleting the ingress-nginx-admission webhook configuration. If you are unsure whether or not you should delete the webhook configuration, you should consult with a security expert.

### Docker Image

Docker Container

Stop and remove all running containers:

```sh
docker stop $(docker ps -aq)
docker rm $(docker ps -aq)
```

Removes all containers:

```sh
docker container rm $(docker container ls -a -q)
```

Forcefully remove all Docker images:

```sh
docker rmi --force $(docker images -a -q)
```

### Prune Docker Objects

[Prune unused Docker objects](https://docs.docker.com/config/pruning/)

[Show untagged images (dangling)](https://docs.docker.com/engine/reference/commandline/images/#show-untagged-images-dangling)

### Docker Cache

[Docker Cache – How to Do a Clean Image Rebuild and Clear Docker's Cache](https://www.freecodecamp.org/news/docker-cache-tutorial/)

[Optimizing builds with cache management](https://docs.docker.com/build/cache/)

[How to get docker-compose to use the latest image from repository](https://stackoverflow.com/questions/37685581/how-to-get-docker-compose-to-use-the-latest-image-from-repository)

## Day 5

### Nginx Reverse Proxy configuration

The nginx.conf file is a configuration file for the Nginx web server. It tells Nginx how to listen for requests, how to handle those requests, and where to send the responses.

The first few lines of the file set up the basic configuration for Nginx. The user directive sets the user that Nginx will run as, the worker_processes directive sets the number of worker processes that Nginx will use, the error_log directive sets the path to the error log file, and the pid directive sets the path to the process ID file.

The next section of the file defines the events that Nginx will listen for. The worker_connections directive sets the maximum number of simultaneous connections that Nginx will accept.

The next section of the file defines the HTTP configuration for Nginx. The include directive includes the /etc/nginx/mime.types file, which defines the MIME types for different file extensions. The default_type directive sets the default MIME type for files that do not have an extension.

The upstream directives define the upstream servers that Nginx will proxy requests to. The eshopfrontend upstream server defines the frontend server, which is responsible for serving static files. The eshopbackend upstream server defines the backend server, which is responsible for serving dynamic content. The other upstream servers define the other services that the e-commerce website uses.

The server directive defines the main server block. The listen directive sets the port that Nginx will listen on, the server_name directive sets the hostname that Nginx will respond to, and the location directives define the paths that Nginx will handle.

The proxy_pass directive tells Nginx to proxy requests to the upstream server for the specified path. The proxy_redirect directive tells Nginx not to redirect requests to the upstream server. The proxy_set_header directive tells Nginx to set the specified headers on the request to the upstream server.

The sendfile directive tells Nginx to use the sendfile() system call to send files to the client. The keepalive_timeout directive sets the amount of time that Nginx will keep a connection open after the client has finished sending requests. The include directive includes the /etc/nginx/conf.d/*.conf files, which can be used to further configure Nginx.

Here is a brief explanation of each directive in the nginx.conf file:

user: Sets the user that Nginx will run as.
worker_processes: Sets the number of worker processes that Nginx will use.
error_log: Sets the path to the error log file.
pid: Sets the path to the process ID file.
worker_connections: Sets the maximum number of simultaneous connections that Nginx will accept.
include: Includes another configuration file.
default_type: Sets the default MIME type for files that do not have an extension.
upstream: Defines an upstream server.
server: Defines a server block.
listen: Sets the port that Nginx will listen on.
server_name: Sets the hostname that Nginx will respond to.
location: Defines a path that Nginx will handle.
proxy_pass: Tells Nginx to proxy requests to the upstream server for the specified path.
proxy_redirect: Tells Nginx not to redirect requests to the upstream server.
proxy_set_header: Tells Nginx to set the specified headers on the request to the upstream server.
sendfile: Tells Nginx to use the sendfile() system call to send files to the client.
keepalive_timeout: Sets the amount of time that Nginx will keep a connection open after the client has finished sending requests.
include: Includes another configuration file.

## Day 6

### [Kaniko - Build Images In Kubernetes](https://github.com/GoogleContainerTools/kaniko)

### Github Jenkins webhooks

`The HyperText Transfer Protocol (HTTP) 302 Found redirect status response code`

- indicates that the resource requested has been temporarily moved to the URL given by the Location header
- A browser redirects to this page but search engines don't update their links to the resource
- Without Trailing Slash webhooks can get redirect error

[Triggering builds with webhooks behind a secure firewall](https://www.jenkins.io/blog/2019/01/07/webhook-firewalls/)

[Github Webhook With Jenkins return 302 Found](https://stackoverflow.com/questions/49848884/github-webhook-with-jenkins-return-302-found)

### AWS EKS Nodes

```sh
kubectl describe nodes
```

```sh
ubuntu@ip-10-0-10-32:~$ kubectl describe nodes
Name:               ip-10-0-10-242.ec2.internal
Roles:              <none>
Labels:             beta.kubernetes.io/arch=amd64
                    beta.kubernetes.io/instance-type=t3.medium
                    beta.kubernetes.io/os=linux
                    eks.amazonaws.com/capacityType=ON_DEMAND
                    eks.amazonaws.com/nodegroup=eshop-mgmt-eks-node
                    eks.amazonaws.com/nodegroup-image=ami-02f5ecb082b74cd86
                    failure-domain.beta.kubernetes.io/region=us-east-1
                    failure-domain.beta.kubernetes.io/zone=us-east-1a
                    k8s.io/cloud-provider-aws=c00b8417cd66d053d0fc57caa7fb9d3e
                    kubernetes.io/arch=amd64
                    kubernetes.io/hostname=ip-10-0-10-242.ec2.internal
                    kubernetes.io/os=linux
                    node.kubernetes.io/instance-type=t3.medium
                    topology.ebs.csi.aws.com/zone=us-east-1a
                    topology.kubernetes.io/region=us-east-1
                    topology.kubernetes.io/zone=us-east-1a
Annotations:        alpha.kubernetes.io/provided-node-ip: 10.0.10.242
                    csi.volume.kubernetes.io/nodeid: {"ebs.csi.aws.com":"i-018db00f31a8bc4a7"}
                    node.alpha.kubernetes.io/ttl: 0
                    volumes.kubernetes.io/controller-managed-attach-detach: true
CreationTimestamp:  Wed, 16 Aug 2023 01:40:17 +0000
Taints:             <none>
Unschedulable:      false
Lease:
  HolderIdentity:  ip-10-0-10-242.ec2.internal
  AcquireTime:     <unset>
  RenewTime:       Wed, 16 Aug 2023 06:12:09 +0000
Conditions:
  Type             Status  LastHeartbeatTime                 LastTransitionTime                Reason                       Message
  ----             ------  -----------------                 ------------------                ------                       -------
  MemoryPressure   False   Wed, 16 Aug 2023 06:07:54 +0000   Wed, 16 Aug 2023 01:40:16 +0000   KubeletHasSufficientMemory   kubelet has sufficient memory available
  DiskPressure     False   Wed, 16 Aug 2023 06:07:54 +0000   Wed, 16 Aug 2023 01:40:16 +0000   KubeletHasNoDiskPressure     kubelet has no disk pressure
  PIDPressure      False   Wed, 16 Aug 2023 06:07:54 +0000   Wed, 16 Aug 2023 01:40:16 +0000   KubeletHasSufficientPID      kubelet has sufficient PID available
  Ready            True    Wed, 16 Aug 2023 06:07:54 +0000   Wed, 16 Aug 2023 01:40:37 +0000   KubeletReady                 kubelet is posting ready status
Addresses:
  InternalIP:   10.0.10.242
  Hostname:     ip-10-0-10-242.ec2.internal
  InternalDNS:  ip-10-0-10-242.ec2.internal
Capacity:
  attachable-volumes-aws-ebs:  25
  cpu:                         2
  ephemeral-storage:           20959212Ki
  hugepages-1Gi:               0
  hugepages-2Mi:               0
  memory:                      3943376Ki
  pods:                        17
Allocatable:
  attachable-volumes-aws-ebs:  25
  cpu:                         1930m
  ephemeral-storage:           18242267924
  hugepages-1Gi:               0
  hugepages-2Mi:               0
  memory:                      3388368Ki
  pods:                        17
System Info:
  Machine ID:                 ec26f70a1a1c41d10e494fd44f7d32a2
  System UUID:                ec26f70a-1a1c-41d1-0e49-4fd44f7d32a2
  Boot ID:                    5dad7f0e-164e-4957-8393-e6fb3b835096
  Kernel Version:             5.10.173-154.642.amzn2.x86_64
  OS Image:                   Amazon Linux 2
  Operating System:           linux
  Architecture:               amd64
  Container Runtime Version:  containerd://1.6.19
  Kubelet Version:            v1.24.11-eks-a59e1f0
  Kube-Proxy Version:         v1.24.11-eks-a59e1f0
ProviderID:                   aws:///us-east-1a/i-018db00f31a8bc4a7
Non-terminated Pods:          (12 in total)
  Namespace                   Name                                                 CPU Requests  CPU Limits  Memory Requests  Memory Limits  Age
  ---------                   ----                                                 ------------  ----------  ---------------  -------------  ---
  argocd                      argocd-application-controller-0                      0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  argocd                      argocd-applicationset-controller-6958f7b744-tvtp2    0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  argocd                      argocd-notifications-controller-5f85647f6c-x768k     0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  jenkins                     jenkins-0                                            50m (2%)      2 (103%)    256Mi (7%)       4Gi (123%)     39d
  kube-system                 aws-node-xjzhc                                       25m (1%)      0 (0%)      0 (0%)           0 (0%)         4h32m
  kube-system                 ebs-csi-node-czfzr                                   30m (1%)      300m (15%)  120Mi (3%)       768Mi (23%)    4h32m
  kube-system                 kube-proxy-x5nq2                                     100m (5%)     0 (0%)      0 (0%)           0 (0%)         4h32m
  meshery                     meshery-consul-8484fbcc96-8rdr5                      0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  meshery                     meshery-kuma-785765997-n9sb4                         0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  meshery                     meshery-linkerd-cc65f9d78-k5wpm                      0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  meshery                     meshery-meshsync-6f969458f6-8vtk8                    0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  meshery                     meshery-osm-6fbc9769cd-pmvpv                         0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource                    Requests     Limits
  --------                    --------     ------
  cpu                         205m (10%)   2300m (119%)
  memory                      376Mi (11%)  4864Mi (146%)
  ephemeral-storage           0 (0%)       0 (0%)
  hugepages-1Gi               0 (0%)       0 (0%)
  hugepages-2Mi               0 (0%)       0 (0%)
  attachable-volumes-aws-ebs  0            0
Events:                       <none>


Name:               ip-10-0-11-193.ec2.internal
Roles:              <none>
Labels:             beta.kubernetes.io/arch=amd64
                    beta.kubernetes.io/instance-type=t3.medium
                    beta.kubernetes.io/os=linux
                    eks.amazonaws.com/capacityType=ON_DEMAND
                    eks.amazonaws.com/nodegroup=eshop-mgmt-eks-node
                    eks.amazonaws.com/nodegroup-image=ami-02f5ecb082b74cd86
                    failure-domain.beta.kubernetes.io/region=us-east-1
                    failure-domain.beta.kubernetes.io/zone=us-east-1b
                    k8s.io/cloud-provider-aws=c00b8417cd66d053d0fc57caa7fb9d3e
                    kubernetes.io/arch=amd64
                    kubernetes.io/hostname=ip-10-0-11-193.ec2.internal
                    kubernetes.io/os=linux
                    node.kubernetes.io/instance-type=t3.medium
                    topology.ebs.csi.aws.com/zone=us-east-1b
                    topology.kubernetes.io/region=us-east-1
                    topology.kubernetes.io/zone=us-east-1b
Annotations:        alpha.kubernetes.io/provided-node-ip: 10.0.11.193
                    csi.volume.kubernetes.io/nodeid: {"ebs.csi.aws.com":"i-077b8f0ef8bad3b7d"}
                    node.alpha.kubernetes.io/ttl: 0
                    volumes.kubernetes.io/controller-managed-attach-detach: true
CreationTimestamp:  Wed, 16 Aug 2023 01:40:16 +0000
Taints:             <none>
Unschedulable:      false
Lease:
  HolderIdentity:  ip-10-0-11-193.ec2.internal
  AcquireTime:     <unset>
  RenewTime:       Wed, 16 Aug 2023 06:12:11 +0000
Conditions:
  Type             Status  LastHeartbeatTime                 LastTransitionTime                Reason                       Message
  ----             ------  -----------------                 ------------------                ------                       -------
  MemoryPressure   False   Wed, 16 Aug 2023 06:07:24 +0000   Wed, 16 Aug 2023 01:40:15 +0000   KubeletHasSufficientMemory   kubelet has sufficient memory available
  DiskPressure     False   Wed, 16 Aug 2023 06:07:24 +0000   Wed, 16 Aug 2023 01:40:15 +0000   KubeletHasNoDiskPressure     kubelet has no disk pressure
  PIDPressure      False   Wed, 16 Aug 2023 06:07:24 +0000   Wed, 16 Aug 2023 01:40:15 +0000   KubeletHasSufficientPID      kubelet has sufficient PID available
  Ready            True    Wed, 16 Aug 2023 06:07:24 +0000   Wed, 16 Aug 2023 01:40:36 +0000   KubeletReady                 kubelet is posting ready status
Addresses:
  InternalIP:   10.0.11.193
  Hostname:     ip-10-0-11-193.ec2.internal
  InternalDNS:  ip-10-0-11-193.ec2.internal
Capacity:
  attachable-volumes-aws-ebs:  25
  cpu:                         2
  ephemeral-storage:           20959212Ki
  hugepages-1Gi:               0
  hugepages-2Mi:               0
  memory:                      3943376Ki
  pods:                        17
Allocatable:
  attachable-volumes-aws-ebs:  25
  cpu:                         1930m
  ephemeral-storage:           18242267924
  hugepages-1Gi:               0
  hugepages-2Mi:               0
  memory:                      3388368Ki
  pods:                        17
System Info:
  Machine ID:                 ec2b6daf532a7a13433124fe6d7f84ab
  System UUID:                ec2b6daf-532a-7a13-4331-24fe6d7f84ab
  Boot ID:                    c50838d5-96be-4025-a7bc-8b3baa908bfb
  Kernel Version:             5.10.173-154.642.amzn2.x86_64
  OS Image:                   Amazon Linux 2
  Operating System:           linux
  Architecture:               amd64
  Container Runtime Version:  containerd://1.6.19
  Kubelet Version:            v1.24.11-eks-a59e1f0
  Kube-Proxy Version:         v1.24.11-eks-a59e1f0
ProviderID:                   aws:///us-east-1b/i-077b8f0ef8bad3b7d
Non-terminated Pods:          (17 in total)
  Namespace                   Name                                     CPU Requests  CPU Limits  Memory Requests  Memory Limits  Age
  ---------                   ----                                     ------------  ----------  ---------------  -------------  ---
  argocd                      argocd-dex-server-5b4dd7696f-2fq2r       0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  argocd                      argocd-repo-server-5fbdd6655b-ch7rm      0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  istio-system                istio-ingressgateway-5d55688987-qtj9n    100m (5%)     2 (103%)    128Mi (3%)       1Gi (30%)      39d
  kube-system                 aws-node-fqv7h                           25m (1%)      0 (0%)      0 (0%)           0 (0%)         4h32m
  kube-system                 coredns-79989457d9-hgpnz                 100m (5%)     0 (0%)      70Mi (2%)        170Mi (5%)     39d
  kube-system                 coredns-79989457d9-lmm6r                 100m (5%)     0 (0%)      70Mi (2%)        170Mi (5%)     39d
  kube-system                 ebs-csi-controller-6c4844c8c9-47bwx      60m (3%)      600m (31%)  240Mi (7%)       1536Mi (46%)   39d
  kube-system                 ebs-csi-controller-6c4844c8c9-ptdrr      60m (3%)      600m (31%)  240Mi (7%)       1536Mi (46%)   39d
  kube-system                 ebs-csi-node-2chkk                       30m (1%)      300m (15%)  120Mi (3%)       768Mi (23%)    4h32m
  kube-system                 kube-proxy-qcpn4                         100m (5%)     0 (0%)      0 (0%)           0 (0%)         4h32m
  meshery                     meshery-app-mesh-67c78f557d-dwt2p        0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  meshery                     meshery-broker-0                         0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  meshery                     meshery-cilium-7757c94c4d-sj4c2          0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  meshery                     meshery-db8dc964-gsk72                   0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  meshery                     meshery-istio-65f67fb978-ndv6r           0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  meshery                     meshery-nsm-7788546ff6-77d2z             0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  meshery                     meshery-operator-545f56d5b-xb9xw         0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource                    Requests     Limits
  --------                    --------     ------
  cpu                         575m (29%)   3500m (181%)
  memory                      868Mi (26%)  5204Mi (157%)
  ephemeral-storage           0 (0%)       0 (0%)
  hugepages-1Gi               0 (0%)       0 (0%)
  hugepages-2Mi               0 (0%)       0 (0%)
  attachable-volumes-aws-ebs  0            0
Events:                       <none>


Name:               ip-10-0-11-9.ec2.internal
Roles:              <none>
Labels:             beta.kubernetes.io/arch=amd64
                    beta.kubernetes.io/instance-type=t3.medium
                    beta.kubernetes.io/os=linux
                    eks.amazonaws.com/capacityType=ON_DEMAND
                    eks.amazonaws.com/nodegroup=eshop-mgmt-eks-node
                    eks.amazonaws.com/nodegroup-image=ami-02f5ecb082b74cd86
                    failure-domain.beta.kubernetes.io/region=us-east-1
                    failure-domain.beta.kubernetes.io/zone=us-east-1b
                    k8s.io/cloud-provider-aws=c00b8417cd66d053d0fc57caa7fb9d3e
                    kubernetes.io/arch=amd64
                    kubernetes.io/hostname=ip-10-0-11-9.ec2.internal
                    kubernetes.io/os=linux
                    node.kubernetes.io/instance-type=t3.medium
                    topology.ebs.csi.aws.com/zone=us-east-1b
                    topology.kubernetes.io/region=us-east-1
                    topology.kubernetes.io/zone=us-east-1b
Annotations:        alpha.kubernetes.io/provided-node-ip: 10.0.11.9
                    csi.volume.kubernetes.io/nodeid: {"ebs.csi.aws.com":"i-0ab37466b41a732f1"}
                    node.alpha.kubernetes.io/ttl: 0
                    volumes.kubernetes.io/controller-managed-attach-detach: true
CreationTimestamp:  Wed, 16 Aug 2023 01:40:22 +0000
Taints:             <none>
Unschedulable:      false
Lease:
  HolderIdentity:  ip-10-0-11-9.ec2.internal
  AcquireTime:     <unset>
  RenewTime:       Wed, 16 Aug 2023 06:12:12 +0000
Conditions:
  Type             Status  LastHeartbeatTime                 LastTransitionTime                Reason                       Message
  ----             ------  -----------------                 ------------------                ------                       -------
  MemoryPressure   False   Wed, 16 Aug 2023 06:12:13 +0000   Wed, 16 Aug 2023 01:40:20 +0000   KubeletHasSufficientMemory   kubelet has sufficient memory available
  DiskPressure     False   Wed, 16 Aug 2023 06:12:13 +0000   Wed, 16 Aug 2023 01:40:20 +0000   KubeletHasNoDiskPressure     kubelet has no disk pressure
  PIDPressure      False   Wed, 16 Aug 2023 06:12:13 +0000   Wed, 16 Aug 2023 01:40:20 +0000   KubeletHasSufficientPID      kubelet has sufficient PID available
  Ready            True    Wed, 16 Aug 2023 06:12:13 +0000   Wed, 16 Aug 2023 01:40:44 +0000   KubeletReady                 kubelet is posting ready status
Addresses:
  InternalIP:   10.0.11.9
  Hostname:     ip-10-0-11-9.ec2.internal
  InternalDNS:  ip-10-0-11-9.ec2.internal
Capacity:
  attachable-volumes-aws-ebs:  25
  cpu:                         2
  ephemeral-storage:           20959212Ki
  hugepages-1Gi:               0
  hugepages-2Mi:               0
  memory:                      3943376Ki
  pods:                        17
Allocatable:
  attachable-volumes-aws-ebs:  25
  cpu:                         1930m
  ephemeral-storage:           18242267924
  hugepages-1Gi:               0
  hugepages-2Mi:               0
  memory:                      3388368Ki
  pods:                        17
System Info:
  Machine ID:                 ec293b61b02d05be09458c058fdd8aa7
  System UUID:                ec293b61-b02d-05be-0945-8c058fdd8aa7
  Boot ID:                    411260b8-a836-4336-b980-a8e01c187c59
  Kernel Version:             5.10.173-154.642.amzn2.x86_64
  OS Image:                   Amazon Linux 2
  Operating System:           linux
  Architecture:               amd64
  Container Runtime Version:  containerd://1.6.19
  Kubelet Version:            v1.24.11-eks-a59e1f0
  Kube-Proxy Version:         v1.24.11-eks-a59e1f0
ProviderID:                   aws:///us-east-1b/i-0ab37466b41a732f1
Non-terminated Pods:          (8 in total)
  Namespace                   Name                                    CPU Requests  CPU Limits  Memory Requests  Memory Limits  Age
  ---------                   ----                                    ------------  ----------  ---------------  -------------  ---
  argocd                      argocd-redis-69d5786dcd-t49qn           0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  argocd                      argocd-server-d489bcdff-2fljr           0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  istio-system                istiod-7b47bb8679-q9nq9                 500m (25%)    0 (0%)      2Gi (61%)        0 (0%)         39d
  kube-system                 aws-node-jvl7v                          25m (1%)      0 (0%)      0 (0%)           0 (0%)         4h31m
  kube-system                 ebs-csi-node-h4gz9                      30m (1%)      300m (15%)  120Mi (3%)       768Mi (23%)    4h31m
  kube-system                 kube-proxy-bnjvw                        100m (5%)     0 (0%)      0 (0%)           0 (0%)         4h31m
  meshery                     meshery-nginx-sm-5c5569dbf4-nkdvj       0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
  meshery                     meshery-traefik-mesh-c5548d4f6-nbk7p    0 (0%)        0 (0%)      0 (0%)           0 (0%)         39d
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource                    Requests      Limits
  --------                    --------      ------
  cpu                         655m (33%)    300m (15%)
  memory                      2168Mi (65%)  768Mi (23%)
  ephemeral-storage           0 (0%)        0 (0%)
  hugepages-1Gi               0 (0%)        0 (0%)
  hugepages-2Mi               0 (0%)        0 (0%)
  attachable-volumes-aws-ebs  0             0
Events:                       <none>
```

### [Using Git source control in VS Code](https://code.visualstudio.com/docs/sourcecontrol/overview)

## Day 7

### Helm Chart

[Helm Charts - What is and why to use them](https://www.youtube.com/watch?v=tQkxAYgXuPY)

[What is Helm in Kubernetes? Helm and Helm Charts explained | Kubernetes Tutorial 23](https://www.bing.com/videos/search?q=best+video+explain+why+use+helm+chart+youtube&view=detail&mid=6CF58EA85C9A8C7E261B6CF58EA85C9A8C7E261B&FORM=VIRE)

## Day 8

### Cloudtrail

[What Is AWS CloudTrail?](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)

WS CloudTrail is an AWS service that helps you enable operational and risk auditing, governance, and compliance of your AWS account. Actions taken by a user, role, or an AWS service are recorded as events in CloudTrail. Events include actions taken in the AWS Management Console, AWS Command Line Interface, and AWS SDKs and APIs.

```sh
aws cloudtrail lookup-events --lookup-attributes AttributeKey=EventName,AttributeValue=CreateLoadBalancer --region=us-west-2 | grep <<Coud Loadbalancer DNS Name >>
```

```sh
aws cloudtrail lookup-events --lookup-attributes AttributeKey=EventName,AttributeValue=CreateLoadBalancer --region=us-west-2 | grep ae663f3f8eff243a69e06266cb319154-1234567890.us-west-2.elb.amazonaws.com
```

```json
{
  "CloudTrailEvent": {
    "eventVersion": "1.08",
    "userIdentity": {
      "type": "AssumedRole",
      "principalId": "AROAXAY7VTE7BDHPKQYQB:1692148309803252560",
      "arn": "arn:aws:sts::----------:assumed-role/eshop-service-eks-cluster-role/1692148309803252560",
      "accountId": "------------",
      "accessKeyId": "ASIAXAY7VTE7PZPVICON",
      "sessionContext": {
        "sessionIssuer": {
          "type": "Role",
          "principalId": "AROAXAY7VTE7BDHPKQYQB",
          "arn": "arn:aws:iam::-----------:role/eshop-service-eks-cluster-role",
          "accountId": "-------------",
          "userName": "eshop-service-eks-cluster-role"
        },
        "webIdFederationData": {},
        "attributes": {
          "creationDate": "2023-08-17T02:24:04Z",
          "mfaAuthenticated": "false"
        }
      },
      "invokedBy": "eks.amazonaws.com"
    },
    "eventTime": "2023-08-17T02:24:05Z",
    "eventSource": "elasticloadbalancing.amazonaws.com",
    "eventName": "CreateLoadBalancer",
    "awsRegion": "us-west-2",
    "sourceIPAddress": "eks.amazonaws.com",
    "userAgent": "eks.amazonaws.com",
    "requestParameters": {
      "subnets": [
        "subnet-014562146fbd5d9f8",
        "subnet-0aa7b262baef75b27"
      ],
      "securityGroups": [
        "sg-0d5df846480d7e2cb"
      ],
      "loadBalancerName": "ae663f3f8eff243a69e06266cb319154",
      "tags": [
        {
          "key": "kubernetes.io/service-name",
          "value": "eshop/eshop-prometheus-server"
        },
        {
          "key": "kubernetes.io/cluster/eshop-service-eks-cluster",
          "value": "owned"
        }
      ],
      "listeners": [
        {
          "protocol": "tcp",
          "loadBalancerPort": 80,
          "instanceProtocol": "tcp",
          "instancePort": 32030
        }
      ]
    },
    "responseElements": {
      "dNSName": "ae663f3f8eff243a69e06266cb319154-1234567890.us-west-2.elb.amazonaws.com"
    },
    "requestID": "0daee6a7-a349-4228-9ac7-8d9c598a2dce",
    "eventID": "09c28c01-f12f-4a6a-9551-7f30270dffc8",
    "readOnly": false,
    "eventType": "AwsApiCall",
    "apiVersion": "2012-06-01",
    "managementEvent": true,
    "recipientAccountId": "----------------",
    "eventCategory": "Management"
  }
}
```

```sh
aws cloudtrail lookup-events --lookup-attributes AttributeKey=EventName,AttributeValue=CreateLoadBalancer --region=us-west-2 --output json | jq '.Events[].CloudTrailEvent' | jq fromjson
```

```sh
aws cloudtrail --region us-east-1  lookup-events --lookup-attributes AttributeKey=EventName,AttributeValue=ConsoleLogin --query Events[].EventTime --output yaml
```

```sh
aws cloudtrail lookup-events --query 'Events[].EventName' --output yaml --max-items 999 | sort | uniq
```

### Service Cluster Lookup Fail

```sh
Unable to create application: error while validating and normalizing app: error validating the repo: Get "https://08B4564CDA95B0E162C6E40AE4465A16.gr7.us-west-2.eks.amazonaws.com/version?timeout=32s": dial tcp: lookup 08B4564CDA95B0E162C6E40AE4465A16.gr7.us-west-2.eks.amazonaws.com on 172.20.0.10:53: no such host
```

The error message indicates that you cannot connect to the Kubernetes service cluster. Please check the following:

- Make sure that the service cluster is healthy in the AWS console.
- Make sure that the cluster settings in ArgoCD match the current service cluster.
- Make sure that the repository settings are properly connected.
- Make sure that you can connect to the service cluster from the admin server.

1. Verify DNS resolution: Check the DNS configuration of the machine or cluster where Argo CD is running. Ensure that the DNS settings are correctly configured, and the machine can resolve hostnames to IP addresses. You can test DNS resolution using the nslookup or dig command. For example:

```sh
nslookup 08B4564CDA95B0E162C6E40AE4465A16.gr7.us-west-2.eks.amazonaws.com
```

If DNS resolution fails, you may need to investigate your DNS configuration or check if there are any network connectivity issues.

2. Check repository URL: Double-check the repository URL provided in the Argo CD application configuration. Ensure that the URL is correct and accessible. Make sure there are no typos or errors in the URL.

3. Verify network connectivity: Ensure that the machine or cluster where Argo CD is running has proper network connectivity to reach the repository URL. Check if there are any network restrictions, firewalls, or security groups that may be blocking the connection.

4. Check access credentials: If the repository requires authentication, verify that the credentials provided in the Argo CD application configuration are correct and have sufficient privileges to access the repository.

5. Test repository access manually: Try accessing the repository URL manually from the machine or cluster where Argo CD is running. This can help identify if there are any issues with accessing the repository from the environment. You can use tools like curl or wget to test the connectivity.

```sh
curl -I https://08B4564CDA95B0E162C6E40AE4465A16.gr7.us-west-2.eks.amazonaws.com/version
```

If the manual test fails, it suggests a problem with the repository's availability or accessibility, and you may need to investigate further.

By following these steps, you should be able to identify the cause of the error and resolve the DNS resolution and repository access issue in Argo CD.

### Amazon EKS Node Group Update

[Updating a managed node group](https://docs.aws.amazon.com/eks/latest/userguide/update-managed-node-group.html)

[Self-managed node updates](https://docs.aws.amazon.com/eks/latest/userguide/update-stack.html)

## Day 9

### [Kiali Topology Graph](https://kiali.io/docs/features/topology/#graph)

#### [Graph Types](https://kiali.io/docs/features/topology/#graph-types)

four different traffic-graph renderings

- The ***workload graph*** provides the a detailed view of communication between workloads

- The ***app graph*** aggregates the workloads with the same app labeling, which provides a more logical view

- The ***versioned app*** graph aggregates by app, but breaks out the different versions providing traffic breakdowns that are version-specific

- The ***service graph*** provides a high-level view, which aggregates all traffic for defined services

### Service Mesh Dashboard

- Meshery
- Kiali
- Service Graph
- Istio Dashboard
- Linkerd Dashboard
- Consul Kiali
- OpenCensus Dashboard

### Kubernetes Image Pull Policy

[The imagePullPolicy for a container and the tag of the image](https://kubernetes.io/docs/concepts/containers/images/#image-pull-policy)

- ***IfNotPresent***

the image is pulled only if it is not already present locally.

- ***Always***

every time the kubelet launches a container, the kubelet queries the container image registry to resolve the name to an image digest. If the kubelet has a container image with that exact digest cached locally, the kubelet uses its cached image; otherwise, the kubelet pulls the image with the resolved digest, and uses that image to launch the container.

- ***Never***

the kubelet does not try fetching the image. If the image is somehow already present locally, the kubelet attempts to start the container; otherwise, startup fails. See pre-pulled images for more details.

### npm install fsevents

[npm install error (code EBADPLATFORM)](https://stackoverflow.com/questions/49475492/npm-install-error-code-ebadplatform)

[package-lock.json: The Complete Guide](https://medium.com/helpshift-engineering/package-lock-json-the-complete-guide-2ae40175ebdd)

`package.json` is a versioning file that primarily contains the list of dependencies (libraries) your node.js project needs to run

`package-lock.json` is a lockfile that contains information about the dependencies/packages with their ***exact version numbers*** that were installed for a node.js project

## Day 10

### Ingress

[Kubernetes Documentation / Concepts / Services, Load Balancing, and Networking / Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/)

[Why And How Of Kubernetes Ingress (And Networking)](https://getenroute.io/blog/ingress-controller-kubernetes-api-gateway-secure-service-jwt-oauth-oidc-network-namespace/)

```sh
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
```
