#s3-delete


**Brief Description** 

- delete ts/mpd s3 dir

**Request URL** 
- `https://resource.tvunetworks.com:10600/api/resource/v1/i/s3-delete`

**Request Method**
- POST 

**Request Example**

```JSON
{
	"bucket": "mma-test-s3",
	"region": "ap-northeast-us",
	"mpdpath":"ADFASDFSFD/WEFWFEWEW",
	"tspath":"EWEWLFWLEFW/WEFWEWFEW",
}

```

**Parameter** 

|Parameter|Required|Type|Description|
|:----    |:---|:----- |-----   |
|bucket |\*  |string | s3 storage bucket
|region |\*  |string | s3 storage bucket region
|mpdpath |\*  |string | the path of mpd
|tspath |\*  |number | the path of ts

**Example of Response**
 ```JSON
{
	"ErrorCode":0,
	"ErrorMessage":"success",
}

{
	"ErrorCode":1,
	"ErrorMessage":"error",
}
 ```

**Parameters of Response**

|Parameter|Type|Description|
|:-----  |:-----|----- |
|ErrorCode |number  | `0` success, Others mean failed.
|ErrorMessage |string  | |
