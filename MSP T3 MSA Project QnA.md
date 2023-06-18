# Microservice Project Rarely Asked Question

## Day 1

### VS Code Shortcut

- `Ctrl+Shift+F`

## Day 2

### WSL Clock Skew

```Bash
aws s3 cp
Fatal error: An error occurred (403) when calling the HeadObject operation: Forbidden
```

[WSL Clock skew issues megathread](https://github.com/microsoft/WSL/issues/10006)

Sometimes the WSL clock can become skewed, usually after hibernate or sleep

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

Edit /etc/wsl.conf to have this content:

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
  
  <https://api.ipify.org/>
  <https://checkip.amazonaws.com/>


```Bash
curl https://api.ipify.org/
```

```Bash
curl https://checkip.amazonaws.com/
```

### Skaffold trouble shooting

Skaffold has a diagnose command that can help you run diagnostics on Skaffold works in your project1. You can also use the debug command to run a pipeline in debug mode1

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

## Day 9

### [Kiali Topology Graph](https://kiali.io/docs/features/topology/#graph)

#### [Graph Types](https://kiali.io/docs/features/topology/#graph-types)

four different traffic-graph renderings

- The ***workload graph*** provides the a detailed view of communication between workloads

- The ***app graph*** aggregates the workloads with the same app labeling, which provides a more logical view

- The ***versioned app*** graph aggregates by app, but breaks out the different versions providing traffic breakdowns that are version-specific

- The ***service graph*** provides a high-level view, which aggregates all traffic for defined services

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

wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
