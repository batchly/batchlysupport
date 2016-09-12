### Media Operations Supported


HTTP Method | Endpoint | Description
--|--|--
GET | api/Profiles | Returns all the profiles available in batch.ly
GET | api/Profiles/{id} | Returns parameters of a particular profile
POST| api/Profiles | Create a new private profile for your usage. 
PUT | api/Profiles/{id} | Edit a given private profile with updated information
DELETE | api/Profiles/{id} | Removes a private profile.
POST | api/Jobs | Creates a new transcoding job with the formats specified in the JSON request
GET | api/Jobs/{id} |Get the status of a specific job
GET | api/Jobs/{id}?profile={profileName} | Get the status of a specific transcoding within a media job

#### Operations
The following Operations are supported as part of the Create Job call.  The rules associated with entities are described below.

Operation | Sources | Profiles | Destinations | Remarks
--|--|--|--|--
Transcode | One Path | One or More Profiles | One Destination | The source file is transcoded to the given profiles.  The destination file name is appended with profile name when creating output
Stitch | At Least Two Paths | None | One Destination | Operation combines the input files to create the destination output
Hls | One Path | At Least Two Profiles | One Destination | The source is converted into many profiles and a destination .m3u8 file created with the appropriate references
GetMetadata | One or more Paths | NA | NA | Individual source path meta data is sent back as webhooks to the given callback url
GenerateThumbnails | One Path | One or More Profiles | One Destination | Source file is used to snapshot to create thumbnails based on profiles.  Destination file format is used and appended with index of images.

Support for additional operations are currently in development and the document will be updated to reflect the same in near future.

### Profile Settings

#### Transcode and Hls Settings
Batchly has in-built profiles for most of the common MP4 and HLS output formats. However, you have flexibility to add or modify the values.

Field Name | Allowed Values
--|--
format | mp4, hls
video_codec | libx264
video_bitrate | Integer e.g represent 100k as 100000
minrate | Integer e.g represent 100k as 100000
maxrate | Integer e.g represent 100k as 100000
bufsize | Integer e.g represent 100k as 100000
video_width | Integer e.g 1084
video_height | Integer e.g 720
framerate | Integer e.g. 15, 30
group_of_pictures | Integer. Typically, double the framerate
video_preset | fast, medium, slow, slower, veryslow, placebo. Default - Medium
profile | high, main, baseline
level | 3.0, 3.1, 4.0, 4.1, 4.2
video_disable | yes, no
video_disable_subtitle | yes,no
audio_codec | aac,ac3
audio_channels | e.g 2
audio_bitrate | Integer e.g represent 100k as 100000
audio_samplerate | E.g 44100, 48000
x264opts | H.264 specific options
movflags | faststart moves the video info to header
hls_time | segment length. Recommended value 9
hls_list_size | Set to 0 for all VOD playlist entries
hls_flags | If set to 'single_file', all segments will be stored in 1 ts file

#### Thumbnail Settings
You can create custom thumbnail profiles by using the following field values.

Field Name | Allowed Values
--|--
thumbnail_time | In seconds. E.g.: 10 for generating thumbnail every 10 seconds
thumbnail_width | In pixels. E.g.: 50 for generating a thumbnail of width 50px
thumbnail_height | In pixels E.g.: 50 for generating a thumbnail of height 50px

### Models

#### Profile
For both profile create and update, the following json needs to be sent. 

- For create, perform a HTTP POST request to /api/Profiles 
- For Update perform a HTTP PUT request to /api/Profiles/{id} endpoint

```
{
  "Name": "unique_profile_name_with_no_spaces",
  "Type": "Transcode | Hls | GenerateThumbnails",
  "Parameters": {
    "key": "value",
    "key2": "value2"
  }
}
```

#### Job

```
{
  "Name": "Name",
  "Sla": 2,
  "Notification": {
      "SuccessCallback": "internal url",
      "ErrorCallback": "internal url"
    },
  "Operations": [
    {
      "Type": "Stitch",
      "Profiles": [],
      "Sources": [
        {
          "Type": "S3",
          "Path": "https://input1"
        },
        {
          "Type": "S3",
          "Path": "https://input2"
        }
      ],
      "Destinations": [
        {
          "Type": "S3",
          "Path": "https://output"
        }
      ]
    },
    {
      "Type": "Transcode",
      "Profiles": ["generic-hls-144p"],
      "Sources": [
        {
          "Type": "S3",
          "Path": "https://input"
        }
      ],
      "Destinations": [
        {
          "Type": "S3",
          "Path": "https://output"
        }
      ], 
      "Metadata": {
          "Probe": true,
          "Callback": "callback url"
        } 
    },
    {
      "Type": "Hls",
      "Profiles": ["generic-hls-240p", "my-custom-480p"],
      "Sources": [
        {
          "Type": "S3",
          "Path": "https://input"
        }
      ],
      "Destinations": [
        {
          "Type": "S3",
          "Path": "https://output",
          "Acl": "private|public-read|public-read-write|authenticated-read|bucket-owner-read|bucket-owner-full-control",
        },
      {
      "Type": "GenerateThumbnails",
      "Profiles": ["thumb_10_50_50"],
      "Sources": [
        {
          "Type": "S3",
          "Path": "https://input"
        }
      ],
      "Destinations": [
        {
          "Type": "S3",
          "Path": "https://output/thumb.jpg"
        }
      ]
    }
  ]
}

```

#### Callbacks

**Success**

```
{
  "ProcessId": "string",
  "StartedOn": "start date time in universal time format",
  "CompletedOn": "completion date time in universal time format"
}
```

**Status Callbacks**

There are 2 types of status callbacks, one for the overall progress and the other for individual progresses for each of the profiles selected.

- Consolidated Callback

```
https://media.batchly.net/api/jobs/{id}
```

The response would be

```
"ProcessID": "string"
"StartedOn":"start date time in universal time format",
"CompletedOn":"completion date time in universal time format",
"Progress": "percentage"
"StatusCode":"overall job status",|2|3|4|
"Status":"status message" |Started|Success|Error|
```

- Individual profile status syntax

```
https://media.batchly.net/api/jobs/{id}?profile={profileName}
```

The response for each profile would be:

```
"ProcessID": "string"
"StartedOn":"start date time in universal time format",
"CompletedOn":"completion date time in universal time format",
"Progress":"in percentage",
"Status":"status message",   
"SubStatus":"substatus message",
"FileName": "output filename"
```

**Error**

```
{
  "ProcessId": "string",
  "StartedOn": "start date time in universal time format",
  "CompletedOn": "completion date time in universal time format",
  "ErrorCode": "system error code",
  "ErrorMessage": "failure reason"
}
```

**Metadata**

```
{
  "ProcessId": "string",
  "Source": "file path",
  "Metadata": "probe result in json string"
}
```

Proceed to [Media Status Codes](media-codes.md) or back to [Media Overview](media-definition.md)