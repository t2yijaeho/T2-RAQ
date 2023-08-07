# MSP T3 Cloud Techinical Architecture Rarely Asked Questions

## Day 1

### [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)

- Operational excellence
- Security
- Reliability
- Performance efficiency
- Cost optimization
- Sustainability

## Day 2

### [AWS Well-Architected Labs](https://wellarchitectedlabs.com/)

## Day 3

### VPC settings for AWS Cloud9

[VPC settings for AWS Cloud9 Development Environments](https://docs.aws.amazon.com/cloud9/latest/user-guide/vpc-settings.html)

- Same AWS account and AWS Region as the AWS Cloud9
- Have a public subnet
- Attach an internet gateway
- Have a route table with a minimum set of routes
- Associated security groups
- Network ACL must allow a minimum set of inbound and outbound traffic

[Default VPC components](https://docs.aws.amazon.com/vpc/latest/userguide/default-vpc.html#default-vpc-components)

### AWS Cloud9 failed to retrieve file

> MacOS Chrome browser

```Text
Failed to write to 'c9gdbshim.js'. Failed to retrieve resource from https://vfs-cloud9.us-east-1.console.aws.amazon.com/vfs/ca4bc0ca154e4f9bb92cd1f5faa3cec6/home/.c9/bin/c9gdbshim.js with code 0.
```

### Here Documents

[Advanced Bash-Scripting Guide: Here Documents](https://tldp.org/LDP/abs/html/here-docs.html)

### Cloud Init

#### User Data log

[How can I send user-data output to the console logs on an EC2 instance running Amazon Linux or Amazon Linux 2?](https://repost.aws/knowledge-center/ec2-linux-log-user-data)

[Cloud Init Logging](https://canonical-cloud-init.readthedocs-hosted.com/en/latest/development/logging.html)

[User Data shell script vs Cloud init directive](https://stackoverflow.com/questions/63921500/how-to-get-user-data-logs-in-terraform)

### Terraform Modules Sources

When downloading module package directories in Terraform, if it is configured to perform a Git clone internally, Git configuration may be required

[Module Sources](https://developer.hashicorp.com/terraform/language/modules/sources)

### Terraform install on WSL

[AWS Terraform CLI Install](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)

### Terraform Console

[The terraform console command provides an interactive console for evaluating expressions](https://developer.hashicorp.com/terraform/cli/commands/console)

## Day 4

### GitOps Console

- Commit: Push to a Git repository
- PaC Install: Create Package Directory to a Git repository and Push Package
- Register: Create an Argo CD application
- Sync: Synchronize an Argo CD application

### VS Code Remote SSH - The process tried to write to a nonexistent pipe

This error message can occur for several reasons when using VS Code's Remote-SSH extension.

- One possible solution is to add the absolute file path to a custom SSH config file (C:\\Users\\{USERNAME}\\.ssh\\config)

- Another solution is to delete the known_hosts file under the directory C:\\Users\\[your-username]\\.ssh

1. [SSH - VScode remote connection error: The process tried to write to a nonexistent pipe](https://stackoverflow.com/questions/60335069/vscode-remote-connection-error-the-process-tried-to-write-to-a-nonexistent-pipe)

2. [Visual Studio Code - vscode can't ssh connect "The process tried to write to a nonexistent pipe"](https://stackoverflow.com/questions/65193292/vscode-cant-ssh-connect-the-process-tried-to-write-to-a-nonexistent-pipe)

3. [Remote Ssh - The process tried to write to a nonexistent pipe](https://github.com/microsoft/vscode-remote-release/issues/1398)

4. [Testing Remote-SSH: No "nonexistent pipe" error popup](https://github.com/microsoft/vscode-remote-release/issues/5770)

5. [Don't show "The process tried to write to a nonexistent pipe"](https://github.com/microsoft/vscode-remote-release/issues/5723)


### Troubleshoot instances

[Working with CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/get-and-view-cloudtrail-log-files.html)

[Troubleshoot instances with failed status checks](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/TroubleshootingInstances.html)

### Prometheus Operator Concept

[Introducing Operators: Putting Operational Knowledge into Software](https://web.archive.org/web/20170129131616/https://coreos.com/blog/introducing-operators.html)

```Text
Q: How is this different than StatefulSets (previously PetSets)?

A: StatefulSets are designed to enable support in Kubernetes for applications that require the cluster to give them "stateful resources" like static IPs and storage. Applications that need this more stateful deployment model still need Operator automation to alert and act on failure, backup, or reconfigure. So, an Operator for applications needing these deployment properties could use StatefulSets instead of leveraging ReplicaSets or Deployments.

Q: How is this different from configuration management like Puppet or Chef?

A: Containers and Kubernetes are the big differentiation that make Operators possible. With these two technologies deploying new software, coordinating distributed configuration, and checking on multi-host system state is consistent and easy using Kubernetes APIs. Operators glue these primitives together in a useful way for application consumers; it isn't just about configuration but the entire, live, application state.

Q: How is this different than Helm?

A: Helm is a tool for packaging multiple Kubernetes resources into a single package. The concept of packaging up multiple applications together and using Operators that actively manage applications are complementary. For example, traefik is a load balancer that can use etcd as its backend database. You could create a Helm Chart that deploys a traefik Deployment and etcd cluster instance together. The etcd cluster would then be deployed and managed by the etcd Operator.
```

[Kubernetes operator vs. controller: What's the difference?](https://www.techtarget.com/searchitoperations/tip/Kubernetes-operator-vs-controller-Whats-the-difference)

[OperatorHub.io](https://operatorhub.io/)

[**CAPABILITY LEVEL**](https://operatorframework.io/what/)

- Basic Install
- Seamless Upgrades
- Full Lifecycle
- Deep Insights
- Auto Pilot

### Prometheus Operator Install

[Imperative object configuration](https://kubernetes.io/docs/concepts/overview/working-with-objects/object-management/#imperative-object-configuration)

[Declarative object configuration](https://kubernetes.io/docs/concepts/overview/working-with-objects/object-management/#declarative-object-configuration)

The content presented in the lab may differ from the actual production environment setup as it demonstrates the installation of only a subset of the stack to quick start experience Prometheus Operator

To configure Prometheus Operator, the following three types are suggested:

[Prometheus Operator vs. kube-prometheus vs. community helm chart](https://github.com/prometheus-operator/prometheus-operator#prometheus-operator-vs-kube-prometheus-vs-community-helm-chart)

#### Prometheus Operator

- uses Kubernetes custom resources to simplify the deployment and configuration
- Prometheus, Alertmanager, and related monitoring components

#### kube-prometheus

- provides example configurations for a complete cluster monitoring stack
- includes deployment of multiple Prometheus and Alertmanager instances, metrics exporters such as the node_exporter for gathering node metrics, scrape target configuration linking Prometheus to various metrics endpoints, and example alerting rules for notification of potential issues in the cluster

#### helm chart

- provides a similar feature set to kube-prometheus
- maintained by the Prometheus community

## Day 5

### Secrets management

[Secret Management in GitOps](https://argo-cd.readthedocs.io/en/stable/operator-manual/secret-management/)

- `External secret management systems` like HashiCorp Vault, Azure Key Vault, AWS Secrets Manager, or Google Cloud Secret Manager. GitOps pipelines can retrieve the secrets during application deployment. The secrets are stored externally, separate from the Git repository, and accessed by the deployment pipeline through APIs or integration mechanism
- `Encrypted secrets in Git repositories`
- `Environment-specific secrets with GitOps overlays` secrets are managed as part of the GitOps configuration

Best practices

1. Use a dedicated secret management system
2. Avoid storing secrets directly in Kubernetes manifests
3. Encrypt secrets at rest and in transit
4. Use RBAC and least privilege principles
5. Implement strong authentication and authorization mechanisms
6. Regularly rotate and manage secrets
7. Monitor and audit secret access
8. Securely distribute and manage secret access
9. Implement defense-in-depth measures
10. Regularly update and patch systems

### Helm Revision

Three Big Concepts

A ***`Chart`*** is a Helm package. It contains all of the resource definitions necessary to run an application, tool, or service inside of a Kubernetes cluster. Think of it like the Kubernetes equivalent of a Homebrew formula, an Apt dpkg, or a Yum RPM file.

A ***`Repository`*** is the place where charts can be collected and shared. It's like Perl's CPAN archive or the Fedora Package Database, but for Kubernetes packages.

A ***`Release`*** is an instance of a chart running in a Kubernetes cluster. One chart can often be installed many times into the same cluster. And each time it is installed, a new release is created. Consider a MySQL chart. If you want two databases running in your cluster, you can install that chart twice. Each one will have its own release, which will in turn have its own release name.

>Helm installs charts into Kubernetes, creating a new release for each installation. And to find new charts, you can search Helm chart repositories

Historical revisions for a given release

[Helm History](https://helm.sh/docs/helm/helm_history/)

Roll back a release to a previous revision

[Helm Rollback](https://helm.sh/docs/helm/helm_rollback/)

### Sealed Secret Architecture

[Sealed Secrets for Kubernetes](https://github.com/bitnami-labs/sealed-secrets)

[How to Handle Secrets Like a Pro Using Gitops](https://codefresh.io/blog/handle-secrets-like-pro-using-gitops/)

1. You create a plain Kubernetes secret locally. You should never commit this anywhere
2. You use kubeseal to encrypt the secret in a SealedSecret
3. You delete the original secret from your workstation and apply to the cluster the sealed secret
4. You can optionally commit the Sealed secret to Git
5. You deploy your application that expects normal Kuberentes secrets to function (The application needs no modifications of any kind.)
6. The controller decrypts the Sealed secrets and passes them to your application as plain secrets
7. The application works as usual

[Kubernetes Secrets Are Not Really Secret](https://auth0.com/blog/kubernetes-secrets-management/)

1. Encrypt the secret on the developer machine using a public key and the kubeseal CLI. This encodes the encrypted secret into a Kubernetes Custom Resource Definition (CRD)
2. Deploy the CRD to the target cluster
3. The Sealed Secret controller decrypts the secret using a private key on the target cluster to produce a standard Kubernetes secret

[Use AWS Secrets Manager secrets in Amazon Elastic Kubernetes Service](https://docs.aws.amazon.com/secretsmanager/latest/userguide/integrating_csi_driver.html)

[Managing secrets deployment in Kubernetes using Sealed Secrets](https://aws.amazon.com/blogs/opensource/managing-secrets-deployment-in-kubernetes-using-sealed-secrets/)

## Day 6

### Domain Driven Design

More detailed information about Domain-Driven Design is covered in the Cloud Application Architecture (CAA) course.

For related content, please refer to the relevant course materials in Confluence.

```text
Day5 4. Definition of Cloud Native Applications and Design Strategies
  - Developing Cloud Native Applications_4.pdf
```

[Modelling Reactive Systems with Event Storming and Domain-Driven Design](https://blog.redelastic.com/corporate-arts-crafts-modelling-reactive-systems-with-event-storming-73c6236f5dd7)

```text
Day6 6. Agile SOA Development, Extreme Programming & DevOps
 - 6.1. Agile Service Analysis and Design Methodology.pdf
 - 6.2. Agile Service Composition Design Methodology.pdf
```

Please refer to the following for information related to the Tanzu methodology used in some of our client projects and the tools being used:

[Event Storming](https://tanzu.vmware.com/developer/practices/event-storming/)

[Real World Examples (via Miro)](https://miro.com/app/board/o9J_kzaSk0E=/)

### Istio Installation

[Which Istio installation method should I use?](https://istio.io/latest/about/faq/#install-method-selection)

[Installation Guides](https://istio.io/latest/docs/setup/install/)

### Istio Sidecar Proxies

[Installing the Sidecar](https://istio.io/latest/docs/setup/additional-setup/sidecar-injection/)

[Istio CNI plugin](https://github.com/istio/istio/tree/master/cni)

[Install Istio with the Istio CNI plugin](https://istio.io/latest/docs/setup/additional-setup/cni/)

[Compare istio-init, istio-cni, and the Istio CNI plugin for handling pod networking functionality](https://www.redhat.com/architect/istio-CNI-plugin)

### Istio Traffic Management

[Istio Traffic Management](https://istio.io/latest/docs/tasks/traffic-management/)

## Day 7

### Kibana Dev console

[cat indices API](https://www.elastic.co/guide/en/elasticsearch/reference/current/cat-indices.html)

[Get mapping API](https://www.elastic.co/guide/en/elasticsearch/reference/current/indices-get-mapping.html)

### fluentd

```Yaml

The specific errors you see in the log are "kubelet upstream connection error." This typically indicates a problem establishing a connection between the kubelet and the upstream Kubernetes API server. The kubelet needs to communicate with the API server to receive instructions and send updates about the containers it manages.

Several factors can cause these errors, including network connectivity issues, misconfiguration of the kubelet, or problems with the Kubernetes API server itself. Here are a few possible reasons for the kubelet upstream connection errors:

Network connectivity: Ensure that the network connectivity between the node running the kubelet and the Kubernetes API server is functioning correctly. Check for any firewall rules, network policies, or other factors that could be blocking the communication.

DNS resolution: The kubelet relies on DNS to resolve the API server's hostname. Ensure that DNS resolution is configured correctly on the node running the kubelet, and the API server's hostname can be resolved.

API server misconfiguration: Check the configuration of the Kubernetes API server to ensure it is set up correctly and is accessible by the kubelet. Verify the API server's address, port, and any relevant authentication or TLS settings.

Kubelet configuration: Review the kubelet's configuration to ensure it is properly configured to connect to the API server. Check the kubelet's command-line flags, configuration file, or any environment variables that affect its connectivity.

API server issues: If none of the above steps resolve the issue, there may be problems with the Kubernetes API server itself. Check the API server logs and investigate if there are any errors or issues reported.

It's recommended to further investigate the specific error messages, review the Kubernetes cluster configuration, and consult the Kubernetes documentation or relevant support resources to troubleshoot and resolve the kubelet upstream connection errors.


```

### Kibana disconnect from Elastic Search

- `F5` or `Ctrl` + `F5` to reconnect

### node(s) didn't have free ports for the requested pod ports

- disable lightweight prometheus and kiali-server in eMarket app

## Day 8

### Scouter

Windows > Reset Perspective

### APM

[Tracing CNCF Cloud Native Interactive Landscape](https://landscape.cncf.io/card-mode?category=tracing)

- [Jaeger: A distributed tracing system that helps you to track requests as they travel through your distributed system](https://www.jaegertracing.io/)
- [Zipkin: Open source distributed tracing system that is similar to Jaeger](https://zipkin.io/)
- [Elastic APM: An open source application performance monitoring (APM) system that is built on top of Elasticsearch](https://www.elastic.co/observability/application-performance-monitoring)
- [SigNoz](https://signoz.io/)
- [Glowroot: A lightweight and easy-to-use APM system that is designed for Java applications](https://glowroot.org/)
- [Scouter: A Java-specific APM system that is designed for high-performance applications](https://github.com/scouter-project/scouter)


### Terraform module version conflict

```Bash
ubuntu@cta:~/perfStation_IaC$ terraform plan
╷
│ Error: Unsupported argument
│
│   on main.tf line 37, in module "eks_blueprints":
│   37:   cluster_name = local.cluster_name
│
│ An argument named "cluster_name" is not expected here.
╵
╷
│ Error: Unsupported argument
│
│   on main.tf line 38, in module "eks_blueprints":
│   38:   cluster_version = local.cluster_version
│
│ An argument named "cluster_version" is not expected here.
╵
╷
│ Error: Unsupported argument
│
│   on main.tf line 40, in module "eks_blueprints":
│   40:   vpc_id             = module.vpc.vpc_id
│
│ An argument named "vpc_id" is not expected here.
╵
╷
│ Error: Unsupported argument
│
│   on main.tf line 41, in module "eks_blueprints":
│   41:   private_subnet_ids = module.vpc.private_subnets
│
│ An argument named "private_subnet_ids" is not expected here.
╵
╷
│ Error: Unsupported argument
│
│   on main.tf line 43, in module "eks_blueprints":
│   43:   cluster_enabled_log_types = []
│
│ An argument named "cluster_enabled_log_types" is not expected
│ here.
╵
╷
│ Error: Unsupported argument
│
│   on main.tf line 45, in module "eks_blueprints":
│   45:   managed_node_groups = {
│
│ An argument named "managed_node_groups" is not expected here.
╵
ubuntu@cta:~/perfStation_IaC$
```

main.tf module "eks_blueprints" "eks_blueprints_kubernetes_addons"

```Bash
source = "github.com/aws-ia/terraform-aws-eks-blueprints.git?ref=v4.32.0"
source = "github.com/aws-ia/terraform-aws-eks-blueprints.git?ref=v4.32.0/modules/kubernetes-addons"
```

[aws-ia/terraform-aws-eks-blueprints v4.32.0 final release before v5.0](https://github.com/aws-ia/terraform-aws-eks-blueprints/releases/tag/v4.32.0)

[Moving forward with v5 of EKS Blueprints #1421](https://github.com/aws-ia/terraform-aws-eks-blueprints/issues/1421)

[Amazon EKS Blueprints for Terraform v4 to v5 Migration](https://aws-ia.github.io/terraform-aws-eks-blueprints/main/v4-to-v5/cluster/)

### Specify terraform module version

#### Version argument

When you specify the version using the version argument, Terraform will automatically download the specified version of the module from the Terraform Registry or another supported module source. This is the recommended way to specify the version of a module.

>it’s generally recommended to use the version argument whenever possible, as it provides better versioning and dependency management features.

#### Ref parameter in the source argument

When you specify the version using the ref parameter in the source argument, you’re telling Terraform to download the module from a specific Git reference, such as a branch, tag, or commit. In your example, you’re specifying that Terraform should download the module from the v4.32.0 tag in the github.com/aws-ia/terraform-aws-eks-blueprints repository.

>Using the ref parameter can be useful if you want to use a specific version of a module that is not available in the Terraform Registry or another supported module source.

### Apache JMeter HTTP(S) Test Script Recorder

[Apache JMeter HTTP(S) Test Script Recorder](https://jmeter.apache.org/usermanual/jmeter_proxy_step_by_step.html)

### Terraform Command: output

[Terraform Command: output](https://developer.hashicorp.com/terraform/cli/commands/output)

### vCPU Service Quota

[Amazon EC2 instance types](https://aws.amazon.com/ec2/instance-types/)

```Yaml
AWS managemnet console menu:
    Service Quotas > AWS services > Amazon Elastic Compute Cloud (Amazon EC2) > Running On-Demand Standard (A, C, D, H, I, M, R, T, Z) instances
```

[Running On-Demand Standard (A, C, D, H, I, M, R, T, Z) instances](https://us-east-1.console.aws.amazon.com/servicequotas/home/services/ec2/quotas/L-1216C47A)

```Bash
aws service-quotas request-service-quota-increase \
    --service-code ec2 \
    --region us-east-1 \
    --quota-code L-1216C47A \
    --desired-value 128
```

### Saturation point vs Critical point

Define the limits of a system's performance

#### Critical point

- The point at which the system will fail
- To optimize the system's performance
- System crashes

#### Saturation point

- The point at which the system can no longer handle any additional load
- Use	To ensure that the system is not overloaded
- System slows down

>The saturation point for the web server might be the point at which the server can no longer handle more than 1000 concurrent requests per second. The critical point for the web server might be the point at which the server will crash if it receives more than 1500 concurrent requests per second

## Day 9

### Persistent Volume on Different Zone

```Yaml
Pod:
  emarket-jaeger-agent-g29vp
REASON:
  FailedScheduling
MESSAGE:
  0/3 nodes are available: 1 Insufficient cpu. preemption: 0/3 nodes are available: 3 No preemption victims found for incoming pod
```

```Yaml
pod:
  nosql-data-0
 SUMMARY EVENTS LOGS
REASON:
  FailedScheduling
MESSAGE:
  "0/3 nodes are available: 1 Insufficient cpu, 2 node(s) had volume node affinity conflict. preemption: 0/3 nodes are available: 1 No preemption victims found for incoming pod, 2 Preemption is not helpful for scheduling."
```

```Bash
  Type     Reason                  Age                   From                     Message
  ----     ------                  ----                  ----                     -------
  Warning  FailedScheduling        6m55s (x10 over 46m)  default-scheduler        0/1 nodes are available: 1 node(s) had volume node affinity conflict. preemption: 0/1 nodes are available: 1 Preemption is not helpful for scheduling.
```

[Kubernetes Pod Warning: 1 node(s) had volume node affinity conflict](https://stackoverflow.com/questions/51946393/kubernetes-pod-warning-1-nodes-had-volume-node-affinity-conflict)

```Yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: gp2
parameters:
  fsType: ext4
  type: gp2
provisioner: kubernetes.io/aws-ebs
reclaimPolicy: Delete
volumeBindingMode: WaitForFirstConsumer
allowedTopologies:
- matchLabelExpressions:
  - key: failure-domain.beta.kubernetes.io/zone
    values:
    - eu-central-1a
    - eu-central-1b
```

[Google Compute Engine Persistent Disk CSI Driver](https://github.com/kubernetes-sigs/gcp-compute-persistent-disk-csi-driver)

### AWS Default Network Access Control List (ACL)

Default ACL has certain properties that cannot be deleted, which is why you see that message. However, it will be removed along with the deletion of the VPC, so it will also be removed from the state file.

[Resource: aws_default_network_acl](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/default_network_acl)

### AWS Security group multiple rules

[Security group rules](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/security-group-rules.html#:~:text=If%20there%20is%20more%20than%20one%20rule%20for%20a%20specific%20port%2C%20Amazon%20EC2%20applies%20the%20most%20permissive%20rule.%20For%20example%2C%20if%20you%20have%20a%20rule%20that%20allows%20access%20to%20TCP%20port%2022%20(SSH)%20from%20IP%20address%20203.0.113.1%2C%20and%20another%20rule%20that%20allows%20access%20to%20TCP%20port%2022%20from%20everyone%2C%20everyone%20has%20access%20to%20TCP%20port%2022.)

>If there is more than one rule for a specific port, Amazon EC2 ***applies the most permissive rule***. For example, if you have a rule that allows access to TCP port 22 (SSH) from IP address 203.0.113.1, and another rule that allows access to TCP port 22 from everyone, everyone has access to TCP port 22

### Pod Pending

Check the current state of the Pod and recent events with `describe` command

```sh
kubectl get pods --field-selector=status.phase=Pending
```

```sh
kubectl describe pod <PENDING POD NAME>
```

[How to debug Kubernetes Pending pods and scheduling failures](https://www.datadoghq.com/blog/debug-kubernetes-pending-pods/)

[Troubleshooting Kubernetes Pods: Stuck in a "Pending" State](https://www.blinkops.com/blog/troubleshooting-kubernetes-pods-stuck-in-pending-state)

[Debug Pods](https://kubernetes.io/docs/tasks/debug/debug-application/debug-pods/)


## Day 10

### GeoIP

1-2-10. location-api pod

```Bash
pymongo.errors.ServerSelectionTimeoutError: No replica set members available for set name "rs0"
```

### CrashLoopBackOff

[Kubernetes CrashLoopBackOff Error: What It Is and How to Fix It](https://komodor.com/learn/how-to-fix-crashloopbackoff-kubernetes-error/)

>Error indicates that a pod failed to start, Kubernetes tried to restart it, and it continued to fail repeatedly

By default, a pod’s restart policy is , meaning it should always restart on failure (other options are ).

>Depending on the restart policy(Always, Never, OnFailure) defined in the pod template, Kubernetes might try to restart the pod multiple times
>Every time the pod is restarted, Kubernetes waits for a longer and longer time, known as a “backoff delay”. During this process, Kubernetes displays the CrashLoopBackOff error

#### Troubleshoot

1. Check for Back Off Restarting Failed Container

    ```sh
    kubectl describe pod <name>
    ```

2. Check Logs From Previous Container Instance

    ```sh
    kubectl logs --previous --tail 10
    ```

3. Check Deployment Logs

    ```sh
    kubectl logs -f deploy/ -n
    ```

4. Enter into the CrashLoop Container

    ```sh
    kubectl exec -it <name> -- /bin/bash
    ```
