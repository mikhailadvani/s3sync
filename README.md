# aws_s3sync

## Installation

`pip install aws_s3sync`

## Execution

#### Pre-requisites

Setup the following environment variables

**AWS_ACCESS_KEY_ID**
**AWS_SECRET_ACCESS_KEY**

#### Command

`sync_to_s3`

#### Arguments

```
optional arguments:
  -h, --help            show this help message and exit
  -b BUCKET, --bucket BUCKET
                        Name of the S3 bucket to upload data to
  -f FILE_PATH, --file_path FILE_PATH
                        Path of the file to be uploaded
  -k KEY, --key KEY     Key of the object. Same as file_path if undefined
  -m {auto,sync,simple-upload}, --mode {auto,sync,simple-upload}
                        Method of upload
  --chunk_size CHUNK_SIZE
                        Size of chunk in multi-part upload in MB
  --multipart_threshold MULTIPART_THRESHOLD
                        Minimum size in MB to upload using multipart
```

##### Mode

* `auto` : Single-part upload or multi-part upload will be chosen based on the file being smaller/larger than `multipart_threshold`
* `sync` : Upload file to S3 only if the local file has changed. Checked based on ETag/MD5
* `simple-upload` : Force single-part upload. Applicable only for files of size larger than `multipart_threshold`

