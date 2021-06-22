> JustinChen@TVU 2020-01-29

**Brief Description** 

- delete the exported file in service

**Request URL** 
- `https://resource.tvunetworks.com:443/resource/v1/delete`
  
**Request Method**
- POST 

**Request Example**

```JSON
{
	"file_name": "04-AFD5282F4F6A36F0-1D82773F668371E9_1561720752604_1561720997604_0.2370001854.ts",
	"uid": "mp4/1715F514A891B80/20200106-19-24-36_1715F514A891B825/1/stream.mpd"
}
```

**Parameter** 

|Parameter|Required|Type|Description|
|:----    |:---|:----- |-----   |
|file_name |\*  |string | Get from `v1/export` |
|uid |\*  |string | |

**Example of Response**

```JSON
{
	"error_code": 0,
	"error_message": "success",
}
```


**Parameters of Response** 

|Parameter|Type|Description|
|:-----  |:-----|----- |

**Comment** 

- 
        
