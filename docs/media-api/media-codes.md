### Media Codes

#### Status Values

Code | Meaning
--|--
101 | Job Starting
102 | Job Processing
103 | Job Error
104 | Job Success
110 | Unknown

#### Substatus Values

Code | Meaning
-- | --
400 | Operation is starting
500 | File Downloading
600 | File Uploading
700 | File transcoding
800 | File stitching
900 | Detecting blackband values
901 | Remove blackband
1000 | Create master playlist (for Hls)
1100 | Create thumbnails
1200 | Operation completed

#### Error Code Values


Code | Meaning
--|--
80 | Incorrect input profile parameters
91 | SQS setup failed in AWS account
501 | S3 bucket not found or incorrect access permission
502 | File download failed
601 | File upload failed
701 | Transcode operation failed
801 | Stitching operation failed
901 | Metadata operation setup failed
902 | Metadata operation failed
903 | Failed to get output bitrate 
904 | Failed to get metadata
905 | Failed to create master playlist (for Hls)
906 | Failed to detect blackband
907 | Failed to remove blackband

