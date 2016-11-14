Batchly API supports the following entities:

* Jobs
* Runs
* Accounts

#### Jobs API

Jobs are calls to perform various operations on the actual dataset. This call varies from one app to another. Though it is app-specific, each job requires jobname, Project, SLA, input location and output location to be mentioned.

Batchly responds immediately with a job ID so your application can track the progress of the job.

**Actions Supported**

HTTP Method | Endpoint | Description
----------- | -------- | ---------------
GET         | api/Jobs | Returns all the jobs associated with your Batchly account

To run individual jobs, call the API associated with the respective app. [App API Documentation](app-api.md)

#### Runs API

Runs are individual instances of the job in Batchly. Runs API allows you to list and delete the runs in your Batchly account.


HTTP Method | Endpoint | Description
----------- | -------- | ------------------
GET         | /api/Runs | Get all the runs associated with your batchly account
GET         | /api/Runs/{id} | Get the details of the run for the given id
DELETE | /api/Runs/{id} | Delete the run details from your account

#### Accounts API

Attach your AWS account to batchly using the accounts API. Accounts calls allow you to create, edit or view AWS accounts associated with your Batchly account.

**Actions Supported**

HTTP Method | Endpoint | Description
--|--|--
POST | /api/Accounts/AWS | Add new AWS account to your batchly account
DELETE | /api/Accounts/{id} | Delete the AWS account associated with this id
GET | /api/Accounts/{id} | Get the AWS account details related to this id
PUT | /api/Accounts/{id} | Update the details for this id
GET | /api/Accounts | Get all the AWS accounts associated with your batchly account