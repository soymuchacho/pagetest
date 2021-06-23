# JustinChen@TVU 2020-01-29
# JustinChen@TVU 2020-03-06: add bucket 
# VesperGu@TVU 2020-05-12: add story 


**Brief Description** 

- get the first frame of the hi-res media file
- export hi-res media data

**Request URL** 
- `https://resource.tvunetworks.com:443/resource/v1/export`
  
**Request Method**
- POST 

**Request Example**

```JSON
{
	"start_position": 1578344206261,
	"mark_pos": "01:00",
	"duration": 128000,
	"uid": "mp4/1715F514A891B80A0000000000000002/20200106-19-24-36_1715F514A891B80A0000000000000002_938531849D11D411_a6aafadb-f126-4ae5-87c6-4ac6caba6325/1/stream.mpd",
	"media_type": "ts",
	"export_type": 0,
	"fetch_media": true,
	"file_name": "CNN4_RAL4_Feb.20200305191626537",
	"story": {
		"id": "1715F514A891B80A0000000000000002",
		"name": "20200106-19-24-36_1715F514A891B80A",
		"slug_info": "base64 string",
	},
}

```

**Parameter** 

|Parameter|Required|Type|Description|
|:----    |:---|:----- |-----   |
|start_position |\*  |number | in millisecond. Get from Search API 
|mark_pos |\*  |string | hh:mm:ss The starting position of the captured video, such as starting from 1 minute of the video, this parameter is 00:01:00.
|duration |\*  |number | in millisecond 
|uid |\*  |string | Get from Search API 
|media_type |  |string | `ts` or `mov`, the default value is `ts`. TODO
|export_type |  |number | `0` 、`1` or `2`, the default value is `0`, `1` is H.264, `2` is H.265.
|fetch_media |  |boolean | this field decides whether generate file or not when API is invoked. You can use `false` to get the thumbnail of the first frame. The default value is `false`
|file_name |  |string | the final file name
|story |  |pairs | "id" : "", "name" : "" , "slug_info" : "base64 string"

**Example of Response**

- "FetchMedia": false
```JSON
{
	"error_code": 0,
	"error_message": "success",
	"data": {
		"TimeWait": 0,
		"TotalTime": 15000, // in millisecond
		"ImagePath": "http://imagebed.tvunetworks.com:8001/1715F514A891B80A0000000000000002/1715F514A891B80A0000000000000002_20200106-19-24-36_1715F514A891B80A0000000000000002_938531849D11D411_a6aafadb-f126-4ae5-87c6-4ac6caba6325_1578344206261_128000.jpg",
		"S3Dir": "export"
	}
}
```

- "FetchMedia": true
```JSON
{
	"error_code": 1,
	"error_message": "Work is processing",
	"data": {
		"TimeWait": 2000,	// in millisecond
		"TotalTime": 15000, // in millisecond
		"ImagePath": "http://imagebed.tvunetworks.com:8001/1715F514A891B80A0000000000000002/1715F514A891B80A0000000000000002_20200106-19-24-36_1715F514A891B80A0000000000000002_938531849D11D411_a6aafadb-f126-4ae5-87c6-4ac6caba6325_1578344206261_128000.jpg",
		"VideoPath": "https://mma-video-archive.s3-us-west-1.amazonaws.com/export/CNN3_RAL3_JAN.20200129162015020.ts"
		"FileName":"CNN3_RAL3_JAN.20200129162015020.ts"
		"S3Dir": "export"
	}
}
```

```JSON
{
	"error_code": 5,
	"error_message": "Work Finish",
	"data": {
		"TimeWait": 0,
		"TotalTime": 15000, // in millisecond
		"ImagePath": "http://imagebed.tvunetworks.com:8001/1715F514A891B80A0000000000000002/1715F514A891B80A0000000000000002_20200106-19-24-36_1715F514A891B80A0000000000000002_938531849D11D411_a6aafadb-f126-4ae5-87c6-4ac6caba6325_1578344206261_128000.jpg",
		"VideoPath": "https://mma-video-archive.s3-us-west-1.amazonaws.com/export/CNN3_RAL3_JAN.20200129162015020.ts"
		"FileName":"CNN3_RAL3_JAN.20200129162015020.ts"
	}
}


slug base64 info looks like:
"slug_info" : {
    	"slug_id":"abcdefghig",
    	"slug_name":"test",
    	"slug_date":"",
    	"clipped_date":"",
    	"clip_length":""
	}
```

**Parameters of Response** 

|Parameter|Type|Description|
|:-----  |:-----|----- |
|error_code |number  | `1` means task is processing, `5` means ready to download |
|error_message |string  | |
|ImagePath |string  | The first frame of the exported file |
|VideoPath |string  | The location of exported media file |

**Comment** 

- The service limits the number of concurrent request for the limited harddisk I/O and network.
        
