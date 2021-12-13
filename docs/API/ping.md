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

| 编号 | 名称       | 类型      | 描述           |
| ---- | ---------- | --------- | -------------- |
| 1    | code       | int       | 状态码         |
| 2    | message    | string    | 响应信息       |
| 3    | detail     | object    | 响应详情       |
| 3.1  | PingID     | string    | ping记录值id   |
| 3.2  | Message    | string    | ping记录值信息 |
| 3.3  | Reply      | string    | ping记录值返回 |
| 3.4  | CreateTime | timestamp | 时间戳         |

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
```json
{
  "code": 200,
  "detail": {
    "PingID": "b44a3087ca644838bc56ae9317f2f99c",
    "Message": "hello",
    "Reply": "hello, too",
    "CreateTime": null
  },
  "message": "success"
}
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

请求url:
```
http://localhost:10000/api/v1/ping/list?offset=1&limit=10
```

响应参数：  

| 编号 | 名称       | 类型      | 描述             |
| ---- | ---------- | --------- | ---------------- |
| 1    | code       | int       | 状态码           |
| 2    | message    | string    | 状态码           |
| 3    | records    | object    | ping_record列表  |
| 3.1  | pingID     | string    | ping消息ID       |
| 3.2  | Message    | string    | 服务器收到的消息 |
| 3.3  | Reply      | string    | 服务器返回的消息 |
| 3.4  | CreateTime | timestamp | 创建时间         |


响应示例：
```json
{
  "code": 200,
  "detail": [
    {
      "PingID": "167c17cb9111447ba558dbe14f91f3e0",
      "Message": "aa",
      "Reply": "aa, too",
      "CreateTime": "2021-12-11T08:44:59Z"
    },
    {
      "PingID": "19af1f61d49045f5a37b9921269b86c4",
      "Message": "22",
      "Reply": "22, too",
      "CreateTime": "2021-12-11T11:30:18Z"
    },
  ],
  "message": "success"
}
```

