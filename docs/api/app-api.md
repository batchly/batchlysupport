### App Specific APIs

Batchly works through Apps. There are marketplace apps such as FFMpeg for video transcoding, and JMeter for load testing. You may also upload your own private app to run in your Batchly account.

Nevertheless, each app has its own set of APIs to perform the basic operations. The request headers, however, differ based on the app you want to create.

**Common Actions Supported By All Apps**

HTTP Method | Endpoint | Description
--|--|--
POST | api/apps/APP_NAME/{id}/Execute | Execute the job
POST | api/apps/APP_NAME | Create a new job
PUT | api/apps/APP_NAME/{id} | Edit a job with updated information. 
GET | api/apps/APP_NAME/{id} | Get details for a job
DELETE | api/apps/APP_NAME/{id} | Delete a job
GET | api/apps/APP_NAME/jobs | Lists all jobs

#### App Specific Request headers 

---

#### FFMpeg - Video Transcoding App

**Request Header**

```
{
  "Name": "string",
  "ProjectId": "string",
  "Region": "string",
  "TimeLimit": 0,
  "ProfileId": "string",
  "FileNameSuffix": "string",
  "SourceLocation": "string",
  "DestinationLocation": "string"
}
```

Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
ProjectId | String | Identifier of the Project under which the job should execute | Yes
Region | String | AWS region where your job will run | Yes
TimeLimit | Integer | Time limit when your job needs to complete | Yes
ProfileId | String | Common video profiles for MP4 and HLS | Yes
FileNameSuffix | String | Suffix to identify the transcoded output file | No
SourceLocation | String | Location where all the input files reside | Yes
DestinationLocation | String | Location where you want the output files to go to | Yes

**Example result**

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

#### ImageMagick - Image processing App

**Request Header**

```
{
  "Name": "string",
  "ProjectId": "string",
  "SourceLocation": "string",
  "DestinationLocation": "string",
  "Region": "string",
  "TimeLimit": 0,
  "Resize": "string"
}
```

Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
ProjectId | String | Identifier of the Project under which the job should execute | Yes
Region | String | AWS region where your job will run | Yes
TimeLimit | Integer | Time limit when your job needs to complete | Yes
Resize | String | Image height and width to which the image needs to be converted to e.g. 100x100 | Yes
SourceLocation | String | Location where all the input files reside | Yes
DestinationLocation | String | Location where you want the output files to go to | Yes

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

**Request Header**

```
{
  "Name": "string",
  "ProjectId": "string",
  "SourceLocation": "string",
  "DestinationLocation": "string",
  "Region": "string",
  "TimeLimit": 0
}
```

Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
ProjectId | String | Identifier of the Project under which the job should execute | Yes
Region | String | AWS region where your job will run |Yes 
TimeLimit | Integer | Time limit when your job needs to complete | Yes
SourceLocation | String | Location where all the input files reside | Yes
DestinationLocation | String | Location where you want the output files to go to | Yes

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

#### JMeter - Load Testing App

**Request Header**

```
{
  "Name": "string",
  "ProjectId": "string",
  "DestinationLocation": "string",
  "TestPlan": "string",
  "InstanceType": "string",
  "InstanceCount": 0
}
```

Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
ProjectId | String | Identifier of the Project under which the job should execute | Yes
TestPlan | Integer | JMX test plan you want to execture | Yes
DestinationLocation | String | Location where you want the output files to go to | Yes
InstanceType | String | Instance type you want Batchly to launch | Yes
InstanceCount | Integer | Number of instances of the InstanceType you want Batchly to launch and manage | Yes

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

#### Hive App

**Request Header**

```
{
  "Name": “Hive Job”,
  "ProjectId": “P-XXXXX”,
  "ClusterId": “j-XXXXX”,
  "ScriptLocation": “s3://BUCKET_NAME/PATH_TO_SCRIPT”,
  "InputLocation": “s3://BUCKET_NAME/PATH_TO_DATASET”,
  "OutputLocation": “s3://BUCKET_NAME/PATH_TO_OUTPUT_LOCATION”,
  "Arguments": “arg1 arg2 arg3”
  "ActionOnFailure": “CONTINUE”
  "InstanceTypes": ["c4.large", "m3.large"]
}    
```

Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
ProjectId | String | Identifier of the Project under which the job should execute | Yes
ClusterId | String | Cluster Id where the job should execute | Yes
ScriptLocation | String | S3 location where the script resides | Yes
InputLocation | String | S3 location where the dataset resides | No
OutputLocation | String | S3 location where results are written | No
Arguments | String | Any arguments that the script requires | No
ActionOnFailure | String | CONTINUE, CANCEL_AND_WAIT, TERMINATE_CLUSTER | Yes
InstanceTypes | String[] | The instance types to be launched | Yes


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

**Request Header**

```
{
  "Name": “Pig Job”,
  "ProjectId": “P-XXXXX”,
  "ClusterId": “j-XXXXX”,
  "ScriptLocation": “s3://BUCKET_NAME/PATH_TO_SCRIPT”,
  "InputLocation": “s3://BUCKET_NAME/PATH_TO_DATASET”,
  "OutputLocation": “s3://BUCKET_NAME/PATH_TO_OUTPUT_LOCATION”,
  "Arguments": “arg1 arg2 arg3”
  "ActionOnFailure": “CONTINUE”
  "InstanceTypes": ["c4.large", "m3.large"]
} 
```

Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
ProjectId | String | Identifier of the Project under which the job should execute | Yes
ClusterId | String | Cluster Id where the job should execute | Yes
ScriptLocation | String | S3 location where the script resides | Yes
InputLocation | String | S3 location where the dataset resides | No
OutputLocation | String | S3 location where results are written | No
Arguments | String | Any arguments that the script requires | No
ActionOnFailure | String | CONTINUE, CANCEL_AND_WAIT, TERMINATE_CLUSTER | Yes
InstanceTypes | String[] | The instance types to be launched | Yes


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

#### Spark App

**Request Header**

```
{
  "Name": “Spark Job”,
  "ProjectId": “P-XXXXX”,
  "ClusterId": “j-XXXXX”,
  "DeployMode": “Cluster”,
  "SparkSubmitOptions": “opt1 opt2 opt3”,
  "ApplicationLocation": “s3://BUCKET_NAME/PATH_TO_SPARK_JAR”,
  "Arguments": “arg1 arg2 arg3”
  "ActionOnFailure": “CONTINUE”
  "InstanceTypes": ["c4.large", "m3.large"]
}
```


Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
ProjectId | String | Identifier of the Project under which the job should execute | Yes
ClusterId | String | Cluster Id where the job should execute | Yes
DeployMode | Integer | 1 (for Cluster mode), 2 (for Client mode) | Yes 
SparkSubmitOptions | String | Specify other options for spark-submit | No
ApplicationLocation | String | S3 location where the Spark jar resides | Yes
Arguments | String | Any arguments that the script requires | No
ActionOnFailure | String | CONTINUE, CANCEL_AND_WAIT, TERMINATE_CLUSTER | Yes
InstanceTypes | String[] | The instance types to be launched | Yes


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

**Request Header**

```
{
  "Name": “HadoopStreaming Job”,
  "ProjectId": “P-XXXXX”,
  "ClusterId": “j-XXXXX”,
  "MapperLocation": “s3://BUCKET_NAME/PATH_TO_MAP_FUNCTION”,
  "ReducerLocation": “s3://BUCKET_NAME/PATH_TO_REDUCE_FUNCTION”,
  "InputLocation": “s3://BUCKET_NAME/PATH_TO_DATASET”,
  "OutputLocation": “s3://BUCKET_NAME/PATH_TO_OUTPUT_LOCATION”,
  "Arguments": “arg1 arg2 arg3”
  "ActionOnFailure": “CONTINUE”
  "InstanceTypes": ["c4.large", "m3.large"]
}
```


Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
ProjectId | String | Identifier of the Project under which the job should execute | Yes
ClusterId | String | Cluster Id where the job should execute | Yes
MapperLocation | String | S3 location of the map function or the name of the Hadoop streaming command to run | Yes
ReducerLocation | String | S3 location of the reduce function or the name of the Hadoop streaming command to run | Yes
InputLocation | String | S3 location where the dataset resides | Yes
OutputLocation | String | S3 location where the results are written | Yes
Arguments | String | Any arguments that the script requires | No
ActionOnFailure | String | CONTINUE, CANCEL_AND_WAIT, TERMINATE_CLUSTER | Yes
InstanceTypes | String[] | The instance types to be launched | Yes


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

#### HadoopCustom App

**Request Header**

```
{
  "Name": “Hadoop Job”,
  "ProjectId": “P-XXXXX”,
  "ClusterId": “j-XXXXX”,
  "JarLocation": “s3://BUCKET_NAME/PATH_TO_JAR”,
  "Arguments": “arg1 arg2 arg3”
  "ActionOnFailure": “CONTINUE”
  "InstanceTypes": ["c4.large", "m3.large"]
}
```


Field Name | Data Type | Description | Mandatory
--|--|--|--
Name | String | Name for the job | Yes
ProjectId | String | Identifier of the Project under which the job should execute | Yes
ClusterId | String | Cluster Id where the job should execute | Yes
JarLocation | String | A path into S3 or a fully qualified java class in the classpath | Yes
Arguments | String | Any arguments that the script requires | No
ActionOnFailure | String | CONTINUE, CANCEL_AND_WAIT, TERMINATE_CLUSTER | Yes
InstanceTypes | String | The instance types to be launched | Yes


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