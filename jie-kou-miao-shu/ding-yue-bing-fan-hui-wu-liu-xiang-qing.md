#### 业务描述 {#id-运单状态订阅-5.3.1业务描述}

订阅方通过订阅接口格式向中通系统订阅所关注的运单号信息,中通系统接收订阅信息并返回该该运单的物流流转信息，为了提高接口的响应时间，该接口设定每次最多接受5条单号信息。超过5条，将会请求失败。

---

#### 字段含义 {#id-运单状态订阅-5.3.2字段含义}

| **参数名称** | **用途** |
| :--- | :--- |
| data | 消息内容 |
| data\_digest | 消息签名 |
| msg\_type | 消息类型\(  SUB\_BILL\) |
| company\_id | 合作商ID |

**data消息体结构说明**

| **参数** | **类型** | **参数说明** | **是否可空** |
| :--- | :--- | :--- | :--- |
| id | String\(50\) | 订阅ID,唯一 | N |
| billCode | String\(32\) | 运单号 | N |
| pushCategory | String\(32\) | callBack（固定,注意大小写） | N |
| pushTarget | String\(256\) | 商家接口地址 | N |
| pushTime | Number | 1 | Y |
| subscriptionCategory | Number | 1-收件、2-发件、4-到件、8-派送、16-签收、32-问题件订阅多种状态 状态码相加即可如全量订阅则为 63 | N |
| createBy | String\(32\) | 订阅人（测试环境统一为：test，生产环境再联调通过后分配。） | N  |

---

#### **请求格式** {#id-运单状态订阅-5.2.3.请求格式}

```
[
       {
        "id": "3333333333",
        "billCode": "680000000004",
        "pushCategory": "callBack",
        "pushTarget": "122.138.1.13:8080/shangjia/traces"
    }
]

```

#### **返回格式** {#id-运单状态订阅-5.2.4.返回格式}

**·**正确返回

```
[
     {
        "id": "51d3af44-e360-4f37-8ce2-139c059bdd60",
        "remark": "订阅成功",
        "status": true,
        "traces": "{\"billCode\":\"680000000004\",\"status\":0,\"traces\":[{\"country\":\"China\",\"desc\":\"[上海市] 快件已到达[上海],业务员易水清正在第1次派件 电话:18516090700 请保持电话畅通、耐心等待\",\"extend\":\"             {\\\"optReasonEn\\\":\\\"Waiting for physical delivery.\\\",\\\"dispCount\\\":1,\\\"dispNoCome\\\":true}\",\"operateUser\":\"易水清\",\"operateUserPhone\":\"18516090700\",\"preOrNextSite\":null,\"scanDate\":\"2017-03-03 22:54:17\",\"scanSite\":{\"city\":\"上海市\",\"code\":\"02100\",\"isCenter\":\"T\",\"name\":\"上海\",\"phone\":\"95311\",\"prov\":\"上海\"},\"scanType\":\"派件\",\"signMan\":\"\"},{\"country\":\"China\",\"desc\":\"[上海市] [上海总部财务]的派件已签收 感谢使用中通快递,期待再次为您服务!\",\"extend\":\"{\\\"optReasonEn\\\":\\\"International delivery.\\\"}\",\"operateUser\":\"\",\"operateUserPhone\":\"\",\"preOrNextSite\":null,\"scanDate\":\"2017-03-27 10:05:30\",\"scanSite\":{\"city\":\"上海市\",\"code\":\"00088\",\"isCenter\":\"F\",\"name\":\"上海总部财务\",\"phone\":\"\",\"prov\":\"上海\"},\"scanType\":\"签收\",\"signMan\":\"拍照签收\"}]}"
        }
]

```

**·**错误返回

```
{
    "status": false,
    "statusCode": "S02",
    "message": "不合法的签名",
    "result": null
}
```



