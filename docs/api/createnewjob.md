#### Job

A job is a reusable template that brings all data and code together with runtime parameters. The job when created includes the default SLA and region for operation. For each execution, you can vary the SLA and region.

For jobs that use AMI based processor, operation region is same as AMI region. Similarly jobs that use VPC projects, the region is limited to the VPC region.

### Create
Creating a job is essentially a composition of multiple API calls.

- **Define Processor: **
You can create a new processor as defined in the previous section.

- **Define Source:**
Depending on your data store, you can call the appropriate API endpoints to define the data source.

-- **AWS S3: **
To define a new S3 location, you need to call the API with bucket name and folder.

 | 
-|-
**REST endpoint** | POST /api/DataSources/S3 
** SDK method **  | DataSourcesController – AddS3 
**Request**	    | AddS3DataSourceRequest        
**Response**      | 201 Created String   

--- **Add S3 Data Source Request**
To create a new request to add S3 storage as data source

Properties | Description 
------------ | -------------
Bucket | Name of the S3 bucket 
Folder| Folder within the S3 bucket

--** Define Destination:**
Depending on your data store, you can call the appropriate API endpoints to define the destination. For processors that return a default response, destination is not mandatory.

--** AWS S3: **
To define a new S3 location, you need to call the API with bucket name and folder.

 | 
-|-
**REST endpoint** | POST /api/DataSources/S3 
** SDK method **  | DataSourcesController – AddS3 
**Request**	    | AddS3DataSourceRequest        
**Response**      | 201 Created String  

- ** Add S3 Data Source Request**
To create a new request to add S3 storage as data source

Properties | Description 
------------ | -------------
Bucket | Name of the S3 bucket 
Folder| Folder within the S3 bucket

- **Define a job specific Parameter group**
This is an optional step where you can define a new parameter group that uses different runtime parameters. The procedure to create a new parameter group is defined above.

- **Compose Job**
After all the required entity identifiers are available, you can call the create job endpoint to create a new job.

 | 
-|-
**REST endpoint** |	POST /api/Jobs
**SDK method**	| JobsController – AddJob
**Request** |	CreateJobRequest
**Response** |	201 Created JobModel

-- **Create Job Request**
Request to create a new job

Properties | Description 
------------ | -------------
Name	|Name of the job
Project Id	| Identifier of the project under which the job should execute 
Processor Id |	Identifier of the processor that processes the data
Data Source Id |	Identifier of the Data Source from which data is extracted for processing
Destination Id	| Identifier to the Data Source into which processed data is sent
Schedule |	Schedule information of Job if it should be managed by Scheduler
Region |	Default Region in which the job should execute. You can change region for each run when calling "Execute" endpoint.
SLA | Default SLA for the job execution. You can change SLA for each run when calling the "Execute" endpoint.
Parameters |	Parameter name and values that should be sent to the processor. The values can be changed for each run when calling the "Execute" endpoint.