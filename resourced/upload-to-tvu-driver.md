**Brief Description** 

- upload file to tvu driver

**Request URL** 
- `https://resource.tvunetworks.com:10600/api/resource/v1/i/upload-to-tvu-driver`
  
**Request Method**
- POST 

**Request Example**

```JSON
{
    "_ServiceName": "resourceservice",
    "_UrlPath": "upload-to-tvu-driver",
    "_Version":1,

	"PeerId": "4D7446C8141EE167",
	"SessionId": "55524C20412686bdb82b53",
	"UserId": "vespergu@tvunetworks.com",
	"LivePath": "mp4/55524C2004E/55524C2041268-6bdb82b53e0a/1/stream.mpd",
	"UploadPath": "tvu/test",
	"PathId": "1cc7ff4569994125a35c4339d53ce01c",
	"Bucket": "mma-s3-test",
	"Region": "ap-northeast-2",
	"FileName": "export.ts",
	"StorageInfo" : "BASE64 string", // If it is a local service, this parameter can be omitted.
}

```

**Parameter** 

|Parameter|Required|Type|Description|
|:----    |:---|:----- |-----   |
|PeerId |\*  |string | peer id
|SessionId |\*  |string | user session
|UserId |\*  |string | the id of user 
|LivePath|\* |string | Get from Search API
|UploadPath |\*  |string  | the path of the uploaded file to s3
|PathId |\*  |string  | the id of the uploaded path
|Bucket |\*  |string  | s3 bucket
|Region |\*  |string  | s3 region
|FileName |\*  |string  | the name of the uploaded file
|StorageInfo |  |string  |base64 string. If it is a local service, this parameter can be omitted.


**Example of Response**

```JSON
{
	"ErrorCode":1,
	"ErrorMessage":"work not finish",
	"TimeWait": "1000",
}
```

**Parameters of Response**

|Parameter|Type|Description|
|:-----  |:-----|----- |
|ErrorCode |number  | `1` means task is processing, `5` means ready to upload |
|ErrorMessage |string  | 
|TimeWait |number  | the upload wait time ms
