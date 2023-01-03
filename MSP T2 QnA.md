# Rarely Asked Questions

## Q00. Basic

***Kteyboard shortcuts***
* `Windows Logo` + `Shift` + `S` : Microsoft Windows Screenshot
* `Ctrl` + `Shift` + `S` : Spring Tool Suite Save all files
* `Ctrl`+ `Shift`+ `O` : Spring Tool Suite Oraganize import
* `Ctrl`+ `Shift`+ `R` : Spring Tool Suite Open Search for resources
* `Ctrl` + `Shift`+ `Escape` : Microsoft Windows Task manager
* `Ctrl` + `F5` : Web Browser Hard refresh

* Gradle Tasks 안 보일 경우 STS(Spring Tool Suite) 상단 메뉴 `Windows` > `Show View` > `Other` > (검색) `Gradle Tasks` 선택 후 `Open`
* STS 상단 메뉴 `Windows` > `Show View` > `Package Explorer`

* 현재 진행중인 교재 위치(목차 번호)와 화면 스크린샷
* 슬랙 상단에 `검색` 기능이 있습니다. 유사한 오류인 경우 해결 내용을 참조하는데 유용합니다

## Q01. OpenAPI Specification Reference

* OpenAPI definitions syntax error can be corrected by editor linting
* Reference to OpenAPI Specifications structure

  <https://oai.github.io/Documentation/specification-structure.html>
  <https://swagger.io/specification/#specification>

* Reference to API Server

  <https://oai.github.io/Documentation/specification-servers.html>
  <https://swagger.io/docs/specification/api-host-and-base-path/>

## Q02. OpenAPI Syntax

* OpenAPI definitions can be written in JSON or YAML
* 특별히 명시된 경우 등을 제외하고 문자열 표현시 JSON과 다르게 YAML에서는 인용부호를 필요로 하지 않습니다

## Q03. Terraform Backend

* 테라폼 스테이트 파일의 S3 사용
   <https://www.terraform.io/language/settings/backends/s3>
* 다이나모 테이블 키 이름은 백엔드 설정의 버킷과 키 값을 이용합니다
* 테라폼 사용 시나리오나 구성환경에 따라 다양한 방법이 가능할 것으로 생각되고 백엔드 스테이트 파일 잠금과 더블어 다중 사용자 환경에 대한 고려가 필요할 것 같습니다
* 파일 잠금의 직접적인 용도는 스테이트 파일의 접근 제한이 맞습니다

## Q04. ArgoCD istio app failed to syncing AWS load balancer

  ```msg
  Error syncing load balancer:
  failed to ensure load balancer:
  error creating load balancer: 
  ResourceInUse: 
  The allocation IDs are not available for use
  tstatus code: 400
  ```

1. 아르고 CD(Argo CD)에서 `emarket`, `istio` 앱 삭제
2. AWS콘솔 `EC2>Load Balancers`  액티브(Active) 상태인 네트워크 로드밸런서(Network Load balancer, Type: Network)만 삭제
3. AWS콘솔 `EC2>Target groups` 이스티오(Istio) 관련 target group(K8s-istiosys-...) 삭제
4. 아르고 CD에서 `istio` 앱 생성
5. AWS콘솔 `EC2>Load Balancers` 네트워크 로드밸런서 액티브 상태 확인
6. 아르고 CD에서 `emarket` 앱 생성

* AWS 콘솔 `Certificate Manager > Certificates Key Status`

## Q05. Oracle to PostgreSQL Open Source Migration Tool

<https://www.enterprisedb.com/blog/the-complete-oracle-to-postgresql-migration-guide-tutorial-move-convert-database-oracle-alternative>

<https://github.com/darold/ora2pg>

## Q06. OpenAPI Specification(OAS) Null data type

* OAS 3.0에서 해당 데이터 값이 널(null) 일 수도 있다는 속성을 나타냅니다

    <https://swagger.io/docs/specification/data-models/data-types/#null>

* OAS 3.1에서는 널 데이터 타입이 사용 가능합니다

    <https://spec.openapis.org/oas/v3.1.0.html#data-types>

## Q07. Terraform state lock

* 테라폼 코드가 정상적으로 수행이 완료되면 S3에 저장된 테라폼 스테이트 파일에 대한 MD5 해시 값이 다이나모DB의 terraform-lock 테이블에 s3 오브젝트 키를 파티션 키로 하는 아이템에 저장이 됩니다

  <https://developer.hashicorp.com/terraform/language/settings/backends/s3#protecting-access-to-workspace-state>

## Q08. AWS Database Migration Service (DMS) Logging

* 데이터베이스 마이그레이션 태스크 오류가 발생한 경우 해당 태스크 상세 내역 화면의 `Table statistics` 탭에서 간단한 오류 내역을 확인할 수 있습니다

* 상세한 오류 내역을 확인하기 위해서는 클라우드 워치 로깅을 활성화(Enable) 하고 상세한 로그 내역을 확인할 수 있습니다

  <https://aws.amazon.com/premiumsupport/knowledge-center/dms-task-error-status/>

  <https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Tasks.CustomizingTasks.TaskSettings.Logging.html>

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

* DMS에서는 자체 액션 뿐만 아니라 변환 룰 표현식에 브라이틱스에서도 사용되는 SQLite 스크립트를 지원합니다

  <https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Tasks.CustomizingTasks.TableMapping.SelectionTransformation.Expressions.html#CHAP_Tasks.CustomizingTasks.TableMapping.SelectionTransformation.Expressions-SQLite>

  <https://aws.amazon.com/blogs/database/transform-column-content-and-data-type-using-aws-dms/>

## Q11. Junit Parameterized Tests

* 매개변수 적용 테스트

  <https://junit.org/junit5/docs/current/user-guide/#writing-tests-parameterized-tests>

## Q12. Terraform Syntax

* 테라폼이 JSON(JavaScript Object Notation)으로 표현이 되는 경우에는 엄격하게 큰따옴표(Double Quotes)를 적용해야 하지만 HCL(HashiCorp Configuration Language)의 경우에는 그렇지 않습니다

* 대부분의 예제에서는 관행상 인용부호를 많이 쓰는 것 같습니다

  <https://www.w3schools.com/js/js_json_syntax.asp>

  <https://github.com/hashicorp/hcl/blob/main/hclsyntax/spec.md>

  <https://developer.hashicorp.com/terraform/language/syntax/configuration?optInFrom=terraform-io>

## Q13. Terraform Data sources

* 테라폼 코드에서 외부 또는 다른 테라폼 코드로 정의된 정보를 참조하고자 할 때 데이터 소스를 사용합니다

<https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/instance>

<https://developer.hashicorp.com/terraform/language/data-sources>

## Q14. MariaDB Backtick

* 마리아DB(MariaDB)에서는 일반 오브젝트 식별자와 예약어를 구분하기 위해 억음부호(Backtick, 키보드 숫자 1 왼쪽에 위치)를 사용합니다

* Identifiers may be quoted using the backtick character - `. Quoting is optional for identifiers that don't contain special characters, or for identifiers that are not reserved words

  <https://mariadb.com/kb/en/identifier-names/>

## Q15. utf8 vs. utf-8

* What is the diffrence between UTF-8, UTF8 and AL32UTF8?

>UTF-8 is a variable-width Unicode encoding and also a strict superset of 7-bit ASCII. One Unicode character can be 1 byte, 2 bytes, 3 bytes or 4 bytes in UTF-8.

>UTF8(without the dash) is the name of the Oracle character set introduced in Oracle 8.0 that follows the UTF-8 encoding. UTF8 supports UTF-8 encoding up to Unicode standard 3.0 only. 

>AL32UTF8 is the Oracle Unicode character set that supports the supplementary characters defined in the latest Unicode standard

Oracle unicode

<https://www.oracle.com/technetwork/products/globalization/twp-appdev-unicode-10gr2-129234.pdf>

<https://docs.oracle.com/en/database/oracle/oracle-database/18/nlspg/appendix-A-locale-data.html#GUID-A9E30C27-FD47-4552-B670-F41A95B11405>

## Q16. rds_superuser role

* `rdsadmin`은 자동 생성되는 사용자(역할) 중 하나로 아마존 RDS 내부적인 관리 용도로 사용

  <https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Appendix.PostgreSQL.CommonDBATasks.Roles.html#Appendix.PostgreSQL.CommonDBATasks.Roles.rds_superuser>

## Q17. PostgreSQL Timestamp

<https://www.postgresql.org/docs/current/datatype-datetime.html>

## Q18. Convention over Configuration

* src/main src/test directory structure origin

<https://en.wikipedia.org/wiki/Convention_over_configuration>

<https://books.sonatype.com/mvnref-book/reference/installation-sect-conventionConfiguration.html>

<https://docs.gradle.org/current/userguide/designing_gradle_plugins.html#convention_over_configuration>

## Q19. Ubuntu 22 version

* which services should be restarted

  <https://discourse.ubuntu.com/t/needrestart-for-servers/21552/1>

* 업데이트를 위해서 해당 백그라운드로 실행되고 있는 서비스를 재시작 하겠느냐는 내용입니다. 운영 환경에서는 확인이 필요하지만 교육 과정 중에는 해당 사항이 없습니다
모든 서비스 선택하고 확인하면 됩니다

  <https://phoenixnap.com/kb/fix-could-not-get-lock-error-ubuntu>

* Signature not yet current

  <https://zhang-yang.medium.com/solving-signature-not-yet-current-error-when-using-aws-in-docker-c2d8ba314a7e>

## Q20. ECR Creation error by time sync failure

* VM 시간이 서버 시간과 5분 이상 차이가 나는 경우 발생하는 오류로 VM의 시간을 재설정하시기 바랍니다
* The system clock of the container is off Amazon’s clock by more than 5 minutes, the maximum allowed by Amazon’s signature algorithm

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

해당 데이터베이스 메뉴에서

  `RDS > Databases > targetdb(-maria)`

연결이 필요한 VM을 선택해서 설정

  `Actions > Set up EC2 connection`

## Q25. AWS SCT Alert(Red exclamation) mark

* Items with a red exclamation mark next to them cannot be directly translated from the source to the target
* Right click on the schema in the left-hand panel, and click Create report

## Q26. AWS UX

1. 좌측 상단 AWS 로고 (Console Home)
2. 우측 상단 [Actions] - [Revert to previous Console Home]

## Q27. Usage of Java Interface on a service layer

* 서비스 레이어에서 인터페이스를 활용하는 이유
* Mock을 사용하기 위한 용도

<https://docs.oracle.com/javase/tutorial/java/concepts/inheritance.html>

<https://stackoverflow.com/questions/28693175/use-of-interfaces-on-a-service-layer>

<https://stackoverflow.com/questions/11528061/i-want-to-define-a-spring-bean-class-with-no-interface>

## Q28. Spring Boot Database Initialization Using Basic SQL Scripts

<https://docs.spring.io/spring-boot/docs/current/reference/html/howto.html#howto.data-initialization.using-basic-sql-scripts>

## Q29. OpenAPI PUT vs. PATCH

Use of PUT vs PATCH methods in REST API real life scenarios

<https://stackoverflow.com/questions/28459418/use-of-put-vs-patch-methods-in-rest-api-real-life-scenarios>

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

* 일반적인 최소 권한의 원칙을 감안하면 필요한 정보 외에 범위를 지정하는 것은 적합하지 않은 것으로 생각됩니다
패스워드 대신에 토큰을 쓰는 이유도 같이 생각해 보아야 하겠습니다
* 깃허브 API에 접근하는 용도라면 새롭게 만들어진 세분화된 PAT를 사용하는게 좋겠습니다

## Q34. Git Ignore

<https://git-scm.com/docs/gitignore>

<https://github.com/github/gitignore#a-collection-of-gitignore-templates>

## Q35. JWT Signature

<https://auth0.com/blog/json-web-token-signing-algorithms-overview/>

<https://www.freecodecamp.org/news/how-to-sign-and-validate-json-web-tokens/>

<https://stackoverflow.com/questions/61624189/why-include-header-and-payload-in-jwt-token>

## Q36. Git vs. SVN

>기술적인 측면도 중요하겠지만 깃이 가지고 있는 자유와 개방성이라는 사상이 회사의 보안 기준과 상충되는 부분을 어떻게 조화시킬 수 있는지에 대한 방안이 없다면 깃을 도입해서 얻을 수 있는 것은 일부 기능 개선에 그치지 않을까 생각됩니다

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

<https://www.jenkins.io/doc/book/system-administration/viewing-logs/>

<https://docs.gradle.org/current/userguide/logging.html>

<https://git-scm.com/docs/git-log>

## Q41. VPC Network Analyze

라우트 테이블의 역할이 서브넷, 인터넷게이트웨이 등이 서로 네트워크 트래픽을 주고 받을 수 있는 경로의 설정 값을 가지고 있는 자원입니다

경로가 실제로 정상적으로 설정되어 있는지 간단하게 확인하시려는 거라면 커맨드 라인 방식의 네트워크 유틸리티를 이용하거나 AWS에서 제공하는 네트워크 애널라이저 등 서비스를 활용하는 방법이 있습니다

`VPC > Reachability Analyzer`

<https://docs.aws.amazon.com/vpc/latest/reachability/what-is-reachability-analyzer.html>

## Q42. User data and cloud-init

* utilize user data to automatically run a script with every restart of Amazon EC2 Linux instance

<https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html#user-data-cloud-init>

<https://cloudinit.readthedocs.io/en/latest/index.html>

<https://help.ubuntu.com/community/CloudInit>

## Q43. Terraform Plan

* Plan 단계가 단독 사용자 환경에서 수작업으로 실습 진행하는 경우에는 별다른 의미를 찾기 어렵겠지만
* 다중 사용자 환경에서 깃옵스(GitOps) 등을 통한 자동화 프로세스를 적용시에는 워크플로우 관점에서 유용한 단계
  <https://developer.hashicorp.com/terraform/tutorials/automation/automate-terraform>

## Q44. Terraform error on a specific AWS EC2 Instance Type

```text
 Unsupported: The requested configuration is currently not supported.
 Please check the documentation for supported configurations
```

<https://docs.aws.amazon.com/autoscaling/ec2/userguide/ts-as-instancelaunchfailure.html#ts-as-instancelaunchfailure-3>

## Q45. Terraform Variable Definition Precedence

<https://developer.hashicorp.com/terraform/language/values/variables#variable-definition-precedence>

## Q46. Terraform Variable Definition

* 관행상 또는 기준 및 절차서에 명시된 경우가 아니라면 입력 변수 정의를 위한 변수 블록(Variable block)은 모든 테라폼 코드에 존재할 수 있습니다
* 변수 정의 파일(.tfvars)은 변수명과 할당값으로 구성되어 코드실행시에 지정하거나 자동으로 불러오도록 구성할 수 있습니다

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

1. 차일드 모듈(Child Module)에서만 필요한 경우 로컬(Local values, Locals)을 사용할 수 있습니다
    <https://developer.hashicorp.com/terraform/language/values/locals>

    조건에 따라서 다른 값이 필요한 경우
    <https://stackoverflow.com/questions/60084611/how-best-to-handle-multiple-tfvars-files-that-use-common-tf-files>

2. 차일드 모듈의 아웃풋(Outputs) 값은  module.<MODULE NAME>.<OUTPUT NAME> 형태로 사용
    <https://developer.hashicorp.com/terraform/language/values/outputs#accessing-child-module-outputs>


## Q50. Domain Name Service

1. route 53 > domain > hosted zone 도메인 정보와 eks-values.yaml 일치 여부 확인
2. route 53 > domain > hosted zone 도메인 정보 로드밸런서 매핑여부 확인 및 필요시 수정

## Q51. Helm Chart 반영

1. 헬름 차트(Helm Chart) eks-values.yaml 파일 수정
2. 교재 2-1-5,  2-1-6 수행하여 깃(Git) 리포지터리(Repository) 반영
3. 아르고CD(Argo CD)에서 이마켓 앱 동기화(Synchronize)

## Q52. Istio path

```text
v1/Service
istio-system
istio-ingressgateway
 SyncFailed
error validating data: [unknown object type "nil" in Service.metadata.annotations.service.beta.kubernetes.io/aws-load-balancer-eip-allocations, unknown object type "nil" in Service.metadata.annotations.service.beta.kubernetes.io/aws-load-balancer-ssl-cert]
```

* 경로(path)를 잘못 설정한 경우 발생
* 경로는 istio를 키인(Key in)하는 입력이 아니라 istio로 검색하여 조회되는 항목을 선택

## Q53. Argo CD app delete

>Argo CD app delete Propagation policy
>
>* Specify propagation policy for deletion of application's resources

### Foreground cascading deletion

* Enters a deletion in progress state
* After deleting all the dependent objects, the controller deletes the owner object
### background cascading deletion

* deletes the owner object immediately  
* controller cleans up the dependent objects in the background

[Kubernetes Cluster Garbage Collection Cascading deletion](https://kubernetes.io/docs/concepts/architecture/garbage-collection/#cascading-deletion)

[Change default deletion propagation policy from foreground to background #5724
](https://github.com/argoproj/argo-cd/issues/5724)

## Q54. MinIO

* 민아이오(MinIO)는 멀티클라우드 오브젝트 스토리지 솔루션으로 이마켓앱에서 이미지 리소스를 저장하는데 사용되고 있습니다
    <https://min.io/docs/minio/kubernetes/upstream/>

* 사이트 접속이 잘 되더라도 이미지가 보이지 않는다면 재설정이 필요할 수 있습니다

* 이미지 등록 배치 작업이 끝나면 다른 파드와 달리 `실행(Running)` 상태로 서비스를 제공하지 않고 `완료(Completed)` 처리됩니다

## Q55. Amazon VPC Subnet sizing

[CIDR Block Calculator](https://cidr.xyz)

<https://docs.aws.amazon.com/vpc/latest/userguide/configure-subnets.html#subnet-sizing>

<https://stackoverflow.com/questions/55320836/how-to-calculate-total-ips-of-a-subnet-in-aws>

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

아래 3개 SQL 문장에 세미콜론이 누락되어 발생하는 오류입니다
코멘트 내용이 추가되지 않아도 실습에는 영향이 없습니다

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

SQL디벨로퍼(Developer)에서 `쿼리 결과(Query Result, Ctrl + Enter)`는 SQL 문장에 대한 수행 결과를 보여주는 내용으로 여러개의 SQL 문장을 순서대로 수행하는 `스크립트 아웃풋(Script Output, F5)`을 보여주는 화면과는 차이가 있습니다

[Script Output and Query Result](https://community.oracle.com/tech/developers/discussion/2201870/whats-the-difference-between-script-output-and-query-result)

스크립트 아웃풋에 대한 인코딩 설정은 아래 메뉴에서 확인해 보시기 바랍니다

`Tools - Preferences - Environment - Encoding`

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

* DMS는 일회성 전환이 아닌 지속적인 데이터 연동 등을 위한 사용도 가능
  
  <https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Task.CDC.html>

## Q63. MariaDB character set and collation

```sql
SELECT * FROM INFORMATION_SCHEMA.SCHEMATA;
```

<https://mariadb.com/kb/en/setting-character-sets-and-collations/#database-level>

## Q64. MarkDown Viewer Dark mode

마크다운 뷰어 업데이트 후에 윈도우즈 다크모드에서 HTML 태그 관련 오류 발생시

* 윈도우즈 다크모드 해제 , 
* 마크다운 뷰어 테마 변경 또는 
* VS코드 와 같은 다른 마크다운 뷰어 사용

## Q65. AWS DMS Selection rules and actions priority

### Load-order
* The priority for loading tables and views. Tables and views with higher values are loaded first
* A positive integer. The maximum value is 2,147,483,647

## Q66. Troubleshoot connecting AWS EC2 Linux instance

<https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/TroubleshootingInstancesConnecting.html>

## Q67. AWS Regions

* 서비스 사용료 및 부하를 고려하여 반별로 리전을 구분하여 운영
* 리전별로 제공되는 서비스는 차이가 있으며 네트워크 지연시간에도 차이가 있음
  
[AWS Regional Services List](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/?nc1=h_ls)

[AWS Latency Monitoring](https://www.cloudping.co/grid)

[AWS Connection Health Check](https://clients.amazonworkspaces.com/Health.html)

[What to Consider when Selecting a Region for your Workloads](https://aws.amazon.com/blogs/architecture/what-to-consider-when-selecting-a-region-for-your-workloads/)

[How to select a Region for your workload based on sustainability goals](https://aws.amazon.com/blogs/architecture/how-to-select-a-region-for-your-workload-based-on-sustainability-goals/)

## Q68. Windows Logo

윈도우 물결무늬 로고의 사용은 2012년 8월 23일에 종료되었습니다

[Microsoft Unveils a New Look](https://blogs.microsoft.com/blog/2012/08/23/microsoft-unveils-a-new-look/)

[Microsoft Windows Logo Variants](https://logos.fandom.com/wiki/Microsoft_Windows)

## Q69. Amazon EC2 Instance Connect

클라우드쉘 또는 클라우드IDE와 동일하게 아마존 EC2 인스턴스 커넥트도 사용자 로컬 클라이언트가 직접 접속하는 것이 아니라 해당 서비스의 엔드포인트를 거쳐서 접속하게 되므로 접속하고자 하는 서비스의 시큐리티 그룹에는 해당 서비스의 CIDR가 등록되어 있어야 합니다

<https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-connect-set-up.html>

<https://aws.amazon.com/blogs/security/use-ec2-instance-connect-to-provide-secure-ssh-access-to-ec2-instances-with-private-ip-addresses/>

