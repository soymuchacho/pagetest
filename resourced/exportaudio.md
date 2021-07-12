
    
**Brief description:** 

- User Registration Interface


**Request URL：** 
- `https://resource.tvunetworks.com:10600/exportaudio `
  
**Method:**
- POST 

**Parameter:** 

|Parameter name|Required|Type|Explain|
|:----    |:---|:----- |-----   |
|StartPos |\*  |number |audio start timestamp   |
|Duration |\*  |number |audio druation for ms   |
|PeerId     |-  |string | -    |
|LivePath|\*|string|export video file path|
|FileName|\*|string|exported audio file name |
|SessionId|\*|string|for auth|
|S3Region|-|string|s3 storage info|
|S3Bucket|-|string|s3 storage info|
|Uid|-|string|live uid|
|GroupId|\*|string|-|
|SampleRate|\*|string|audio stream info for speech server|
|Language|\*|string|transcriber language|
|UserId|\*|string|-|
|FileStartTimecode|\*|number|-|
|FileEndTimecode|\*|number|-|
|FileStartTimestamp|\*|number|-|
|FileEndTimestamp|\*|number|-|
|AudioPath|\*|string|audio network url|



 **Request example**

``` 
{
	"_ServiceName": "resourceservice",
	"_UrlPath": "exportaudio",
	"_Version":1,

	"StartPos": 1562253612833,
	"Duration": 9000,
	"PeerId": "4D7446C8141EE167",
	"LivePath": "mp4/55524C20455854200000016BB6AD004E/55524C20455854200000016BB6AD004E_4D7446C8141EE167_1562253592803_eb3f1268-6bdb-4884-8d76-2db582b53e0a/1/stream.mpd",
	"FileName": "1.flac",
	"SessionId": "2A39603DDB0F47CFB32E96C8366084AE",
	"S3Region": "ap-northeast-1",
	"S3Bucket": "imgbed",
	“Uid” : “test”,
	“GroupId”:”test”,
	“SampleRate”:120,
	“Language”:”en-Us”,
	“UserId”:”test@tvu”,
	“FileStartTimecode”：123,
	“FileEndTimecode”：123333，
	“FileStartTimestamp”:1562253612833,
	“FileEndTimestamp”:1562253612833,
	“AudioPath”:”http://1.2.3.4:90/xxx.xxx”
}

```

 **Return parameter description** 

|Parameter name|Type|Explain|
|:-----  |:-----|-----                           |
|ErrorCode |number   |  -|
|ErrorMessage|string|-|
|TimeWait|number|export to audio cost time|
 **Return example**
 ```
 {
	"ErrorCode": -1,
	"ErrorMessage": "open/data/www/ts/55524C204558542000000169F4B00E83/55524C204558542000000169F4B00E83_F6DDEE53075B1451_1562248888128_f261fd9b-6e22-4277-9949-ca5aa9429491/rec.index: no such file or directory",
	“TimeWait”:1000
}

 ```
