## PutRestoreResult

**简要描述：** 

- PutRestoreResult

**请求URL：** 
- ` https://ip:port/PutRestoreResult `

**请求方式：**
- post 


 **请求参数示例**

``` 
{
  "code":0,
  "message":"succ",
  "type":0,
  "task_id":"xxxxxxxx",
  "file_dir":"",
  "file_list_status":[
    {
      "file_name":"",
      "file_code":0
    },
	...
  ]
}
```



**参数：** 

|参数名|是否必选|类型|说明|
|:----    |:---|:----- |-----   |
|code |必选  |int |作业错误码 |
|message |必选  |string |作业错误信息 |
|type |必选  |int |操作类型 0：表示测试网络，1：表示真正发送结果 |
|task_id |必选  |string |任务Id |
|file_dir |必选  |string |s3文件所在目录 |
|file_name |必选  |string |文件名称 |
|file_code |必选  |int |文件处理状态 |

 **返回示例**

``` 
{
  "code":0,
  "message":"succ"
}
```

 **返回参数说明** 

|参数名|类型|说明|
|:-----  |:-----|----- |
|code |int  |错误码
|message |string  |错误信息

 **备注** 

- 此接口是回调接口，实现需要客户端实现

  ​      
