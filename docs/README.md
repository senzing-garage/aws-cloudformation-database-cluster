# aws-cloudformation-database-cluster

## Synopsis

`aws-cloudformation-database-cluster` deploys three Senzing database clusters into AWS using a Cloudformation template.

## Overview

The `aws-cloudformation-database-cluster` AWS Cloudformation template creates the following resources:

1. AWS infrastructure
    1. VPC
    1. Subnets
    1. Internet Gateway
    1. Routes
    1. IAM Roles and Policies
    1. Logging
1. AWS services
    1. AWS Relational Data Service (RDS) Aurora Postgres Serverless

The following diagram shows a simplified representation of this deployment.

![Image of architecture](architecture.png)

GitHub repository for
[aws-cloudformation-database-cluster](https://github.com/Senzing/aws-cloudformation-database-cluster).

### Contents

1. [Preamble](#preamble)
    1. [Legend](#legend)
1. [Expectations](#expectations)
1. [Demonstrate using AWS Console](#demonstrate-using-aws-console)
1. [Using deployment](#using-deployment)
1. [Additional topics](#additional-topics)
1. [Parameters](#parameters)
1. [Outputs](#outputs)

## Preamble

At [Senzing](http://senzing.com),
we strive to create GitHub documentation in a
"[don't make me think](https://github.com/Senzing/knowledge-base/blob/master/WHATIS/dont-make-me-think.md)" style.
For the most part, instructions are copy and paste.
Whenever thinking is needed, it's marked with a "thinking" icon :thinking:.
Whenever customization is needed, it's marked with a "pencil" icon :pencil2:.
If the instructions are not clear, please let us know by opening a new
[Documentation issue](https://github.com/Senzing/aws-cloudformation-database-cluster/issues/new?template=documentation_request.md)
describing where we can improve.   Now on with the show...

### Legend

1. :thinking: - A "thinker" icon means that a little extra thinking may be required.
   Perhaps there are some choices to be made.
   Perhaps it's an optional step.
1. :pencil2: - A "pencil" icon means that the instructions may need modification before performing.
1. :warning: - A "warning" icon means that something tricky is happening, so pay attention.

## Expectations

- **Time:** Budget 40 minutes to get the demonstration up-and-running.
- **Background knowledge:** This repository assumes a working knowledge of:
  - [AWS Cloudformation](https://github.com/Senzing/knowledge-base/blob/master/WHATIS/aws-cloudformation.md)

## Demonstrate using AWS Console

### Launch AWS Cloudformation

1. :warning: **Warning:** This Cloudformation deployment will accrue AWS costs.
   With appropriate permissions, the
   [AWS Cost Explorer](https://aws.amazon.com/aws-cost-management/aws-cost-explorer/)
   can help evaluate costs.
1. Visit [AWS Cloudformation with Senzing template](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=senzing-db&templateURL=https://s3.amazonaws.com/public-read-access/aws-cloudformation-database-cluster/cloudformation.yaml)
1. At lower-right, click on "Next" button.
1. In **Specify stack details**
    1. In **Parameters**
        1. In **Security responsibility**
            1. Understand the nature of the security in the deployment.
            1. Once understood, enter "I AGREE".
    1. At lower-right, click "Next" button.
1. In **Configure stack options**
    1. At lower-right, click "Next" button.
1. In **Review senzing-db**
    1. Near the bottom, in **Capabilities**
        1. Check ":ballot_box_with_check: I acknowledge that AWS CloudFormation might create IAM resources."
    1. At lower-right, click "Create stack" button.

## Using deployment

1. By itself, this deployment doesn't do much.
   It is simply the database deployment to be used by subsequent Cloudformations.
1. Example subsequent deployments:
    1. [aws-cloudformation-ecs-senzing-stack-basic](https://github.com/Senzing/aws-cloudformation-ecs-senzing-stack-basic)

## Additional topics

1. [How to set AWS RDS force-scaling-capacity](https://github.com/Senzing/knowledge-base/blob/master/HOWTO/set-aws-rds-force-scaling-capacity.md)
1. [How to migrate an AWS RDS database](https://github.com/Senzing/knowledge-base/blob/master/HOWTO/migrate-aws-rds-database.md)

### Review AWS Cloudformation

The AWS resources created by the
[cloudformation.yaml](https://github.com/Senzing/aws-cloudformation-database-cluster/blob/main/cloudformation.yaml)
template can be see in the [AWS Management Console](https://console.aws.amazon.com).

1. CloudFormation
    1. [Stacks](https://console.aws.amazon.com/cloudformation/home?#/stacks)
1. CloudWatch
    1. [Log groups](https://console.aws.amazon.com/cloudwatch/home?#logsV2:log-groups)
1. Elastic Compute Cloud (EC2)
    1. [Network interfaces](https://console.aws.amazon.com/ec2/v2/home?#NIC)
1. Identity and Access Management (IAM)
    1. [Roles](https://console.aws.amazon.com/iam/home?#/roles)
1. Relational Data Service (RDS)
    1. [Databases](https://console.aws.amazon.com/rds/home?#databases:)
    1. [Parameter groups](https://console.aws.amazon.com/rds/home?#parameter-groups:)
    1. [Subnet groups](https://console.aws.amazon.com/rds/home?#db-subnet-groups-list:)
1. Virtual Private Cloud (VPC)
    1. [Internet gateways](https://console.aws.amazon.com/vpc/home?#igws)
    1. [Network ACLs](https://console.aws.amazon.com/vpc/home?#acls)
    1. [Route Tables](https://console.aws.amazon.com/vpc/home?#RouteTables)
    1. [Security Groups](https://console.aws.amazon.com/vpc/home?#SecurityGroups)
    1. [Subnets](https://console.aws.amazon.com/vpc/home?#subnets)
    1. [VPCs](https://console.aws.amazon.com/vpc/home?#vpcs)

### View results

1. Visit [AWS Cloudformation console](https://console.aws.amazon.com/cloudformation/home).
1. Choose appropriate "Stack name"
1. Choose "Outputs" tab.
    1. [Outputs](#outputs) are described further down this page.

## Parameters

Technical information on AWS Cloudformation parameters can be seen at
[Parameters](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html).

### MultipleDatabases

1. **Synopsis:**
   Choose single database or Senzing database cluster.  For more information see:
   https://senzing.zendesk.com/hc/en-us/articles/360010599254-Scaling-Out-Your-Database-With-Clustering
1. **Required:** Yes
1. **Type:** Choice
1. **Allowed values:**
    1. "Multiple"
    2. "Single"
1. **Default:** Multiple

### SecurityResponsibility

1. **Synopsis:**
   This Cloudformation deploys resources that have no public interface.
   To enable additional security measures for the deployment in your specific environment,
   you'll need to consult with your AWS administrator.
1. **Required:** Yes
1. **Type:** String
1. **Allowed values:**
    1. "I AGREE"
1. **Default:** None

## Outputs

### AccountID

1. **Synopsis:**
   The identifier of the AWS account used to create the cloudformation stack.
1. **Details:**
   FIXME:

### DatabaseHostCore

1. **Synopsis:**
   One of 3 Senzing database clusters that hold the Senzing Model.
1. **Details:**
   See the database cluster having a Name in the form `{StackName}-aurora-senzing-core-cluster` in the
   [AWS RDS Console](https://console.aws.amazon.com/rds/home?#databases:).

### DatabaseHostLibfeat

1. **Synopsis:**
   Two of 3 Senzing database clusters that hold the Senzing Model.
1. **Details:**
   See the database cluster having a Name in the form `{StackName}-aurora-senzing-libfeat-cluster` in the
   [AWS RDS Console](https://console.aws.amazon.com/rds/home?#databases:).

### DatabaseHostRes

1. **Synopsis:**
   Three of 3 Senzing database clusters that hold the Senzing Model.
1. **Details:**
   See the database cluster having a Name in the form `{StackName}-aurora-senzing-res-cluster` in the
   [AWS RDS Console](https://console.aws.amazon.com/rds/home?#databases:).

### DatabaseName

1. **Synopsis:**
   The name of the database.
   It is same name across all 3 database servers.
1. **Details:**
   Usually "G2".

### DatabasePassword

1. **Synopsis:**
   The randomly-generated administrative password for authenticating with the database.

### DatabasePortCore

1. **Synopsis:**
   The port used to access the [DatabaseHostCore](#databasehostcore) database.
1. **Details:**
   See the database cluster having a Name in the form `{StackName}-aurora-senzing-core-cluster` in the
   [AWS RDS Console](https://console.aws.amazon.com/rds/home?#databases:).

### DatabasePortLibfeat

1. **Synopsis:**
   The port used to access the [DatabaseHostLibfeat](#databasehostlibfeat) database.
1. **Details:**
   See the database cluster having a Name in the form `{StackName}-aurora-senzing-libfeat-cluster` in the
   [AWS RDS Console](https://console.aws.amazon.com/rds/home?#databases:)

### DatabasePortRes

1. **Synopsis:**
      The port used to access the [DatabaseHostRes](#databasehostres) database.
1. **Details:**
   See the database cluster having a Name in the form `{StackName}-aurora-senzing-res-cluster` in the
   [AWS RDS Console](https://console.aws.amazon.com/rds/home?#databases:).

### DatabaseUsername

1. **Synopsis:**
   Username to access database in each of the three databases.
1. **Details:**
   More information at [AWS RDS Console](https://console.aws.amazon.com/rds/home).

### Ec2InternetGateway

1. **Synopsis:**
   For use in Cloudformation `AWS::EC2::Route` declarations.
1. **Details:**
   See the route table having a "Name" in the form `{StackName}-ec2-route-table-private` in the
   [AWS VPC Console](https://console.aws.amazon.com/vpc/home?#RouteTables).

### Ec2SecurityGroupInternal

1. **Synopsis:**
   For use in Cloudformation declarations such as `AWS::EC2::SecurityGroupIngress`.
1. **Details:**
   See the security group having a "Name" in the form `{StackName}-ec2-security-group-internal` in the
   [AWS VPC Console](https://console.aws.amazon.com/vpc/home?#SecurityGroups ).

### Ec2Vpc

1. **Synopsis:**
   The AWS Resource ID of the Virtual Private Cloud (VPC).
1. **Details:**
   See the VPC having a "Name" in the form `{StackName}-ec2-vpc` in the
   More information at [AWS VPC Console](https://console.aws.amazon.com/vpc/home?#vpcs:).

### Ec2VpcCidrBlock

1. **Synopsis:**
   For use in Cloudformation `AWS::EC2::SecurityGroup` declarations.
1. **Details:**
   See the "IPV4 CIDR" having a "Name" in the form `{StackName}-ec2-vpc` in the
   [AWS VPC Console](https://console.aws.amazon.com/vpc/home?#vpcs).

### SubnetPrivate1

1. **Synopsis:**
   The first of two private subnets created.
1. **Details:**
   See the subnet having a Name in the form `{StackName}-ec2-subnet-private-1` in the
   [AWS Virtual Private Cloud console](https://console.aws.amazon.com/vpc/home?#subnets:).

### SubnetPrivate2

1. **Synopsis:**
   The second of two private subnets created.
1. **Details:**
   See the subnet having a Name in the form `{StackName}-ec2-subnet-private-2` in the
   [AWS Virtual Private Cloud console](https://console.aws.amazon.com/vpc/home?#subnets:).

### SubnetPublic1

1. **Synopsis:**
   The first of two public subnets created.
1. **Details:**
   See the subnet having a Name in the form `{StackName}-ec2-subnet-public-1` in the
   [AWS Virtual Private Cloud console](https://console.aws.amazon.com/vpc/home?#subnets:).

### SubnetPublic2

1. **Synopsis:**
   The second of two public subnets created.
1. **Details:**
   See the subnet having a Name in the form `{StackName}-ec2-subnet-public-2` in the
   [AWS Virtual Private Cloud console](https://console.aws.amazon.com/vpc/home?#subnets:).
