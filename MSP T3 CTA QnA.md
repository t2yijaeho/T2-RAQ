# MSP T3 Cloud Techinical Architecture Rarely Asked Questions

## Day 1

[AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)

- Operational excellence
- Security
- Reliability
- Performance efficiency
- Cost optimization
- Sustainability

## Day 2

[AWS Well-Architected Labs](https://wellarchitectedlabs.com/)

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
- Register: Create an Argo CD application
- Sync: Synchronize an Argo CD application

### VS Code Remote SSH - The process tried to write to a nonexistent pipe

This error message can occur for several reasons when using VS Code's Remote-SSH extension. 

- One possible solution is to add the absolute file path to a custom SSH config file (C:\\Users\\{USERNAME}\\.ssh\\config) ¹. 

- Another solution is to delete the known_hosts file under the directory C:\\Users\\[your-username]\\.ssh ¹. Have you tried any of these solutions?

(1) [SSH - VScode remote connection error: The process tried to write to a nonexistent pipe](https://stackoverflow.com/questions/60335069/vscode-remote-connection-error-the-process-tried-to-write-to-a-nonexistent-pipe)

(2) [Visual Studio Code - vscode can't ssh connect "The process tried to write to a nonexistent pipe"](https://stackoverflow.com/questions/65193292/vscode-cant-ssh-connect-the-process-tried-to-write-to-a-nonexistent-pipe)

(3) [Remote Ssh - The process tried to write to a nonexistent pipe](https://github.com/microsoft/vscode-remote-release/issues/1398)

(4) [Testing Remote-SSH: No "nonexistent pipe" error popup](https://github.com/microsoft/vscode-remote-release/issues/5770)

(5) [Don't show "The process tried to write to a nonexistent pipe"](https://github.com/microsoft/vscode-remote-release/issues/5723)

### Prometheus Operator Concept

[Kubernetes operator vs. controller: What's the difference?](https://www.techtarget.com/searchitoperations/tip/Kubernetes-operator-vs-controller-Whats-the-difference)

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

>Day5 4. Definition of Cloud Native Applications and Design Strategies
>  - Developing Cloud Native Applications_4.pdf

[Modelling Reactive Systems with Event Storming and Domain-Driven Design](https://blog.redelastic.com/corporate-arts-crafts-modelling-reactive-systems-with-event-storming-73c6236f5dd7)

>Day6 6. Agile SOA Development, Extreme Programming & DevOps
> - 6.1. Agile Service Analysis and Design Methodology.pdf
> - 6.2. Agile Service Composition Design Methodology.pdf

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

### Kibana disconnect from Elastic Search

- `F5` or `Ctrl` + `F5` to reconnect

### node(s) didn't have free ports for the requested pod ports

- disable lightweight prometheus and kiali-server in eMarket app

kiki

## Day 8

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

## Day 9

### Persistent Volume on Different Zone

```Yaml
Pod:
  emarket-jaeger-agent-g29vp
REASON:
  FailedScheduling
MESSAGE:
  0/3 nodes are available: 1 Insufficient cpu. preemption: 0/3 nodes are available: 3 No preemption victims found for incoming pod.
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

## Day 10

1-2-10. location-api pod

```Bash
pymongo.errors.ServerSelectionTimeoutError: No replica set members available for set name "rs0"
```
