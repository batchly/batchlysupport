#### Table of Contents

- [Batchly Media Overview](media-definition.md)
- [Media Operations API](media-operations.md)
- [Media Status Codes](media-codes.md)

### Batchly Media API Overview

Batchly Media enables both digital producers and publishing companies to automaticallybenefit from AWS cost and usage savings by optimizing media workloads with spot instances and EC2 smart sizing. Batchly is 20x times cheaper than other popular cloud transcoders.

Features that customers love:

**Instance Smart Sizing** Realize ultimate EC2 efficiencies with automatic instance sizing based on the file type, file size and output profiles.

**Parallelization** Process each profile in parallel to give you fast transcode times and quick time-to-market.

**AWS Spot Bid Optimization** Seamlessly deploy, move, and manage workloads over high cost savings spot instances across any AWS region.

**Seamless Integration** Integrate to any third party CMS solution using Batchly Media REST APIs.

**Fully Managed** Benefit from cost and utilization optimizations from within your own AWS account while we do the heavy lifting. Add to it, you don’t pay for ingress and egress of your video content.



#### Why Batchly Media?

The global Video-On-Demand (VOD) market is projected to reach US$91B by 2020, largely driven by revolution in mobile technologyandfreedomtoviewitacrossmultipledevices,controloverviewingtimeand varietyofchoice.

For publishers and content owners, VODenabling their entire content libraryrequires transcoding it into multiple bitrates and resolutions (profiles) to suit their demography. This is a expensive operation often involving transcoding multiple renditions for different geographies, channels and devices. In addition, cloud transcoders require you to move data into theirserverswhichadds toyouringressandegresscostsand mightnotcomplywithyourlicensingpolicies.

#### Technical Details

 - AVC (H.264) and HEVC Codec Support 
 - HLS & MPEG-DASH Packaging
 - Runs in your AWS account
 - Black band removal
 - Thumbnail generation
 - Stitch multiple videos
 - REST APIs
 - Webhook callbacks for success, failure and progress
 - Metadata info for original and transcoded files
 - Set AWS ACL rules for output files

#### API Definition

The Batchly Media Api supports the following entities

- Profiles
- Jobs

Profiles are a way to group all the parameters that are required for successful processing of a file.  This may include the width, height, aspect ratio, etc…

Batchly Media Api has few pre built profiles that are available for performing media operations.  

Jobs are calls to perform various operations on actual files.  This call involves the following data to be sent as part of the request.

- The source location of your video.
- Job notification location (via webhook)
- One or multiple custom or preset desired encoding recipes.
- One or multiple delivery points for your video.

Batchly responds immediately with a media ID so your application can track the progress of the job.

#### End Point

To send API requests to Batchly.net, please send HTTP(S) post requests to:

```
https://media.batchly.net/
```

#### Authentication

**ApiKey**
A user's unique authentication key string. This authentication key will be shared with your team when the system is configured for your usage. This key is mandatory and needs to be sent as part of every Api Call.  The Key should be sent along in the Request Header as below.

```
Authorization: ApiKey AccessKey:SecretKey
```


