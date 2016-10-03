### Batchly Security Policy

As a “Cloud First” company, we at Batchly take security very seriously and it has always been at the heart of our decisions & workflows from day one.


#### AWS Account Security

Batchly runs within your secure AWS account. It uses IAM Roles and a set of permissions associated with it to access & manage AWS infrastructure. We DO NOT store your AWS Access and Secret keys. 


#### IAM Role and Permissions:

We adhere to AWS recommended best practices for assuming a role within your AWS account.
(Refer: http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_common-scenarios_third-party.htm)

To start using Batchly you are required to create a role that Batchly can assume within your AWS account. We have published an exhaustive list of permissions that Batchly requires to manage your AWS environment in the most cost effective manner. We DO NOT require * (All) permissions and only take fine grained permissions for different AWS services.

The following are the permissions that are required across services:

#### AWS:EC2

```
ec2:CreateSecurityGroup
ec2:CreateSpotDatafeedSubscription
ec2:CancelSpotInstanceRequests 
ec2:CreateTags 
ec2:DeleteTags
ec2:CreateVolume 
ec2:attach* 
ec2:Describe* 
ec2:RequestSpotInstances 
ec2:RunInstances 
ec2:GetConsoleOutput
ec2:AuthorizeSecurityGroup*

**On Resources Created by Batchly**

ec2:StartInstances
ec2:StopInstances
ec2:TerminateInstances
ec2:DeleteVolume		
ec2:DeleteSecurityGroup
```

#### AWS:S3

```
s3:AbortMultipartUpload
s3:Get*
s3:List*
s3:Put*
s3:RestoreObject
s3:CreateBucket
```

#### AWS:SQS

```
sqs:CreateQueue
sqs:GetQueueAttributes
sqs:GetQueueUrl
sqs:ListQueues
sqs:SetQueueAttributes
```

#### AWS:CloudWatch

```
cloudwatch:DescribeAlarmHistory
cloudwatch:DescribeAlarms
cloudwatch:DescribeAlarmsForMetric
cloudwatch:DisableAlarmActions
cloudwatch:EnableAlarmActions
cloudwatch:GetMetricData
cloudwatch:GetMetricStatistics
cloudwatch:ListMetrics
cloudwatch:PutMetricAlarm
cloudwatch:PutMetricData
cloudwatch:SetAlarmState
```

#### AWS:Autoscaling

```
autoscaling:Describe*
autoscaling:AttachLoadBalancers
autoscaling:CreateOrUpdateTags
autoscaling:DetachLoadBalancers
autoscaling:AttachInstances
autoscaling:DetachInstances
autoscaling:SetDesiredCapacity
autoscaling:TerminateInstanceInAutoScalingGroup
autoscaling:UpdateAutoScalingGroup
```

#### AWS:EMR

```
elasticmapreduce:AddTags		
elasticmapreduce:AddJobFlowSteps		
elasticmapreduce:DescribeJobFlows		
elasticmapreduce:DescribeCluster		
elasticmapreduce:DescribeStep			
elasticmapreduce:ListBootstrapActions	
elasticmapreduce:ListClusters		
elasticmapreduce:ListInstanceGroups		
elasticmapreduce:ListInstances		
elasticmapreduce:ListSteps
elasticmapreduce:ModifyInstanceGroups	
elasticmapreduce:RunJobFlow

**On Resources Created by Batchly**

elasticmapreduce:RemoveTags
elasticmapreduce:SetTerminationProtection
elasticmapreduce:SetVisibleToAllUsers	
elasticmapreduce:TerminateJobFlows
```

#### AWS:ElasticBeanstalk

```
elasticbeanstalk:Describe*
elasticbeanstalk:RequestEnvironmentInfo
elasticbeanstalk:RetrieveEnvironmentInfo
elasticbeanstalk:ValidateConfigurationSettings
elasticbeanstalk:RestartAppServer
```

#### Others

```
ecs:Describe*
ecs:List*
ecs:DeregisterContainerInstance
ecs:RegisterTaskDefinition
elasticloadbalancing:ConfigureHealthCheck
elasticloadbalancing:DeregisterInstancesFromLoadBalancer
elasticloadbalancing:Describe*
elasticloadbalancing:RegisterInstancesWithLoadBalancer
iam:ListRoles
iam:ListInstanceProfiles
iam:ListInstanceProfilesForRole
iam:PassRole
sts:AssumeRole
logs:CreateLogGroup
logs:PutRetentionPolicy
```

### Resources Key / Password Management

We have a strict Time-bound key rotation policy for managing resource passwords and keys that are used internally. In practice these are rotated at regular intervals to contain damages due to any extremely rare incident of a data breach.


### Batchly Account Security

As a customer you are provided with your own Batchly account. We provide the following ways for you to interface with Batchly:

- Batchly Console
- Batchly API/SDKs

### Batchly API / SDKs:

Batchly API backend only processes authenticated and signed requests from the user. Batchly uses HMAC-SHA1 authentication. All responses are signed to ensure that the origin of the response is indeed Batchly and no one else. 

Batchly SDKs use APIs internally and take care of signing and authentication for you.

### Batchly Internal Infrastructure

We have a High Availability (HA) setup for our backend infrastructure and hence is tolerant to failures across Availability Zones and Regions.

The Batchly infrastructure works within its own Virtual Private cloud (VPC) and therefore is isolated from the public internet. Access to any resources within the VPC from the public internet is carefully modulated using appropriate Security Groups and Access Control Lists (ACLs).

We have separate Environments (Dev QA and Production) each serving a specific purpose in the product’s Development Life Cycle. Exhaustive testing and Quality assurances are undertaken in the QA environment before any feature is moved live.