## 功能描述

UpdateSpeechQueue 接口用于更新语音识别队列。

## 请求

#### 请求示例

```plaintext
PUT /asrqueue/p8eb46b8cc1a94bc09512d16c5c4f4d3a HTTP/1.1
Host: <BucketName-APPID>.ci.<Region>.myqcloud.com
Date: <GMT Date>
Authorization: <Auth String>
Content-Length: <length>
Content-Type: application/xml

<body>
```

>?
- 此接口 Host 需要填写数据万象域名。
- Authorization: Auth String（详情请参见 [请求签名](https://cloud.tencent.com/document/product/436/7778) 文档）。

#### 请求头

此接口仅使用公共请求头部，详情请参见数据万象 [公共请求头部](https://cloud.tencent.com/document/product/460/42865) 文档。

#### 请求体

该请求操作的实现需要有以下请求体。

```plaintext
<Request>
    <Name>Queue Name</Name>
    <QueueID></QueueID>
    <State></State>
    <NotifyConfig>
        <Type></Type>
        <Url></Url>
        <Event></Event>
    </NotifyConfig>
</Request>
```

具体数据描述如下：

| 节点名称（关键字） | 父节点 | 描述           | 类型      | 是否必选 |
| :----------------- | :----- | :------------- | :-------- | :------- |
| Request            | 无     | 保存请求的容器 | Container | 是       |

Container 类型 Request 的具体数据描述如下：

| 节点名称（关键字） | 父节点  | 描述     | 类型      | 是否必选 | 限制                                                         |
| :----------------- | :------ | :------- | :-------- | :------- | :----------------------------------------------------------- |
| Name               | Request | 模板名称 | String    | 是       | 长度限制100字符                                              |
| QueueID            | Request | 管道 ID  | String    | 是       | -                                                            |
| State              | Request | 管道状态 | String    | 是       | 1. Active 表示管道内的作业会被语音识别服务调度执行 <br>2. Paused 表示管道暂停，作业不再会被语音识别服务调度执行，管道内的所有作业状态维持在已提交状态，已经处于识别中的任务将继续执行，不受影响 |
| NotifyConfig       | Request | 通知渠道 | Container | 是       | 第三方回调 Url                                               |

Container 类型 NotifyConfig 的具体数据描述如下：

| 节点名称（关键字） | 父节点               | 描述                    | 类型   | 是否必选 | 限制            |
| :----------------- | :------------------- | :---------------------- | :----- | :------- | :-------------- |
| Url                | Request.NotifyConfig | 回调配置                | String | 否       | 长度限制100字符 |
| Type               | Request.NotifyConfig | 回调类型，普通回调：Url | String | 否       | 长度限制100字符 |
| Event              | Request.NotifyConfig | 回调事件                | String | 否       | 长度限制100字符 |
| State              | Request.NotifyConfig | 回调开关，Off，On       | String | 否       | 长度限制100字符 |

## 响应

#### 响应头

此接口仅返回公共响应头部，详情请参见数据万象 [公共响应头部](https://cloud.tencent.com/document/product/460/42866) 文档。

#### 响应体

该响应体返回为 **application/xml** 数据，包含完整节点数据的内容展示如下：

```plaintext
<Response>
    <RequestId>NTk0MjdmODlfMjQ4OGY3XzYzYzhf****</RequestId>
    <Queue>
        <QueueId></QueueId>
        <Name></Name>
        <State>Active</State>
        <NotifyConfig>
            <Url>mts-topic-1</Url>
            <Type></Type>
            <Event></Event>
        </NotifyConfig>
        <CreateTime></CreateTime>
        <UpdateTime></UpdateTime>
    </Queue>
</Response>
```

具体的数据内容如下：

| 节点名称（关键字） | 父节点 | 描述           | 类型      |
| :----------------- | :----- | :------------- | :-------- |
| Response           | 无     | 保存结果的容器 | Container |

Container 节点 Response 的内容：

| 节点名称（关键字） | 父节点   | 描述                                                         | 类型      |
| :----------------- | :------- | :----------------------------------------------------------- | :-------- |
| RequestId          | Response | 请求的唯一 ID                                                | String    |
| Queue              | Response | 队列信息，详情同 DescribeSpeechQueues 接口中的 Response.QueueList 节点 | Container |

#### 错误码

该请求操作无特殊错误信息，常见的错误信息请参见数据万象 [错误码](https://cloud.tencent.com/document/product/460/42867) 文档。
