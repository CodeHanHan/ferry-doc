# ping接口文档

## 1. ping接口

接口描述：查验服务是否正常启动

接口地址：http://101.43.99.162:10001/api/v1/ping/create

请求类型： POST

请求参数：  

| 编号 | 名称    | 类型   | 是否必须 | 描述                 |
| ---- | ------- | ------ | -------- | -------------------- |
| 1    | message | string | 是       | 要发送给服务器的信息 |

响应参数  

| 编号 | 名称  | 类型   | 描述             |
| ---- | ----- | ------ | ---------------- |
| 1    | reply | string | 服务器返回的消息 |

请求示例：
```sh
curl -X 'POST' \
  'http://localhost:10000/api/v1/ping/create?message=hello' \
  -H 'accept: application/json' \
  -d ''
```

请求url
```
http://localhost:10000/api/v1/ping/create?message=hello
```

响应示例：
```
hello, too
```    

## 2. 查询ping记录
接口描述：分页查询之前发送ping的记录

接口地址：http://101.43.99.162:10001/api/v1/ping/list

请求类型: GET

请求参数：  

| 编号 | 名称   | 类型 | 是否必须 | 描述     |
| ---- | ------ | ---- | -------- | -------- |
| 1    | offset | int  | 是       | 偏移量   |
| 2    | limit  | int  | 是       | 分页大小 |

请求示例：
```sh
curl -X 'GET' \
  'http://localhost:10000/api/v1/ping/list?offset=1&limit=10' \
  -H 'accept: application/json'
```

请求url
```
http://localhost:10000/api/v1/ping/list?offset=1&limit=10
```

响应参数：  

| 编号 | 名称       | 类型      | 描述             |
| ---- | ---------- | --------- | ---------------- |
| 1    | records    | object    | ping_record列表  |
| 1.1  | pingID     | string    | ping消息ID       |
| 1.2  | Message    | string    | 服务器收到的消息 |
| 1.3  | Reply      | string    | 服务器返回的消息 |
| 1.4  | CreateTime | timestamp | 创建时间         |


响应示例：
```json
[
  {
    "PingID": "bfb9994db194403ba2cc34ad2d716f9e",
    "Message": "hello",
    "Reply": "hello, too",
    "CreateTime": "2021-12-11T04:36:46Z"
  }
]
```

