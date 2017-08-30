#### **业务描述** {#id-运单状态订阅-5.2.1.业务描述}

订阅方通过取消接口格式向中通系统取消所关注的运单号信息,中通系统接收取消信息后同步返回处理成功或者失败.

---

#### **字段含义** {#id-运单状态订阅-5.2.2.字段含义}

| **参数名称** | **用途** |
| :--- | :--- |
| data | 消息内容 |
| data\_digest | 消息签名 |
| msg\_type | 消息类型\(  CANCEL 取消\) |
| company\_id | 合作商ID |

**data消息体结构说明**

| **参数** | **类型** | **参数说明** | **是否空** |
| :--- | :--- | :--- | :--- |
| id | String\(50\) | 订阅ID,唯一 | N |
| billCode | String\(32\) | 运单号 | N |
| pushCategory | String\(32\) | callBack | N |
| pushTarget | String\(256\) | 商家接口地址 | N |

---

#### **请求格式** {#id-运单状态订阅-5.2.3.请求格式}

```
[
    {
        "id": "1111111111",
       "billCode": "68121",
        "pushCategory": "callBack",
        "pushTarget": "122.138.1.13:8080/shangjia/traces"
    },
    {
        "id": "2222222222",
        "billCode": "68122",
        "pushCategory": "callBack",
        "pushTarget": "122.138.1.13:8080/shangjia/traces"
    },
    {
        "id": "3333333333",
        "billCode": "68123",
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
        "id": "1111111111",
        "remark": "取消订阅成功68121",
        "status": true
    },{
        "id": "2222222222",
        "remark": "取消订阅成功68122",
        "status": true
    },{
        "id": "3333333333",
        "remark": "取消订阅成功68123",
        "status": true
    },
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





