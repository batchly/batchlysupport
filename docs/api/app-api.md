### App Specific APIs

Batchly works through Apps. There are marketplace apps such as FFMpeg for video transcoding, and JMeter for load testing. You may also upload your own private app to run in your Batchly account.

Nevertheless, each app has its own set of APIs to perform the basic operations. The request headers, however, differ based on the app you want to create.

**Common Actions Supported By All Apps**

HTTP Method | Endpoint | Description
--|--|--
POST | api/apps/{APP_NAME}/{id}/Execute | Execute the job
POST | api/apps/{APP_NAME}/Add | Create a new job
PUT | api/apps/{APP_NAME}/{id} | Edit a job with updated information. 
GET | api/apps/{APP_NAME}/{id} | Get details for a job
DELETE | api/apps/{APP_NAME}/{id} | Delete a job
GET | api/apps/{APP_NAME}/jobs | Lists all jobs

#### App Specific Request headers 

---

#### Auto Scaling Group App

APP_NAME : Auto Scaling Group 

**Request Header**

```
{
  "Name": "Auto Scaling Job",
  "AutoScalingGroupName": "SPECIFY_NAME",
  "MinOnDemandInstanceCount": 0,
  "MaxInstanceCount": 0,
  "DesiredInstanceCount": 0,
  "RestrictToSelectedInstance": true,
  "HealthCheckGracePeriod": 0,
  "AccountId": "A-XXXXX",
  "BaseRegion": "string",
  "VpcId": "vpc-XXXXX",
  "SubnetIds": [
    "subnet-XXXXX"
  ]
}
```


Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
AutoScalingGroupName | String | Specify Autoscaling group associated to the account | Yes
MaxInstanceCount | Integer | Maximum number of instances to be launched| Yes
DesiredInstanceCount | Integer | Desired number of instances to be launched | Yes
MinInstanceCount | Integer | Minimum number of instances to be launched | Yes
RestrictToSelectedInstance | Boolean | Restrict not to choose instances other than selected | No
HealthCheckGracePeriod | Integer | Provide the health check grace period (in seconds) | No
AccountId | String | Identifier of the Account under which the job should execute | Yes
BaseRegion | String | AWS region where your job will run |Yes
VpcId | String | Vpc Id where the job should execute | Yes
SubnetIds | String | Specify the Subnet Ids under selected Vpc | Yes


**Success Response**

```
{
  "RequestId": "string",
  "Data": {
    "Runs": 0,
    "IsScheduled": true,
    "IsExecuting": true,
    "Engine": "Cluster",
    "AppName": "Auto Scaling Group",
    "IsPrivateApp": true,
    "Id": "W-XXXXX",
    "Name": "JOB_NAME"
    }
}
```

---

#### Elastic Load Balancer App

APP_NAME : Elastic Load Balancer

**Request Header**

```
{
  "Name": "Elastic Load Balancer Job",
  "MaxInstanceCount": 0,
  "DesiredInstanceCount": 0,
  "MinOnDemandInstanceCount": 0,
  "ElasticLoadBalancerName": "SPECIFY_NAME",
  "LaunchScript": "SPECIFY_LAUNCH_SCRIPT",
  "AmiId": "ami-XXXXX",
  "InstanceType": "c4.large",
  "RestrictToSelectedInstance": true,
  "SecurityGroupId": "sg-XXXXX",
  "HealthCheckGracePeriod": 0,
  "InstanceProfileArn": "SPECIFY_PROFILE_ARN",
  "KeyPair": "SPECIFY_KEY_PAIR",
  "ScalingRules": [
    {
      "MetricName": "SPECIFY_METRIC_NAME",
      "Namespace": "SPECIFY_NAMESPACE",
      "ScaleAt": 0,
      "ScaleFactor": 0,
      "EvaluationPeriods": 0,
      "Period": 0,
      "MetricStatisticType": "CPUUtilization",
      "ScaleType": "Average",
      "Unit": "Percent",
      "Dimensions": "{key}:{value}"
    }
  ],
  "AccountId": "A-XXXXX",
  "BaseRegion": "us-east-1",
  "VpcId": "vpc-XXXXX",
  "SubnetIds": [
    "subnet-XXXXX"
  ]
}
```


Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
MaxInstanceCount | Integer | Maximum number of instances to be launched| Yes
DesiredInstanceCount | Integer | Desired number of instances to be launched | Yes
MinInstanceCount | Integer | Minimum number of instances to be launched | Yes
ElasticLoadBalancerName | String | Specify the Elastic Load Balancer Name | Yes
LaunchScript | String | Provide the script to be launched | No
AmiId | String | Specify the Ami Id | Yes
InstanceType | String | The instance type to be launched | Yes
RestrictToSelectedInstance | Boolean | Restrict not to choose instances other than selected | No
SecurityGroupId | String | Specify the security group | Yes
HealthCheckGracePeriod | Integer | Provide the health check grace period (in seconds) | No
InstanceProfileArn | String | Provide the instance profile Arn | Yes
ScalingRules | String | Specify the Scaling Rules | No
KeyPair | String | Specify the key pair | Yes
MetricName | String | Provide desired metric name | Yes
Namespace | String | Provide namespace | Yes
ScaleAt | Integer | Number of Instances to be scaled at | Yes
ScaleFactor | Integer | Number of Instances to be scaled | Yes
EvaluationPeriods | Integer | Number of cycle | Yes
Period | Integer | Specify the time period | Yes
MetricStatisticType |  | Specify the type of metric | Yes
ScaleType |  | Specify the type of scaling | Yes
Unit |  | Specify the unit type | Yes
Dimensions | String | Provide the deminesions in the given format - {Key} : {Value} | Yes
AccountId | String | Identifier of the Account under which the job should execute | Yes
BaseRegion | String | AWS region where your job will run |Yes
VpcId | String | Vpc Id where the job should execute | Yes
SubnetIds | String | Specify the Subnet Ids under selected Vpc | Yes


**Success Response**

```
{
  "RequestId": "string",
  "Data": {
    "Runs": 0,
    "IsScheduled": true,
    "IsExecuting": true,
    "Engine": "Cluster",
    "AppName": "Elastic Load Balancer",
    "IsPrivateApp": true,
    "Id": "W-XXXXX",
    "Name": "JOB_NAME"
  }
```

---

#### AMI App

APP_NAME : AMI

**Request Header**

```
{
  "Name": "AMI Job",
  "MaxInstanceCount": 0,
  "DesiredInstanceCount": 0,
  "MinOnDemandInstanceCount": 0,
  "ElasticLoadBalancerName": "SPECIFY_NAME",
  "LaunchScript": "SPECIFY_LAUNCH_SCRIPT",
  "AmiId": "ami-XXXXX",
  "InstanceType": "c4.large",
  "RestrictToSelectedInstance": true,
  "SecurityGroupId": "sg-XXXXX",
  "HealthCheckGracePeriod": 0,
  "InstanceProfileArn": "SPECIFY_PROFILE_ARN",
  "KeyPair": "SPECIFY_KEY_PAIR",
  "ScalingRules": [
    {
      "MetricName": "SPECIFY_METRIC_NAME",
      "Namespace": "SPECIFY_NAMESPACE",
      "ScaleAt": 0,
      "ScaleFactor": 0,
      "EvaluationPeriods": 0,
      "Period": 0,
      "MetricStatisticType": "CPUUtilization",
      "ScaleType": "Average",
      "Unit": "Percent",
      "Dimensions": "{key}:{value}"
    }
  ],
  "AccountId": "A-XXXXX",
  "BaseRegion": "us-east-1",
  "VpcId": "vpc-XXXXX",
  "SubnetIds": [
    "subnet-XXXXX"
  ]
}
```


Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
MaxInstanceCount | Integer | Maximum number of instances to be launched| Yes
DesiredInstanceCount | Integer | Desired number of instances to be launched | Yes
MinInstanceCount | Integer | Minimum number of instances to be launched | Yes
ElasticLoadBalancerName | String | Specify the Elastic Load Balancer Name | Yes
LaunchScript | String | Provide the script to be launched | No
AmiId | String | Specify the Ami Id | Yes
InstanceType | String | The instance type to be launched | Yes
RestrictToSelectedInstance | Boolean | Restrict not to choose instances other than selected | No
SecurityGroupId | String | Specify the security group | Yes
HealthCheckGracePeriod | Integer | Provide the health check grace period (in seconds) | No
InstanceProfileArn | String | Provide the instance profile Arn | Yes
ScalingRules | String | Specify the Scaling Rules | No
KeyPair | String | Specify the key pair | Yes
MetricName | String | Provide desired metric name | Yes
Namespace | String | Provide namespace | Yes
ScaleAt | Integer | Number of Instances to be scaled at | Yes
ScaleFactor | Integer | Number of Instances to be scaled | Yes
EvaluationPeriods | Integer | Number of cycle | Yes
Period | Integer | Specify the time period | Yes
MetricStatisticType |  | Specify the type of metric | Yes
ScaleType |  | Specify the type of scaling | Yes
Unit |  | Specify the unit type | Yes
Dimensions | String | Provide the deminesions in the given format - {Key} : {Value} | Yes
AccountId | String | Identifier of the Account under which the job should execute | Yes
BaseRegion | String | AWS region where your job will run |Yes
VpcId | String | Vpc Id where the job should execute | Yes
SubnetIds | String | Specify the Subnet Ids under selected Vpc | Yes


**Success Response**

```
{
  "RequestId": "string",
  "Data": {
    "Runs": 0,
    "IsScheduled": true,
    "IsExecuting": true,
    "Engine": "Cluster",
    "AppName": "AMI",
    "IsPrivateApp": true,
    "Id": "W-XXXXX",
    "Name": "JOB_NAME"
  }
```

---

#### ElasticBeanstalk App

APP_NAME : ElasticBeanstalk

**Request Header**

```
{
  "Name": "ElasticBeanstalk Job",
  "EnvironmentId": "SPECIFY_ENVIRONMENT_NAME",
  "MinOnDemandInstanceCount": 0,
  "MaxInstanceCount": 0,
  "DesiredInstanceCount": 0,
  "RestrictToSelectedInstance": true,
  "HealthCheckGracePeriod": 0,
  "AccountId": "A-XXXXX",
  "BaseRegion": "us-east-1",
  "VpcId": "vpc-XXXXX",
  "SubnetIds": [
    "subnet-XXXXX"
  ]
}
```


Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
EnvironmentId | String | Specify the Beanstalk environment | Yes
MaxInstanceCount | Integer | Maximum number of instances to be launched| Yes
DesiredInstanceCount | Integer | Desired number of instances to be launched | Yes
MinInstanceCount | Integer | Minimum number of instances to be launched | Yes
RestrictToSelectedInstance | Boolean |  Restrict not to choose instances other than selected | No
HealthCheckGracePeriod | Integer | Provide the health check grace period (in seconds) | No
AccountId | String | Identifier of the Account under which the job should execute | Yes
BaseRegion | String | AWS region where your job will run |Yes
VpcId | String | Vpc Id where the job should execute | Yes
SubnetIds | String | Specify the Subnet Id under selected Vpc | Yes


**Success Response**

```
{
  "RequestId": "string",
  "Data": {
    "Runs": 0,
    "IsScheduled": true,
    "IsExecuting": true,
    "Engine": "Cluster",
    "AppName": "ElasticBeanstalk",
    "IsPrivateApp": true,
    "Id": "W-XXXXX",
    "Name": "JOB_NAME"
  }
```

---

#### Spark App

APP_NAME : Spark

**Request Header**

```
{
  "Name": "Spark Job",
  "ClusterId": "j-XXXXX",
  "DeployMode": "Cluster",
  "SparkSubmitOptions": "opt1 opt2 opt3",
  "ApplicationLocation": "s3://BUCKET_NAME/PATH_TO_SPARK_JAR",
  "ActionOnFailure": "CONTINUE",
  "Arguments": "arg1 arg2 arg3",
  "InstanceTypes": [
    "c4.large", "m3.large"
  ],
  "AccountId": "A-XXXXX",
  "BaseRegion": "us-east-1",
  "VpcId": "vpc-XXXXX",
  "SubnetIds": [
    "subnet-XXXXX"
  ]
}
```


Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
ClusterId | String | Cluster Id where the job should execute | Yes
DeployMode | Integer | 1 (for Cluster mode), 2 (for Client mode) | Yes 
SparkSubmitOptions | String | Specify other options for spark-submit | No
ApplicationLocation | String | S3 location where the Spark jar resides | Yes
ActionOnFailure | String | CONTINUE, CANCEL_AND_WAIT, TERMINATE_CLUSTER | Yes
Arguments | String | Any arguments that the script requires | No
InstanceTypes | String | The instance types to be launched | Yes
AccountId | String | Identifier of the Account under which the job should execute | Yes
BaseRegion | String | AWS region where your job will run |Yes
VpcId | String | Vpc Id where the job should execute | Yes
SubnetIds | String | Specify the Subnet Id under selected Vpc | Yes


**Success Response**

```
{
   Id: "W-XXXXX",
   Name: "Spark Job",
   Runs: 1,
   IsScheduled: "False",
   IsExecuting: "True | False",
   Engine: "MapReduce"
}   
```

---

#### HadoopStreaming App

APP_NAME: HadoopStreaming

**Request Header**

```
{
  "Name": "HadoopStreaming Job",
  "ClusterId": "j-XXXXX",
  "MapperLocation": "s3://BUCKET_NAME/PATH_TO_MAP_FUNCTION",
  "ReducerLocation": "s3://BUCKET_NAME/PATH_TO_REDUCE_FUNCTION",
  "InputLocation": "s3://BUCKET_NAME/PATH_TO_DATASET",
  "OutputLocation": "s3://BUCKET_NAME/PATH_TO_OUTPUT_LOCATION",
  "Arguments": "arg1 arg2 arg3",
  "ActionOnFailure": "CONTINUE",
  "InstanceTypes": [
    "c4.large", "m3.large"
  ],
  "AccountId": "A-XXXXX",
  "BaseRegion": "us-east-1",
  "VpcId": "vpc-XXXX",
  "SubnetIds": [
    "subnet-XXXXX"
  ]
}
```


Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
ClusterId | String | Cluster Id where the job should execute | Yes
MapperLocation | String | S3 location of the map function or the name of the Hadoop streaming command to run | Yes
ReducerLocation | String | S3 location of the reduce function or the name of the Hadoop streaming command to run | Yes
InputLocation | String | S3 location where the dataset resides | Yes
OutputLocation | String | S3 location where the results are written | Yes
Arguments | String | Any arguments that the script requires | No
ActionOnFailure | String | CONTINUE, CANCEL_AND_WAIT, TERMINATE_CLUSTER | Yes
InstanceTypes | String | The instance types to be launched | Yes
AccountId | String | Identifier of the Account under which the job should execute | Yes
BaseRegion | String | AWS region where your job will run |Yes
VpcId | String | Vpc Id where the job should execute | Yes
SubnetIds | String | Specify the Subnet Id under selected Vpc | Yes

**Success Response**

```
{
   Id: "W-XXXXX",
   Name: "HadoopStreaming Job",
   Runs: 1,
   IsScheduled: "False",
   IsExecuting: "True | False",
   Engine: "MapReduce"
}   
```
---

#### Hadoop App

APP_NAME: Hadoop

**Request Header**

```
{
  "Name": "Hadoop Job",
  "ClusterId": "j-XXXXX",
  "JarLocation": "s3://BUCKET_NAME/PATH_TO_JAR",
  "Arguments": "arg1 arg2 arg3",
  "ActionOnFailure": "CONTINUE",
  "InstanceTypes": [
    "c4.large", "m3.large"
  ],
  "AccountId": "A-XXXXX",
  "BaseRegion": "us-east-1",
  "VpcId": "vpc-XXXX",
  "SubnetIds": [
    "subnet-XXXXX"
  ]
}
```


Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
ClusterId | String | Cluster Id where the job should execute | Yes
JarLocation | String | A path into S3 or a fully qualified java class in the classpath | Yes
Arguments | String | Any arguments that the script requires | No
ActionOnFailure | String | CONTINUE, CANCEL_AND_WAIT, TERMINATE_CLUSTER | Yes
InstanceTypes | String | The instance types to be launched | Yes
AccountId | String | Identifier of the Account under which the job should execute | Yes
BaseRegion | String | AWS region where your job will run |Yes
VpcId | String | Vpc Id where the job should execute | Yes
SubnetIds | String | Specify the Subnet Id under selected Vpc | Yes


**Success Response**

```
{
   Id: "W-XXXXX",
   Name: "Hadoop Job",
   Runs: 1,
   IsScheduled: "False",
   IsExecuting: "True | False",
   Engine: "MapReduce"
}   
```

---

#### Hive App

APP_NAME: Hive

**Request Header**

```
{
  "Name": "Hive Job",
  "ClusterId": "j-XXXXX",
  "ScriptLocation": "s3://BUCKET_NAME/PATH_TO_SCRIPT",
  "InputLocation": "s3://BUCKET_NAME/PATH_TO_DATASET",
  "OutputLocation": "s3://BUCKET_NAME/PATH_TO_OUTPUT_LOCATION",
  "Arguments": "arg1 arg2 arg3",
  "ActionOnFailure": "CONTINUE",
  "InstanceTypes": ["c4.large", "m3.large"],
  "AccountId": "A-XXXXX",
  "BaseRegion": "us-east-1",
  "VpcId": "vpc-XXXX",
  "SubnetIds": [
    "subnet-XXXXX"
  ]
}   
```

Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
ClusterId | String | Cluster Id where the job should execute | Yes
ScriptLocation | String | S3 location where the script resides | Yes
InputLocation | String | S3 location where the dataset resides | No
OutputLocation | String | S3 location where results are written | No
Arguments | String | Any arguments that the script requires | No
ActionOnFailure | String | CONTINUE, CANCEL_AND_WAIT, TERMINATE_CLUSTER | Yes
InstanceTypes | String | The instance types to be launched | Yes
AccountId | String | Identifier of the Account under which the job should execute | Yes
BaseRegion | String | AWS region where your job will run |Yes
VpcId | String | Vpc Id where the job should execute | Yes
SubnetIds | String | Specify the Subnet Id under selected Vpc | Yes


**Success Response**

```
{
   Id: "W-XXXXX",
   Name: "Hive Job",
   Runs: 1,
   IsScheduled: "False",
   IsExecuting: "True | False",
   Engine: "MapReduce"
}   
```

---

#### Pig App

APP_NAME: PIG

**Request Header**

```
{
  "Name": "Pig Job",
  "ClusterId": "j-XXXXX",
  "ScriptLocation": "s3://BUCKET_NAME/PATH_TO_SCRIPT",
  "InputLocation": "s3://BUCKET_NAME/PATH_TO_DATASET",
  "OutputLocation": "s3://BUCKET_NAME/PATH_TO_OUTPUT_LOCATION",
  "Arguments": "arg1 arg2 arg3",
  "ActionOnFailure": "CONTINUE",
  "InstanceTypes": ["c4.large", "m3.large"],
  "AccountId": "A-XXXXX",
  "BaseRegion": "us-east-1",
  "VpcId": "vpc-XXXX",
  "SubnetIds": [
    "subnet-XXXXX"
  ]
} 
```

Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
ClusterId | String | Cluster Id where the job should execute | Yes
ScriptLocation | String | S3 location where the script resides | Yes
InputLocation | String | S3 location where the dataset resides | No
OutputLocation | String | S3 location where results are written | No
Arguments | String | Any arguments that the script requires | No
ActionOnFailure | String | CONTINUE, CANCEL_AND_WAIT, TERMINATE_CLUSTER | Yes
InstanceTypes | String | The instance types to be launched | Yes
AccountId | String | Identifier of the Account under which the job should execute | Yes
BaseRegion | String | AWS region where your job will run |Yes
VpcId | String | Vpc Id where the job should execute | Yes
SubnetIds | String | Specify the Subnet Id under selected Vpc | Yes


**Success Response**

```
{
   Id: "W-XXXXX",
   Name: "Pig Job",
   Runs: 1,
   IsScheduled: "False",
   IsExecuting: "True | False",
   Engine: "MapReduce"
}   
```

---

#### JMeter - Load Testing App

APP_NAME: JMeter

**Request Header**

```
{
  "Name": "Jmeter Job",
  "OutputLocation": "s3://BUCKET_NAME/PATH_TO_OUTPUT_LOCATION",
  "TestPlan": "Upload test plan (jmx file)",
  "InstanceType": "string",
  "InstanceCount": 2,
  "AccountId": "A-XXXXX",
  "BaseRegion": "us-east-1",
  "VpcId": "vpc-XXXX",
  "SubnetIds": [
    "subnet-XXXXX"
  ]
}
```

Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
OutputLocation | String | Location where you want the output files to go to | Yes
TestPlan | Integer | JMX test plan you want to execture | Yes
InstanceType | String | Instance type you want Batchly to launch | Yes
InstanceCount | Integer | Number of instances of the InstanceType you want Batchly to launch and manage | Yes
AccountId | String | Identifier of the Account under which the job should execute | Yes
BaseRegion | String | AWS region where your job will run |Yes
VpcId | String | Vpc Id where the job should execute | Yes
SubnetIds | String | Specify the Subnet Id under selected Vpc | Yes

**Success Response**

```
{
  "RequestId": "string",
  "Data": {
    "Runs": 0,
    "IsScheduled": true,
    "IsExecuting": true,
    "Engine": "All",
    "AppName": "string",
    "IsPrivateApp": true,
    "Id": "string",
    "Name": "string"
  },
  "Errors": {},
  "ContinuationToken": "string"
}
```
---

#### FFMpeg - Video Transcoding App

APP_NAME: FFMpeg

**Request Header**

```
{
  "Name": "string",
  "TimeLimit": 0,
  "ProfileId": "string",
  "FileNameSuffix": "string",
  "SourceLocation": "string",
  "DestinationLocation": "string",
  "AccountId": "string",
  "BaseRegion": "string",
  "VpcId": "string",
  "SubnetIds": [
    "string"
  ]
}
```

Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
TimeLimit | Integer | Time limit when your job needs to complete | Yes
ProfileId | String | Common video profiles for MP4 and HLS | Yes
FileNameSuffix | String | Suffix to identify the transcoded output file | No
SourceLocation | String | Location where all the input files reside | Yes
DestinationLocation | String | Location where you want the output files to go to | Yes
AccountId | String | Identifier of the Account under which the job should execute | Yes
BaseRegion | String | AWS region where your job will run |Yes
VpcId | String | Vpc Id where the job should execute | Yes
SubnetIds | String | Specify the Subnet Id under selected Vpc | Yes


**Success Response**

```
{
  "RequestId": "string",
  "Data": {
    "Runs": 0,
    "IsScheduled": true,
    "IsExecuting": true,
    "Engine": "All",
    "AppName": "string",
    "IsPrivateApp": true,
    "Id": "string",
    "Name": "string"
  }
```
---

#### ImageMagick - Image processing App

APP_NAME: ImageMagick

**Request Header**

```
{
  "Name": "string",
  "SourceLocation": "string",
  "DestinationLocation": "string",
  "TimeLimit": 0,
  "Resize": "string",
  "AccountId": "string",
  "BaseRegion": "string",
  "VpcId": "string",
  "SubnetIds": [
    "string"
  ]
}
```

Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
SourceLocation | String | Location where all the input files reside | Yes
DestinationLocation | String | Location where you want the output files to go to | Yes
TimeLimit | Integer | Time limit when your job needs to complete | Yes
Resize | String | Image height and width to which the image needs to be converted to e.g. 100x100 | Yes
AccountId | String | Identifier of the Account under which the job should execute | Yes
BaseRegion | String | AWS region where your job will run |Yes
VpcId | String | Vpc Id where the job should execute | Yes
SubnetIds | String | Specify the Subnet Id under selected Vpc | Yes

**Success Response**

```
{
  "RequestId": "string",
  "Data": {
    "Runs": 0,
    "IsScheduled": true,
    "IsExecuting": true,
    "Engine": "All",
    "AppName": "string",
    "IsPrivateApp": true,
    "Id": "string",
    "Name": "string"
  },
  "Errors": {},
  "ContinuationToken": "string"
}
```

---

#### Tesseract - Optical Character Recognition App

APP_NAME: Tesseract

**Request Header**

```
{
  "Name": "string",
  "SourceLocation": "string",
  "DestinationLocation": "string",
  "TimeLimit": 0,
  "AccountId": "string",
  "BaseRegion": "string",
  "VpcId": "string",
  "SubnetIds": [
    "string"
  ]
}
```

Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
SourceLocation | String | Location where all the input files reside | Yes
DestinationLocation | String | Location where you want the output files to go to | Yes
TimeLimit | Integer | Time limit when your job needs to complete | Yes
AccountId | String | Identifier of the Account under which the job should execute | Yes
BaseRegion | String | AWS region where your job will run |Yes
VpcId | String | Vpc Id where the job should execute | Yes
SubnetIds | String | Specify the Subnet Id under selected Vpc | Yes

**Success Response**

```
{
  "Runs": 0,
  "IsScheduled": true,
  "IsExecuting": true,
  "Engine": "All",
  "AppName": "string",
  "IsPrivateApp": true,
  "Id": "string",
  "Name": "string"
}
```
---