**Brief Description** 

- get the thumbnail of the hi-res media

**Request URL** 
- `https://resource.tvunetworks.com:10600/api/resource/v1/i/getthumbnail`
  
**Request Method**
- POST 

**Request Example**

```JSON
{
    "_ServiceName": "resourceservice",
    "_UrlPath": "getthumbnail",
    "_Version":1,

	"StartPos": 1562253612833,
	"StartTime": "00:13:12",
	"LivePath": "mp4/55524C2004E/55524C2041268-6bdb82b53e0a/1/stream.mpd",

}

```

**Parameter** 

|Parameter|Required|Type|Description|
|:----    |:---|:----- |-----   |
|StartPos |\*  |number | in millisecond. Get from Search API.
|StartTime |\*  |string | in millisecond. Relative time of mark.
|LivePath |\*  |string | Get from Search API 
|SessionId |  |string  | for auth

**Example of Response**

```JSON
{
	"ErrorCode":0,
	"ErrorMessage":"Success",
	"ImagePath":"/4B999DC458FBC4C80000000000000002/4B999DC458FBC4C80000000000000002_20200316-02-21-49_4B999DC458FBC4C80000000000000002_FE31F2B2CEAA2E63_4b13335c-2fc1-45ea-9cb5-f92065a26e91_1584973791094_7170000.jpg",
}
```

**Parameters of Response**

|Parameter|Type|Description|
|:-----  |:-----|----- |
|ErrorCode |number  | `1` means task is processing, `5` means ready to download |
|ErrorMessage |string  | |
|ImagePath |string  | The first frame of the exported clip |
