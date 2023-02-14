# Rarely Asked Questions

## Q00. Basic

***Kteyboard shortcuts***
* `Windows Logo` + `Shift` + `S` : Microsoft Windows Screenshot
* `Ctrl` + `Shift` + `S` : Spring Tool Suite Save all files
* `Ctrl`+ `Shift`+ `O` : Spring Tool Suite Oraganize import
* `Ctrl`+ `Shift`+ `R` : Spring Tool Suite Open Search for resources
* `Ctrl` + `Shift`+ `Escape` : Microsoft Windows Task manager
* `Ctrl` + `F5` : Web Browser Hard refresh

* Gradle Tasks menu STS(Spring Tool Suite) upper menu `Windows` > `Show View` > `Other` > (Search) `Gradle Tasks` Select and `Open`
* STS upper menu `Windows` > `Show View` > `Package Explorer`

* Current textbook location (table of contents number) and screenshot
* There is a 'search' function at the top of the slack. If it is a similar error, it is useful to refer to the solution

## Q01. OpenAPI Specification Reference

* OpenAPI definitions syntax error can be corrected by editor linting
* Reference to OpenAPI Specifications structure

  <https://oai.github.io/Documentation/specification-structure.html>
  <https://swagger.io/specification/#specification>

* Reference to API Server

  <https://oai.github.io/Documentation/specification-servers.html>
  <https://swagger.io/docs/specification/api-host-and-base-path/>

* OpenAPI Parameter Object

  [The Parameter Object](https://oai.github.io/Documentation/specification-parameters.html#the-parameter-object)


* OpenAPI Specification

  [The OpenAPI Specification Explained](https://oai.github.io/Documentation/specification.html#the-openapi-specification-explained)


* There may be differences depending on the version, so you need to check the version when referring to the guide document
* The version used for practice is 3.0.1

  [3.1.0](https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.1.0.md)

  [Version archive](https://github.com/OAI/OpenAPI-Specification/blob/main/versions)

  [3.0.1](https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.1.md)


## Q02. OpenAPI Syntax

* OpenAPI definitions can be written in JSON or YAML
* when expressing strings YAML does not require quotation marks, unlike JSON, except when specifically specified

## Q03. Terraform Backend

* Use Amazon S3 for terraform state files  
  <https://www.terraform.io/language/settings/backends/s3>
* The Dynamo table key name uses the bucket and key values of the backend settings
* Various methods are possible depending on the terraform usage scenario or configuration environment
* Necessary to consider the backend state file lock and multi-user environment.
* The direct use of file locking is to limit access to state files

## Q04. ArgoCD istio app failed to syncing AWS load balancer

  ```msg
  Error syncing load balancer:
  failed to ensure load balancer:
  error creating load balancer: 
  ResourceInUse: 
  The allocation IDs are not available for use
  tstatus code: 400
  ```

1. Argo CD `emarket`, `istio` app delete
2. AWS management console `EC2>Load Balancers`  Active Network Load balancer(Type: Network) delete
3. AWS management console `EC2>Target groups` Istio related target group(K8s-istiosys-...) delete
4. Argo CD `istio` app create
5. AWS management console `EC2>Load Balancers` Confirm Network Load balancer active state
6. Argo CD `emarket` app create
7. AWS management console `Certificate Manager > Certificates Key Status`

## Q05. Oracle to PostgreSQL Open Source Migration Tool

  [The Complete Oracle to Postgres Migration Guide](https://www.enterprisedb.com/blog/the-complete-oracle-to-postgresql-migration-guide-tutorial-move-convert-database-oracle-alternative)

  [ora2pg](https://github.com/darold/ora2pg)

## Q06. OpenAPI Specification(OAS) Null data type

* In OAS 3.0, the property indicates that the corresponding data value may be null

  <https://swagger.io/docs/specification/data-models/data-types/#null>

* Null data type is available in OAS 3.1

  <https://spec.openapis.org/oas/v3.1.0.html#data-types>

## Q07. Terraform state lock

* When the terraform code is executed normally, the MD5 hash value for the terraform state file stored in S3 in the item with the s3 object key as the partition key in the terraform-lock table of DynamoDB

  [Protecting Access to Workspace State](https://developer.hashicorp.com/terraform/language/settings/backends/s3#protecting-access-to-workspace-state)

## Q08. AWS Database Migration Service (DMS) Logging

* If a database migration task error occurs, you can check the simple error history on the `Table statistics` tab on the task detail screen.
* To check the detailed error history, you can enable cloud watch logging and check the detailed log history

  [AWS DMS task in an error status](https://aws.amazon.com/premiumsupport/knowledge-center/dms-task-error-status/)

  [Logging task settings](https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Tasks.CustomizingTasks.TaskSettings.Logging.html)

## Q09. Linux single dot directory

[Dot Definition](http://www.linfo.org/dot.html)

>This is a short string (i.e., sequence of characters) that is added to the end of the base name (i.e., the main part of the name) of a file or directory in order to indicate the type of file or directory.

>On Unix-like operating systems every directory contains, as a minimum, an object represented by a single dot and another represented by two successive dots. The former refers to the directory itself and the latter refers to its parent directory (i.e., the directory that contains it). These items are automatically created in every directory, as can be seen by using the ls command with its -a option (which instructs it to show all of its contents, including hidden items).

* Single Dot: Directory itself
* Double Dots: Parent directory

```Shell
git add .
git add -A
```

## Q10. AWS DMS Task Expressions

* AWS DMS supports SQLite scripts used in Brightics for transformation rule expressions as well as self-action

  [Using SQLite functions to build expressions](https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Tasks.CustomizingTasks.TableMapping.SelectionTransformation.Expressions.html#CHAP_Tasks.CustomizingTasks.TableMapping.SelectionTransformation.Expressions-SQLite)

  [Transform column content and data type using AWS DMS](https://aws.amazon.com/blogs/database/transform-column-content-and-data-type-using-aws-dms/)

## Q11. Junit Parameterized Tests

* [Junit Parameterized Tests](https://junit.org/junit5/docs/current/user-guide/#writing-tests-parameterized-tests)

## Q12. Terraform Syntax

* If the terraform is expressed as JavaScript Object Notation (JSON), Double Quotes should be strictly applied, but not in the case of HCL (HashiCorp Configuration Language).

* In most examples, quotation marks are used as a practice

  [JSON Syntax](https://www.w3schools.com/js/js_json_syntax.asp)

  [HCL Native Syntax Specification](https://github.com/hashicorp/hcl/blob/main/hclsyntax/spec.md)

  [Terraform Configuration Syntax](https://developer.hashicorp.com/terraform/language/syntax/configuration?optInFrom=terraform-io)

## Q13. Terraform Data sources

>To use information defined outside of Terraform, defined by another separate Terraform configuration, or modified by functions

  [Terraform Data sources](https://developer.hashicorp.com/terraform/language/data-sources)

  [Data Source: aws_instance](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/instance)

## Q14. MariaDB Backtick

* MariaDB uses a phonetic code (Backtick, located on the left side of keyboard number 1) to distinguish between general object identifiers and reserved words

>Identifiers may be quoted using the backtick character - `. Quoting is optional for identifiers that don't contain special characters, or for identifiers that are not reserved words

[Identifier Names](https://mariadb.com/kb/en/identifier-names/)

## Q15. utf8 vs. utf-8

* What is the diffrence between UTF-8, UTF8 and AL32UTF8?

>UTF-8 is a variable-width Unicode encoding and also a strict superset of 7-bit ASCII. One Unicode character can be 1 byte, 2 bytes, 3 bytes or 4 bytes in UTF-8.

>UTF8(without the dash) is the name of the Oracle character set introduced in Oracle 8.0 that follows the UTF-8 encoding. UTF8 supports UTF-8 encoding up to Unicode standard 3.0 only. 

>AL32UTF8 is the Oracle Unicode character set that supports the supplementary characters defined in the latest Unicode standard

[Oracle unicode](https://www.oracle.com/technetwork/products/globalization/twp-appdev-unicode-10gr2-129234.pdf)

[Locale Data](https://docs.oracle.com/en/database/oracle/oracle-database/18/nlspg/appendix-A-locale-data.html#GUID-A9E30C27-FD47-4552-B670-F41A95B11405)

## Q16. rds_superuser role

>`rdsadmin` – A role that's created to handle many of the management tasks that the administrator with superuser privileges would perform on a standalone PostgreSQL database. This role is used internally by RDS for PostgreSQL for many management tasks.

  [Understanding the rds_superuser role](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Appendix.PostgreSQL.CommonDBATasks.Roles.html#Appendix.PostgreSQL.CommonDBATasks.Roles.rds_superuser)

## Q17. PostgreSQL Schema, Timestamp

  [PostgreSQL Schema](https://www.postgresqltutorial.com/postgresql-administration/postgresql-schema/)
  [Difference Between Schema and Database](https://blog.devart.com/difference-between-schema-database.html)

  [Date/Time Types](https://www.postgresql.org/docs/current/datatype-datetime.html)

## Q18. Convention over Configuration

* src/main src/test directory structure origin

[Convention over configuration](https://en.wikipedia.org/wiki/Convention_over_configuration)

[Maven Reference](https://books.sonatype.com/mvnref-book/reference/installation-sect-conventionConfiguration.html)

[Gradle Reference](https://docs.gradle.org/current/userguide/designing_gradle_plugins.html#convention_over_configuration)

## Q19. Ubuntu 22 version

* which services should be restarted

  <https://discourse.ubuntu.com/t/needrestart-for-servers/21552/1>

* It is about whether to restart the service running in the background for update. It needs to be checked in the production environment, but it is not applicable in training environment
* You can select all services and select OK

  <https://phoenixnap.com/kb/fix-could-not-get-lock-error-ubuntu>

## Q20. ECR Creation error by time sync failure

* If the container or VM time is off the standard time by more than 5 minutes, please reset the time
* The system clock of the container is off Amazon’s clock by more than 5 minutes, the maximum allowed by Amazon’s signature algorithm
  [Time in container is out of sync](https://forums.docker.com/t/time-in-container-is-out-of-sync/16566)
  [Solving "Signature not yet current" Error When Using AWS in Docker](https://zhang-yang.medium.com/solving-signature-not-yet-current-error-when-using-aws-in-docker-c2d8ba314a7e)

## Q21. MobaXterm connection troubleshoot Checklist

1. MobaXterm Configuration

   * `admin_server`: `Private IPv4 address`
   * `bastion_server`: `Public IPv4 address`

2. Security Group Configuration

   * `bastion-sg`: `Inbound rule MyIP`
   * `admin-sg`: `Inbound rule Bastion-sg`

3. Nat Gateway Configuration

   * `Nat Gateway`: `Public Subnet`: `mgmt-public-sub01`

4. Route Tables Configuration

   * `Route Tables`: `mgmt-route-public`: `0.0.0.0/0` `igw-`
   * `Route Tables`: `mgmt-route-private`: `0.0.0.0/0` `nat-`

## Q22. Terraform destroy resources with dependency

  ```bash
  terraform plan -refresh-only
  ```

## Q23. SSH to AWS EKS Worker Nodes

  <https://github.com/awslabs/amazon-eks-ami/issues/161>

  <https://docs.aws.amazon.com/eks/latest/userguide/create-managed-node-group.html>

* Specify networking

    `Configure SSH access to nodes`

    `SSH key pair`

    `Allow SSH remote access from`

## Q24. Amazon RDS Set up EC2 connection

AWS Management Console
  `RDS > Databases > targetdb(-maria)`

Select and set the VM that needs to be connected
  `Actions > Set up EC2 connection`

[Amazon EC2 now offers an automated connection set-up solution between EC2 instance and RDS Database](https://aws.amazon.com/about-aws/whats-new/2022/10/amazon-ec2-automated-connection-solution-ec2-instance-rds-database/)
[Connecting an EC2 instance and an RDS database automatically](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/ec2-rds-connect.html)

## Q25. AWS SCT Alert(Red exclamation) mark

* Items with a red exclamation mark next to them cannot be directly translated from the source to the target
* Right click on the schema in the left-hand panel, and click Create report

[Assessment report warning message](https://docs.aws.amazon.com/SchemaConversionTool/latest/userguide/CHAP_AssessmentReport.WarningMessage.html)

## Q26. AWS UX

1. AWS logo at the top left (Console Home)
2. Top right [Actions] - [Revert to previous Console Home]

## Q27. Usage of Java Interface on a service layer

* Reasons for utilizing interfaces in the service layer
* For using Mock

  [What Is Inheritance?](https://docs.oracle.com/javase/tutorial/java/concepts/inheritance.html)

  [Use of Interfaces on a service layer](https://stackoverflow.com/questions/28693175/use-of-interfaces-on-a-service-layer)

  [Spring Bean CLASS with NO Interface](https://stackoverflow.com/questions/11528061/i-want-to-define-a-spring-bean-class-with-no-interface)

## Q28. Spring Boot Database Initialization Using Basic SQL Scripts

[Initialize a Database Using Basic SQL Scripts](https://docs.spring.io/spring-boot/docs/current/reference/html/howto.html#howto.data-initialization.using-basic-sql-scripts)


## Q29. OpenAPI PUT vs. PATCH

[Use of PUT vs PATCH methods in REST API real life scenarios](https://stackoverflow.com/questions/28459418/use-of-put-vs-patch-methods-in-rest-api-real-life-scenarios)

## Q30. StringIndexOutOfBoundsException

>Getting this error when parsing a file:
java.lang.StringIndexOutOfBoundsException: begin x, end -x, length xx

StringIndexOutOfBounds exceptions with relative server urls when ***`loading from a file path that includes spaces`***

## Q31. KeyCloak logging

```sql
Reason: liquibase.exception.DatabaseException: Column "USER_SETUP_ALLOWED" not found; SQL statement:
ALTER TABLE PUBLIC.AUTHENTICATION_EXECUTION ALTER COLUMN  USER_SETUP_ALLOWED SET DEFAULT NULL [42122-197] [Failed SQL: (42122) ALTER TABLE PUBLIC.AUTHENTICATION_EXECUTION ALTER COLUMN  USER_SETUP_ALLOWED SET DEFAULT NULL]
```

```powershell
kc.bat start --log-level=all --log=console,file
```

## Q32. KeyCloak Client Scope

<https://www.keycloak.org/docs/latest/server_admin/#_role_scope_mappings>

<https://stackoverflow.com/questions/42186537/resources-scopes-permissions-and-policies-in-keycloak>

## Q33. GitHub Personal Access Token

* Considering the general principle of least privilege, it is not considered appropriate to specify a scope other than necessary information
* We should also think about why tokens are used instead of passwords
* For access to the GitHub API, it is recommended to use the newly created fine-grained PAT

## Q34. Git Ignore

[gitignore ](https://git-scm.com/docs/gitignore)

[A collection of .gitignore templates](https://github.com/github/gitignore#a-collection-of-gitignore-templates)

## Q35. JWT Signature

<https://auth0.com/blog/json-web-token-signing-algorithms-overview/>

<https://www.freecodecamp.org/news/how-to-sign-and-validate-json-web-tokens/>

<https://stackoverflow.com/questions/61624189/why-include-header-and-payload-in-jwt-token>

## Q36. Git vs. SVN

* The technical aspect may be important, but if there is no way to harmonize Git's ideas of freedom and openness with the company's security standards, I think what can be obtained by introducing Git will only improve some functions

## Q37. GitHub Personal Access Token instead of password

https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token

## Q38. Spring Boot Admin Exception

https://stackoverflow.com/questions/72068618/spring-boot-admin-java-net-unknownhostexception-failed-to-resolve-saurabh-pc

>spring.boot.admin.client.instance.management-base-url= http://localhost:8081

https://codecentric.github.io/spring-boot-admin/current/

| Property name | Description |
| - | - |
| spring.boot.admin.client.url | Comma separated ordered list of URLs of the Spring Boot Admin server to register at. This triggers the AutoConfiguration. Mandatory. |
| spring.boot.admin.client.instance. management-base-url | Base url for computing the management-url to register with. The path is inferred at runtime, and appended to the base url. |
| spring.boot.admin.client.instance.service-base-url | Base url for computing the service-url to register with. The path is inferred at runtime, and appended to the base url. In Cloudfoundry environments you can switching to https like this: spring.boot.admin.client.instance.service-base-url=https://${vcap.application.uris[0]} |
| spring.boot.admin.client.instance.service-url |Service-url to register with. Can be overridden in case the reachable url is different (e.g. Docker). |

## Q39. Ubuntu install mirror site

```shell
sudo vi /etc/apt/sources.list
%s/archive.ubuntu.com/mirror.kakao.com/
%s/security.ubuntu.com/mirror.kakao.com/
%s/ap-northeast-2.ec2//
```

## Q40. Jenkins Console Output log location

```shell
${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_NUMBER}/log
$JENKINS_HOME/jobs/$JOB_NAME/builds/lastSuccessfulBuild/log
```

[Jenkins "Console Output" log location in filesystem](https://stackoverflow.com/questions/37386581/jenkins-console-output-log-location-in-filesystem)

[How to download a huge console output from Jenkins](https://stackoverflow.com/questions/72759260/how-to-download-a-huge-console-output-from-jenkins)

[Jenkins Viewing logs](https://www.jenkins.io/doc/book/system-administration/viewing-logs/)

[Gradle Logging](https://docs.gradle.org/current/userguide/logging.html)

[git-log](https://git-scm.com/docs/git-log)

## Q41. VPC Network Analyze

* The role of a route table is a resource that has setting values ​​for routes through which subnets, Internet gateways, etc. can exchange network traffic with each other.

* If you simply want to check whether the path is actually properly set, you can use a command-line network utility or a service such as a network analyzer provided by AWS.

`VPC > Reachability Analyzer`

<https://docs.aws.amazon.com/vpc/latest/reachability/what-is-reachability-analyzer.html>

## Q42. User data and cloud-init

* utilize user data to automatically run a script with every restart of Amazon EC2 Linux instance

<https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html#user-data-cloud-init>

<https://cloudinit.readthedocs.io/en/latest/index.html>

<https://help.ubuntu.com/community/CloudInit>

## Q43. Terraform Plan

* If the `Plan` phase is practiced manually in a single user environment, it will be difficult to find any meaning, but
* Useful steps from a workflow perspective when applying automation processes through GitOps in a multi-user environment

[Running Terraform in Automation](https://developer.hashicorp.com/terraform/tutorials/automation/automate-terraform)

## Q44. Terraform error on a specific AWS EC2 Instance Type

```text
 Unsupported: The requested configuration is currently not supported.
 Please check the documentation for supported configurations
```

<https://docs.aws.amazon.com/autoscaling/ec2/userguide/ts-as-instancelaunchfailure.html#ts-as-instancelaunchfailure-3>

## Q45. Terraform Variable Definition Precedence

<https://developer.hashicorp.com/terraform/language/values/variables#variable-definition-precedence>

## Q46. Terraform Variable Definition

* Variable blocks for defining input variables can exist in all Terraform code unless specified by convention or standards and procedures.
* The variable definition file (.tfvars) consists of variable names and assigned values, and can be configured to be assigned or automatically called at code execution.

<https://developer.hashicorp.com/terraform/language/values/variables#variable-definitions-tfvars-files>

## Q47. Amazon DynamoDB Table Items summary

* DynamoDB updates following values approximately every six hours. Recent changes might not be reflected in these values

```text
ItemCount
IndexSizeBytes
TableSizeBytes
```

## Q48. Terraform Best Practices

<https://developer.hashicorp.com/terraform/intro/core-workflow>

<https://cloud.google.com/docs/terraform/best-practices-for-terraform>

<https://github.com/ozbillwang/terraform-best-practices>

## Q49. Terraform variables

1. You can use Local values ​​(Locals) if you only need it in Child Modules
    <https://developer.hashicorp.com/terraform/language/values/locals>

    When different values ​​are required depending on conditions
    <https://stackoverflow.com/questions/60084611/how-best-to-handle-multiple-tfvars-files-that-use-common-tf-files>

2. Output values ​​of child modules are used in the form of module.<MODULE NAME>.<OUTPUT NAME>

    <https://developer.hashicorp.com/terraform/language/values/outputs#accessing-child-module-outputs>

4. `vpc_id = var.vpc_id`
  If vpc_id is in Resource Blocks, vpc_id is a configuration argument to set the resource, and var.vpc_id is an input variable to set the value of the variable

  [Resource Blocks](https://developer.hashicorp.com/terraform/language/resources/syntax)
  [Input Variables](https://developer.hashicorp.com/terraform/language/values/variables)

## Q50. Domain Name Service

1. `route 53 > domain > hosted zone` check whether domain information matches eks-values.yaml
2. `route 53 > domain > hosted zone` Check wheter domain information matches load balancer and modify if necessary

## Q51. Helm Chart Apply

1. Modify Helm Chart eks-values.yaml file
2. Apply textbook 2-1-5, 2-1-6 for Git repository
3. Synchronize eMarket app on ArgoCD

## Q52. Istio path

```text
v1/Service
istio-system
istio-ingressgateway
 SyncFailed
error validating data: [unknown object type "nil" in Service.metadata.annotations.service.beta.kubernetes.io/aws-load-balancer-eip-allocations, unknown object type "nil" in Service.metadata.annotations.service.beta.kubernetes.io/aws-load-balancer-ssl-cert]
```

* Occurs when the path is set incorrectly
* The path is not an key-in input, but selects items to be searched by searching with istio

## Q53. Argo CD app delete

>Argo CD app delete Propagation policy
>
>* Specify propagation policy for deletion of application's resources

### Foreground cascading deletion

* Enters a deletion in progress state
* After deleting all the dependent objects, the controller deletes the owner object
* 
### background cascading deletion

* deletes the owner object immediately  
* controller cleans up the dependent objects in the background

[Kubernetes Cluster Garbage Collection Cascading deletion](https://kubernetes.io/docs/concepts/architecture/garbage-collection/#cascading-deletion)

[Change default deletion propagation policy from foreground to background #5724
](https://github.com/argoproj/argo-cd/issues/5724)

## Q54. MinIO

* MinIO is a multi-cloud object storage solution used to store image resources in eMarket App.
  <https://min.io/docs/minio/kubernetes/upstream/>

* If you can't see the image even though you can access the site, you may need to reconfigure

* When the image registration batch task is finished, unlike other pods, it is treated as ‘Completed’ rather than providing a service in a ‘Running’ state

## Q55. Amazon VPC Subnet sizing

[CIDR Block Calculator](https://cidr.xyz)

<https://docs.aws.amazon.com/vpc/latest/userguide/configure-subnets.html#subnet-sizing>

<https://stackoverflow.com/questions/55320836/how-to-calculate-total-ips-of-a-subnet-in-aws>


* subnet with CIDR block 10.0.0.0/24, the following five IP addresses are reserved

```text
10.0.0.0: Network address
10.0.0.1: Reserved by AWS for the VPC router
10.0.0.2: Reserved by AWS for the DNS server
10.0.0.3: Reserved by AWS for future use
10.0.0.255: Network broadcast address
```

## Q56. A Kubernetes controller for Elastic Load Balancers

* Annotations

***service.beta.kubernetes.io/aws-load-balancer-eip-allocations***

>internet-facing lb only. Length must match the number of subnets

[A Kubernetes controller for Elastic Load Balancers](https://kubernetes-sigs.github.io/aws-load-balancer-controller/)

[Routing with Istio Service Mesh and Amazon EKS](https://aws.amazon.com/blogs/apn/saas-identity-and-routing-with-istio-service-mesh-and-amazon-eks/)

## Q57. hr_comnt.sql script error

>Error starting at line : 33 File @ C:\app\Administrator\product\18.0.0\dbhomeXE\demo\schema\human_resources\hr_comnt.sql

>In command -

>COMMENT ON TABLE regions 
IS 'Regions table that contains region numbers and names. Contains 4 rows; references with the Countries table.'

>COMMENT ON COLUMN regions.region_id
IS 'Primary key of regions table.'

>COMMENT ON COLUMN regions.region_name
IS 'Names of regions. Locations are in the countries of these regions.'

>COMMENT ON TABLE locations
IS 'Locations table that contains specific address of a specific office,
warehouse, and/or production site of a company. Does not store addresses / locations of customers. Contains 23 rows; references with the departments and countries tables. '

>Error report -
>ORA-00933: SQL command not properly ended
>00933. 00000 -  "SQL command not properly ended"

>*Cause:    
*Action:

The error is caused by missing semicolons in the three SQL statements below.
Even if the comment content is not added, the lab is not affected

```
COMMENT ON TABLE regions 
IS 'Regions table that contains region numbers and names. Contains 4 rows; references with the Countries table.'

COMMENT ON COLUMN regions.region_id
IS 'Primary key of regions table.'

COMMENT ON COLUMN regions.region_name
IS 'Names of regions. Locations are in the countries of these regions.'
```

Cause
The message ORA-00933: sql command not properly ended. This error is usually caused by an SQL statement with a clause that is not allowed for that statement. Some examples that might cause this error are:

An INSERT statement with an ORDER BY clause or an INNER JOIN
A DELETE statement with an INNER JOIN or ORDER BY clause
An UPDATE statement with an INNER JOIN
If the SQL syntax is incorrect.
The error also might occur because of using a semicolon ";" at the end or incorrect syntax since the other causes involve joins.

<https://confluence.atlassian.com/bitbucketserverkb/ora-00933-sql-command-not-properly-ended-error-while-starting-bitbucket-server-1086416714.html>

## Q58. Query Result vs. Script Output

* Execute Statement(Run Statement): for a selected individual statement
>executes the statement at the mouse pointer in the Enter SQL Statement box. The SQL statements can include ?bind variables and substitution variables of type VARCHAR2 (although in most cases, VARCHAR2 is automatically converted internally to NUMBER if necessary); a pop-up box is displayed for entering variable values.

* Run Script: for all statements on the worksheet
>executes all statements in the Enter SQL Statement box using the Script Runner. The SQL statements can include substitution variables (but not bind variables) of type VARCHAR2 (although in most cases, VARCHAR2 is automatically converted internally to NUMBER if necessary); a pop-up box is displayed for entering substitution variable values.

>Every time you click the Run Script icon, the linesize value is reset to the system default, which is the width of the Script Output pane. If you want to ensure a specific linesize is in effect, use the set linesize command (for example, set linesize=80) for each Run Script occurrence.

[2.8 Using the SQL Worksheet](https://docs.oracle.com/en/database/oracle/sql-developer/22.2/rptug/sql-developer-concepts-usage.html#GUID-FB7B5B33-3B34-497D-B12A-C30779DE2322:~:text=Execute%20Statement%20executes,Run%20Script%20occurrence.)

In SQL Developer, `Query Result (Run Statement, Ctrl + Enter)` is the content that shows the results of execution of SQL statements, and `Script Output (Run Script that executes several SQL, F5)` is different from the screen showing

[Script Output and Query Result](https://community.oracle.com/tech/developers/discussion/2201870/whats-the-difference-between-script-output-and-query-result)

* Please check the encoding settings for script output in the menu below.

  `Tools - Preferences - Environment - Encoding`

<https://forums.oracle.com/ords/apexds/post/sqldeveloper-editor-encoding-7422>
## Q59. EDB Postgres vs. PostgreSQL

<https://www.commandprompt.com/education/enterprisedb-vs-postgresql/>

<https://www.enterprisedb.com/blog/comparing-edb-postgres-platform-and-postgresql>

## Q60. PostgreSQL Tablespaces

<https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_PostgreSQL.html#PostgreSQL.Concepts.General.FeatureSupport.Tablespaces>

<https://www.postgresql.org/docs/current/manage-ag-tablespaces.html>

## Q61. PostgreSQL Quote Escape

<https://www.postgresql.org/docs/current/sql-syntax-lexical.html>

<https://stackoverflow.com/questions/57430988/postgres-escape-single-and-double-quotes-in-text-field>

## Q62. AWS DMS CDC

* DMS can also be used for continuous change data capture rather than one-time conversion
  
  <https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Task.CDC.html>

## Q63. MariaDB character set and collation

```sql
SELECT * FROM INFORMATION_SCHEMA.SCHEMATA;
```

<https://mariadb.com/kb/en/setting-character-sets-and-collations/#database-level>

## Q64. MarkDown Viewer Dark mode

Difficulties related to HTML tags in Windows Dark Mode after Markdown Viewer update

* Disable Windows dark mode
* Change markdown viewer theme or
* Use another markdown viewer like VS Code

## Q65. AWS DMS Selection rules and actions priority

### Load-order
* The priority for loading tables and views. Tables and views with higher values are loaded first
* A positive integer. The maximum value is 2,147,483,647

## Q66. Troubleshoot connecting AWS EC2 Linux instance

<https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/TroubleshootingInstancesConnecting.html>

## Q67. AWS Regions

* Operate by classifying regions by class considering service usage fee and load
* Services provided by region are different and network latency is also different.
  
[AWS Regional Services List](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/?nc1=h_ls)

[AWS Latency Monitoring](https://www.cloudping.co/grid)

[AWS Connection Health Check](https://clients.amazonworkspaces.com/Health.html)

[What to Consider when Selecting a Region for your Workloads](https://aws.amazon.com/blogs/architecture/what-to-consider-when-selecting-a-region-for-your-workloads/)

[How to select a Region for your workload based on sustainability goals](https://aws.amazon.com/blogs/architecture/how-to-select-a-region-for-your-workload-based-on-sustainability-goals/)

## Q68. Windows Logo

Use of the Windows wave logo ended on August 23, 2012

[Microsoft Unveils a New Look](https://blogs.microsoft.com/blog/2012/08/23/microsoft-unveils-a-new-look/)

[Microsoft Windows Logo Variants](https://logos.fandom.com/wiki/Microsoft_Windows)

## Q69. Amazon EC2 Instance Connect

As with Cloud Shell or Cloud IDE, Amazon EC2 Instance Connect is not accessed directly by the user's local client, but through the endpoint of the service, so the CIDR of the service to be accessed must be registered in the security group of the service.

[Set up EC2 Instance Connect](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-connect-set-up.html)

[Use EC2 Instance Connect to provide secure SSH access to EC2 instances with private IP addresses](https://aws.amazon.com/blogs/security/use-ec2-instance-connect-to-provide-secure-ssh-access-to-ec2-instances-with-private-ip-addresses/)


```Powershell
Set-PSRepository -Name PSGallery -InstallationPolicy Trusted
Get-PSRepository -Name PSGallery
Install-Module -Name AWS.Tools.Installer
Install-Module -Name AWS.Tools.Installer -Force



```

```Bash
sudo apt update
sudo apt install -y jq

curl https://ip-ranges.amazonaws.com/ip-ranges.json > aws_ip-ranges.json
jq '.prefixes[] | select((.region=="us-east-1" or .region=="us-west-2") and .service=="EC2_INSTANCE_CONNECT")' < aws_ip-ranges.json > ec2_instance_connect_ip_ranges.txt

```

## Q70. Jenkins admin password

In general, sensitive passwords are not encrypted in such a way that they can be decrypted.
The Jenkins initial administrator password is provided only for use during installation, and the password is not encrypted with a text conversion algorithm such as Base64.

Initial admin password for jenkins
[Setup Jenkins On Kubernetes](https://www.jenkins.io/doc/book/installing/kubernetes/)

[Reset Jenkins Admin User Password](https://medium.com/@selvarajk/how-to-reset-jenkins-admin-user-password-6fb29d4398bb)


## Q71. git remote

Through the Git Remote command, you can check the storage location to remotely upload the code currently stored in the local repository. If you have multiple repositories or branches, you can check that the desired locations are specified correctly

## Q72. Istio concepts

Istio is one of the Service Mesh solutions, which is applied to solve the complexity of connection between services that can occur in microservice architectures using integrated Side Car Proxy, which is separated from business logic
For more information, see chapter 2 of the operational domain day 4 theory textbook. Please refer to the Deploy Application and lecture videos first.

<https://istio.io/latest/docs/concepts/>
<https://www.opsmx.com/blog/what-is-service-mesh-and-why-is-it-necessary/>

## Q73. AWS DMS Tasks

 Recommend that you refer directly to the user guide for the various features of AWS DMS

[AWS Database Migration Service User Guide](https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Tasks.CustomizingTasks.TableMapping.html)

If you want to practice various cases using SCT and DMS, please also refer to the contents below

[AWS Database Migration Workshop](https://catalog.us-east-1.prod.workshops.aws/workshops/77bdff4f-2d9e-4d68-99ba-248ea95b3aca/en-US)

[Sources for AWS SCT](https://docs.aws.amazon.com/SchemaConversionTool/latest/userguide/CHAP_Source.html)

[Sources for data migration](https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Source.html)
## Q74. Remote Desktop Connection (RDP) Certificate Warnings

(https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/remote-desktop-connection-rdp-certificate-warnings/ba-p/259301)

## Q75. Amazon EC2 Instance lifecycle

[Instance lifecycle](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-lifecycle.html)

[Terminate your instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/terminating-instances.html)

[Troubleshoot instance termination (shutting down)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/TroubleshootingInstancesShuttingDown.html#terminated-instance-still-displaying)

## Q76. Gradle Listing tasks

[Listing tasks](https://docs.gradle.org/current/userguide/command_line_interface.html#sec:listing_tasks)

## Q77. Amazon EC2 Public IPv4 addresses

[Public IPv4 addresses](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-instance-addressing.html#concepts-public-addresses:~:text=We%20release%20your%20instance%27s%20public%20IP%20address%20when%20it%20is%20stopped%2C%20hibernated%2C%20or%20terminated.%20Your%20stopped%20or%20hibernated%20instance%20receives%20a%20new%20public%20IP%20address%20when%20it%20is%20started.)

## Q78. Spring Boot Configuration

[Developing Your First Spring Boot Application](https://docs.spring.io/spring-boot/docs/current/reference/html/getting-started.html#getting-started.first-application)

## Q79. Annotation Interface ExtendWith

[Annotation Interface ExtendWith](https://junit.org/junit5/docs/5.8.0/api/org.junit.jupiter.api/org/junit/jupiter/api/extension/ExtendWith.html)

[SpringExtension](https://rieckpil.de/what-the-heck-is-the-springextension-used-for/)

[Junit 5 with Spring Boot: When to use @ExtendWith Spring or Mockito?](https://stackoverflow.com/questions/61433806/junit-5-with-spring-boot-when-to-use-extendwith-spring-or-mockito)

## Q80. MyBatis 

[10 Spring MyBatis Best Practices](https://climbtheladder.com/10-spring-mybatis-best-practices/)
https://mybatis.org/mybatis-3/getting-started.html

<https://mybatis.org/mybatis-3/getting-started.html>


## Q81. Annotation Processing Generated source directory

[Annotation Processing Generated source directory](https://help.eclipse.org/latest/index.jsp?topic=%2Forg.eclipse.jdt.doc.user%2Freference%2Fref-apt-config.htm)

## Q82. Mockbean

https://www.baeldung.com/java-spring-mockito-mock-mockbean

## Q83. H2 connection mode

Although H2 is often used as an in-memory database in practice, it can also be used disk-based and supports various settings depending on the URL.

[Database URL Overview](http://www.h2database.com/html/features.html#database_url)


## Q84. MariaDB Reserved Words

 It is recommended to refer to the official website or source files for each version for related documents

>Reserved words cannot be used as Identifiers, unless they are quoted.
>The definitive list of reserved words for each version can be found by examining the sql/lex.h and sql/sql_yacc.yy files.

[Reserved Words](https://mariadb.com/kb/en/reserved-words/)

<https://github.com/MariaDB/server/blob/11.0/sql/lex.h>
<https://github.com/MariaDB/server/blob/11.0/sql/sql_yacc.yy>


## Q85. Spring Boot OAuth2 with keycloak

[Spring Boot Oauth2](https://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/htmlsingle/#web.security.oauth2.client)

[Spring Boot OAuth2 with keycloak for Bearer Client](https://ravthiru.medium.com/springboot-oauth2-with-keycloak-for-bearer-client-3a31f608a78)

[SpringBoot OAuth2 with Keycloak as provider](https://ravthiru.medium.com/springboot-oauth2-with-keycloak-as-provider-c31b2897e913)

## Q86. Spring Boot Admin UI Customizing Available Languages

https://codecentric.github.io/spring-boot-admin/current/#_customizing_available_languages

## Q87. SSH through jump sever using private key in macOS 

ssh -i privatekey.pem -o "ProxyCommand ssh -W %h:%p -i privatekey.pem user@jumpserverhost" user@targetserver

[SSH through jump sever using private key in macOS ](https://superuser.com/questions/1344557/ssh-through-jump-sever-using-private-key-in-macbook)

[PEM, DER, CRT, and CER: X.509 Encodings and Conversions](https://www.ssl.com/guide/pem-der-crt-and-cer-x-509-encodings-and-conversions/)

## Q88. Characteristics of security group rules

[Characteristics of security group rules](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html#:~:text=Characteristics%20of%20security%20group,outbound%20traffic%20is%20allowed)

## Q89. CIDR 0.0.0.0/0

[What is the difference between 0.0.0.0/0 and 0.0.0.0/1?](https://serverfault.com/questions/1100250/what-is-the-difference-between-0-0-0-0-0-and-0-0-0-0-1)

## Q90. kubectl Flags

Single dash(-) means shorthand form of double dash(--) flags

Refer to help of command
`kubectl run --help` or `kubectl run -h`

A hyphen in `all-namespaces` is not a flag mark

```
--all-namespaces
-A
If present, list the requested object(s) across all namespaces. Namespace in current context is ignored even if specified with --namespace
```

## Q91. Reverse Terraform

[Import Terraform Configuration](https://developer.hashicorp.com/terraform/tutorials/state/state-import)

[Terraformer](https://github.com/GoogleCloudPlatform/terraformer)

[TerraCognita](https://github.com/cycloidio/terracognita)

## Q92. AWS Database Migration Service replication subnet group

[Creating a replication subnet group](https://docs.aws.amazon.com/dms/latest/userguide/CHAP_ReplicationInstance.VPC.html#CHAP_ReplicationInstance.VPC.Subnets)

## Q93. Helm

For basic Helm-related guide, refer to the Kubernetes lecture textbook

[15_Helm.md](https://github.com/JungSangup/mspt2/blob/main/doc/%5BBook%5D%2015_Helm.md)

For the basics of deploying Helm charts using EKS, please see the workshop below.

[Amazon EKS Workshop > Beginner > Helm](https://www.eksworkshop.com/beginner/060_helm/)

## Q94. Jump Host

To connect to the admin server

1. Connect to the public IP of the bastion server in the local environment
2. Connect to the admin server private IP from the bastion server

You have to go through a two-step process

I hope you understand that I enter all the admin server and bastion server information in MobaXterm to connect at once

[AWS Bastion Host / Jump Box](https://dev.to/aws-builders/aws-bastion-host-jump-box-5h87)

[SSH connection to EC2 private instance](https://res.cloudinary.com/practicaldev/image/fetch/s--CHSpu-V5--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8cgwqc8m0i9e26be1j9u.png)

## Q95. Argo CD Applications

[Argo CD Applications](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/#applications)

## Q96. Jenkins Pipeline Syntax

[Pipeline Syntax When Built-in Conditions](https://www.jenkins.io/doc/book/pipeline/syntax/#built-in-conditions)


[DNS attributes in your VPC](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-dns.html#vpc-dns-support)

## Q97. Amazon RDS Endpoint naming format

>1.Is there some way to "predict" or otherwise determine what the hexchars will be?
>
>You can't predict it, but once you create at least one instance in a region you will know what it is for your account in that region (and it will be the same for all RDS instances belonging to the same account in that region).

>2.Is there a way to set this?
>
>No. The "hexchars" component is generated internally and is unique to your AWS account in each region (cannot be changed). The "hexchars" will be different for the same account in a different region.

>3.Is the hexchars consistent if the instance ID is consistent?
>
>Yes. You can delete an instance and if you create another with the same name, it will have the same endpoint address as the original instance (for the same AWS account in the same region). Also, if you rename an instance from "myinst1" to "myinst2", the first component is the only that changes and the "hexchars.region.rds.amazonaws.com" remains the same.

[RDS endpoint name format](https://stackoverflow.com/questions/34990104/rds-endpoint-name-format)

## Q98. Amazon EBS CSI driver

>CSI drivers
>* replace the Kubernetes "in-tree" storage drivers that exist in the Kubernetes project source code.
>* work with storage providers, such as Amazon EBS.
>* provide a simplified plugin model that make it easier for storage providers like AWS to release features and maintain support without depending on the Kubernetes release cycle.


[Amazon EKS Kubernetes versions](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html)

[Updating an Amazon EKS cluster Kubernetes version](https://docs.aws.amazon.com/eks/latest/userguide/update-cluster.html)

[Kubernetes CSI Developer Documentation](https://kubernetes-csi.github.io/docs/introduction.html)

[Amazon EBS CSI driver](https://docs.aws.amazon.com/eks/latest/userguide/ebs-csi.html)

[Amazon EBS CSI driver Helm chart](https://github.com/kubernetes-sigs/aws-ebs-csi-driver/tree/master/charts/aws-ebs-csi-driver)

[Amazon EBS CSI migration frequently asked questions](https://docs.aws.amazon.com/eks/latest/userguide/ebs-csi-migration-faq.html)


## Q99. Amazon EKS IAM Roles for Service Accounts

[IAM Roles for Service Accounts](https://eksctl.io/usage/iamserviceaccounts/)