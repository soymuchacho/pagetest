# delete

**Brief Description** 

- delete img from service

**Request URL** 
- `https://mma.tvunetworks.com:8001/api/imgbed/v1/delete`

**Request Method**
- POST 

**Request Example**

```JSON
{
	"path":"55524C204558542000000174AF512E0B",
    "filename":"55524C204558542000000174AF512E0B_20200921-06-32-13_1600669949254_26000.jpg"
}
```

**Parameter** 

|Parameter|Required|Type|Description|
|:----    |:---|:----- |-----   |
|path |\*  |string | the path of upload file
|filename |\*  |string | the name of upload file

**Example of Response**

```JSON
{"errCode":0,"message":"ok"}
```

**Parameters of Response**

|Parameter|Type|Description|
|:-----  |:-----|----- |
|errCode |number  | `0` means delete successful
|message |string  | |
