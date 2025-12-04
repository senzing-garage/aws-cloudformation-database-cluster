# aws-cloudformation-database-cluster

## :no_entry: Deprecated

[![No Maintenance Intended](http://unmaintained.tech/badge.svg)](http://unmaintained.tech/)

Replaced by our new [Senzing Entity Resolution AWS Marketplace offering](https://aws.amazon.com/marketplace/pp/prodview-p3y2bvjkxcipo?sr=0-1&ref_=beagle&applicationId=AWSMPContessa).

If you are beginning your journey with [Senzing],
please start with [Senzing Quick Start guides].

You are in the [Senzing Garage]
where projects are "tinkered" on.
Although this GitHub repository may help you understand an approach to using Senzing,
it's not considered to be "production ready" and is not considered to be part of the Senzing product.
Heck, it may not even be appropriate for your application of Senzing!

## Synopsis

The
`aws-cloudformation-database-cluster`
AWS Cloudformation template creates an AWS VPC
and Aurora Postgres serverless database deployment.
The Cloudformation does not deploy Senzing.
Rather, it deploys a database than can be used by other AWS Cloudformations
which do deploy Senzing such as
[aws-cloudformation-ecs-senzing-stack-basic].

## How to deploy without much thinking

For more details, see [details of deployment].

1. :warning: **Warning:** This Cloudformation deployment will accrue AWS costs.
   With appropriate permissions, the [AWS Cost Explorer] can help evaluate costs.
1. Download the appropriate [AWS Cloudformation template example] from this repository to your local device. Example:

   ```console
   curl -X GET \
       --output ~/cloudformation.yaml \
       https://raw.githubusercontent.com/Senzing/aws-cloudformation-database-cluster/main/cloudformation.yaml
   ```

1. It is highly suggested to take a look at the AWS Cloudformation Template that has been downloaded. This template is an example that deploys and configures a number of services and facilities. While it is a working example, each business may have different requirements and their account may not have all the privileges required to deploy it. Furthermore, the examples change over time and these files are meant to be treated as code files so they should be put under source control.
1. Visit the [AWS Cloudformation home].
1. At the upper-right, click the "Create stack" drop-down and choose "With new resources (standard)".
1. In the "Specify template" area choose the "Upload a template file" radio button.
1. Select the "Choose file" button and choose the AWS Cloudformation template that was downloaded previously.
1. At lower-right, click on "Next" button.
1. In **Specify stack details**
   1. In **Stack name**
      1. Choose a stack name that is unique to you and 21 characters or less. (Several resource types have a limit of 32 character names. The CFT uses the stack name and an 11 character suffix to name resources uniquely.)
   1. In **Parameters**
      1. In **Senzing installation**
         1. If you plan on loading billions of records, choose "Multiple".
         1. Otherwise, choose "Single".
      1. In **Security responsibility**
         1. Understand the nature of the security in the deployment.
         1. Once understood, enter "I AGREE".
   1. At lower-right, click "Next" button.
1. In **Configure stack options**
   1. At lower-right, click "Next" button.
1. In **Review senzing database stack**
   1. Near the bottom, in **Capabilities**
      1. Check ":ballot_box_with_check: I acknowledge that AWS CloudFormation might create IAM resources."
   1. At lower-right, click "Create stack" button.

## Additional topics

1. [Details of deployment]
1. [How to migrate an AWS RDS database]

[aws-cloudformation-ecs-senzing-stack-basic]: https://github.com/senzing-garage/aws-cloudformation-ecs-senzing-stack-basic
[AWS Cloudformation home]: https://console.aws.amazon.com/cloudformation/home
[AWS Cloudformation template example]: https://raw.githubusercontent.com/Senzing/aws-cloudformation-database-cluster/main/cloudformation.yaml
[AWS Cost Explorer]: https://aws.amazon.com/aws-cost-management/aws-cost-explorer/
[details of deployment]: docs/README.md
[How to migrate an AWS RDS database]: https://github.com/senzing-garage/knowledge-base/blob/main/HOWTO/migrate-aws-rds-database.md
[Senzing]: https://senzing.com/
[Senzing Garage]: https://github.com/senzing-garage
[Senzing Quick Start guides]: https://docs.senzing.com/quickstart/
