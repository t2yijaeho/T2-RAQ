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

### Kaniko

## Day 7

### Helm Chart

[Helm Charts - What is and why to use them](https://www.youtube.com/watch?v=tQkxAYgXuPY)

[What is Helm in Kubernetes? Helm and Helm Charts explained | Kubernetes Tutorial 23](https://www.bing.com/videos/search?q=best+video+explain+why+use+helm+chart+youtube&view=detail&mid=6CF58EA85C9A8C7E261B6CF58EA85C9A8C7E261B&FORM=VIRE)

## Day 8

### Cloudtrail

```sh
aws cloudtrail lookup-events --lookup-attributes AttributeKey=EventName,AttributeValue=CreateLoadBalancer --region=us-west-2 | grep <<Coud Loadbalancer DNS Name >>
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

## Day 10

### Ingress

[Kubernetes Documentation / Concepts / Services, Load Balancing, and Networking / Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/)

[Why And How Of Kubernetes Ingress (And Networking)](https://getenroute.io/blog/ingress-controller-kubernetes-api-gateway-secure-service-jwt-oauth-oidc-network-namespace/)

```sh
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
```
