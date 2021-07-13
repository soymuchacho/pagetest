# export-to-s3dir


**Brief Description** 

- export hi-res media data to s3 dir

**Request URL** 
- `https://resource.tvunetworks.com:10600/export-to-s3dir`

**Request Method**
- POST 

**Request Example**

```JSON
{
	"_ServiceName": "resourceservice",
	"_UrlPath": "export-to-s3dir",
	"_Version":1,

	"ServiceCaller": "mma",
	"StartPos": 1562253612833,
	"StartTime": "00:13:12",
	"Duration": 9000,
	"PeerId": "4D7446C8141EE167",
	"LivePath": "mp4/55524C2004E/55524C2041268-6bdb82b53e0a/1/stream.mpd",
	"FileName": "04-60C262253621833_0.0993375889",
	"SessionId": "2A39603DDB0F47CFB32E96C8366084AE",
	"export_type": 1,
	"storage_info" : "BASE64 string",
	"userid": "dev@tvunetworks.com",
	"ExportS3Region": "us-west-1",
	"ExportS3Bucket": "export",
	"ExportS3Key": "AKIAKMEWDHAJQH4YLNFN:SQwJeOobv82932fksfel+/6V7uiRVgudrJF4oTH",
}

```

**Parameter** 

|Parameter|Required|Type|Description|
|:----    |:---|:----- |-----   |
|ServiceCaller |\*  |string | the name of service caller. `mma` or `search`
|StartPos |\*  |number | in millisecond. Get from Search API.
|StartTime |\*  |string | in millisecond. Relative time of mark.
|Duration |\*  |number | in millisecond 
|LivePath |\*  |string | Get from Search API 
|FileName |  |string | the final file name
|SessionId |  |string  | for auth
|export_type |  |number | `0` 、`1` or `2`, the default value is `0`, `1` is H.264, `2` is H.265.
|userid |  |string  |the id of user
|ExportS3Region |  |string  |export s3 region
|ExportS3Bucket |  |string  |export s3 bucket
|ExportS3Key |  |string  |export s3 key

**Example of Response**
 ```JSON
{
	"TimeWait":2000,
	"ErrorCode":-1,
	"ErrorMessage":"not such dir",
	"ImagePath":"/4B999DC458FBC4C80000000000000002/4B999DC458FBC4C80000000000000002_20200316-02-21-49_4B999DC458FBC4C80000000000000002_FE31F2B2CEAA2E63_4b13335c-2fc1-45ea-9cb5-f92065a26e91_1584973791094_7170000.jpg",
	"VideoPath":"/export/4B999DC458FBC4C80000000000000002/test.ts"
	"Version":"v1",
	"S3Dir":"export",
	"LackLength": 0
}
 ```

**Parameters of Response**

|Parameter|Type|Description|
|:-----  |:-----|----- |
|ErrorCode |number  | `1` means task is processing, `5` means ready to download |
|ErrorMessage |string  | |
|ImagePath |string  | The first frame of the exported clip |
|VideoPath |string  | The location of exported media clip |
|Version |string  | the version of resource |
|S3Dir       |string | s3bucket sub path
|LackLength       |number | in millisecond. The difference in length between the requested exported video clip and the actual exported video clip |


**Comment** 

- The service limits the number of concurrent request for the limited harddisk I/O and network.

- The original string of "BASE64 string" should looks like:

```JSON
	"storage_info" : [
		{
			"storage_purpose": "ts",
			"storage_type": "S3",
			"storage_enable": true,
			"storage_name": "mma-video-archive",
			"storage_location": "us-west-1",
			"storage_description": "",
			"storage_root_folder": ""
		},    
		{
			"storage_purpose": "mp4",
			"storage_type": "S3",
			"storage_enable": true,
			"storage_name": "mma-video-archive",
			"storage_location": "us-west-1",
			"storage_description": "",
			"storage_root_folder": ""
		}
	]
	
```