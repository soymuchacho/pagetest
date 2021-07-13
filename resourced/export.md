# export


**Brief Description** 

- get the first frame of the hi-res media file
- export hi-res media data

**Request URL** 
- `https://resource.tvunetworks.com:10600/export`

**Request Method**
- POST 

**Request Example**

```JSON
{
	"_ServiceName": "resourceservice",
	"_UrlPath": "export",
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
	"FetchMedia": true,
	"S3Region": "ap-northeast-1",	//depricated
	"S3Bucket": "imgbed",	//depricated
	"storage_info" : "BASE64 string",
	"userid": "dev@tvunetworks.com",
	"story": {
		"id": "4B999DC458FBC4C800000000",
		"name": "04-60C262253621833_0.0993375889",
		"slug_info": "base64 string",
	}
}

Get thumbnail only

{
	"_ServiceName": "resourceservice",
	"_UrlPath": "export",
	"_Version":1,

	"StartPos": 1562253612833,
	"StartTime": "00:13:12",
	"Duration": 9000,
	"PeerId": "4D7446C8141EE167",
	"LivePath": "mp4/55524C2004E/55524C2041268-6bdb82b53e0a/1/stream.mpd",
	"FileName": "04-60C262253621833_0.0993375889",
	"SessionId": "2A39603DDB0F47CFB32E96C8366084AE",
	"FetchMedia": false,
	"FetchThumb": true,
	"userid": "dev@tvunetworks.com",
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
|FetchMedia |\*  |boolean | this field decides whether generate file or not when API is invoked. You can use `false` to get the thumbnail of the first frame. The default value is `false`
|FetchThumb |  |boolean | You can use `true` to get the thumbnail of any frame. The default value is `false`. FetchMedia must be `false`.
|FileName |  |string | the final file name
|SessionId |  |string  | for auth
|export_type |  |number | `0` 、`1` or `2`, the default value is `0`, `1` is H.264, `2` is H.265.
|S3Region |  |string  |s3 region
|S3Bucket |  |string  |s3 bucket
|userid |  |string  |the id of user
|story |  |pairs  |"id":"","name":"", "slug_info": "base64 string",

**Example of Response**

- "FetchMedia": false
```JSON
{
	"TimeWait":0,
	"ErrorCode":0,
	"ErrorMessage":"Success",
	"ImagePath":"/4B999DC458FBC4C80000000000000002/4B999DC458FBC4C80000000000000002_20200316-02-21-49_4B999DC458FBC4C80000000000000002_FE31F2B2CEAA2E63_4b13335c-2fc1-45ea-9cb5-f92065a26e91_1584973791094_7170000.jpg",
	"S3Dir":"export",
}
```

- "FetchMedia": true
```JSON
{
	"TimeWait":2000,
	"ErrorCode":1,
	"ErrorMessage":"Work Not Finish",
	"ImagePath":"/4B999DC458FBC4C80000000000000002/4B999DC458FBC4C80000000000000002_20200316-02-21-49_4B999DC458FBC4C80000000000000002_FE31F2B2CEAA2E63_4b13335c-2fc1-45ea-9cb5-f92065a26e91_1584973791094_7170000.jpg",
	"S3Dir":"export",
	"LackLength":123000
}
```

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
	
	
	"slug_info" : {
    	"slug_id":"abcdefghig",
    	"slug_name":"test",
    	"slug_date":"",
    	"clipped_date":"",
    	"clip_length":""
	}
	
```