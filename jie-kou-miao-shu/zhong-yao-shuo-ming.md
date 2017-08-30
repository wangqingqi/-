#### **业务描述** {#id-运单状态订阅-5.1.1.业务描述}

订阅方通过订阅接口格式向中通系统订阅所关注的运单号信息,中通系统接收订阅信息后同步返回处理成功或者失败.

---

#### **字段含义** {#id-运单状态订阅-5.1.2.字段含义}

| **参数名称** | **用途** |
| :--- | :--- |
| data | 消息内容 |
| data\_digest | 消息签名 |
| msg\_type | 消息类型\(SUB 订阅\) |
| company\_id | 合作商ID |

**data 消息体结构说明**

| 参数 | **类型** | **参数说明** | **是否可空** |
| :--- | :--- | :--- | :--- |
| id | String\(50\) | 订阅ID,唯一 | N |
| billCode | String\(32\) | 运单号 | N |
| pushCategory | String\(32\) | callBack（固定,注意大小写） | N |
| pushTarget | String\(256\) | 商家接口地址 | N |
| pushTime | Number | 1 | Y |
| subscriptionCategory | Number | 1-收件、2-发件、4-到件、8-派送、16-签收、32-问题件订阅多种状态 状态码相加即可如全量订阅则为 63 | N |
| createBy | String\(32\) | 订阅人（测试环境统一为：test，生产环境再联调通过后分配。） | N |

---

#### **请求格式** {#id-运单状态订阅-5.1.3.请求格式}



`[{`

`     "id": "1111111111",`

`     "billCode": "700000000",`

`     "pushCategory": "callBack",`

`     "pushTarget": "122.138.1.13:8080/shangjia/traces",`

`     "pushTime": 1,`

`     "subscriptionCategory": 63,`

` "createBy": "XXX",`

`},{`

`     "id": "1111111112",`

`     "billCode": "7000000001",`

`     "pushCategory": "callBack",`

`     "pushTarget": "122.138.1.13:8080/shangjia/traces",`

`    "pushTime": 1,`

`    "subscriptionCategory": 63,`

`  "createBy": "XXX"`

`},{`

`    "id": "1111111113",`

`     "billCode": "7000000002",`

`     "pushCategory": "callBack",`

`     "pushTarget": "122.138.1.13:8080/shangjia/traces",`

`     "pushTime": 1,`

`     "subscriptionCategory": 63,`

` "createBy": "XXX"`

`}]`





