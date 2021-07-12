


**Brief Description** 

- rename the exported file

**Request URL** 
- `https://resource.tvunetworks.com:10600/rename`
  
**Request Method**
- POST 

**Request Example**

```JSON
{
	"PeerId": "4D7446C8141EE167",
	"LivePath": "mp4/55524C2004E/55524C2041268-6bdb82b53e0a/1/stream.mpd",
	"OldFileName": "04-60C262253621833_0.0993375889",
	"NewFileName": "new.0993375889",
	"SessionId": "2A39603DDB0F47CFB32E96C8366084AE",
	"storage_info" : "BASE64 string", // If it is a local service, this parameter can be omitted.
	"userid": "dev@tvunetworks.com",
}


```

**Parameter** 

|Parameter|Required|Type|Description|
|:----    |:---|:----- |-----   |
|OldFileName |  |string | the old file name
|NewFileName |  |string | the new file name
|SessionId |  |string  | for auth
|storage_info |  |string  |base64 string. If it is a local service, this parameter can be omitted.
|userid |  |string  |the id of user

**Example of Response**

```JSON
{
	"ErrorCode":0,
	"ErrorMessage":"Success",
	"NewName" : "new.0993375889"
}
```
```

 ```JSON
{
	"ErrorCode":-1,
	"ErrorMessage":"not such dir"
}
 ```

**Parameters of Response**

|Parameter|Type|Description|
|:-----  |:-----|----- |
|ErrorCode |number  | `0` means success, other means failed |
|ErrorMessage |string  | Failure details |
|NewName       |string | the name after rename. (Fields only for success)


**Comment** 

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