### **业务描述**

当商家订阅的单号产生新的物流详情时，中通会主动推送一条消息至商家提供的接口上。消息签名的校验参考订阅接口。测试的密钥为：123456

---

### **字段含义**

| **参数名称** | **用途** |
| :--- | :--- |
| data | 消息内容 |
| data\_digest | 消息签名 |
| msg\_type | 消息类型\(Traces\) |
| company\_id | 合作商ID（为调用订阅接口时传递的createBy） |

**data消息体结构说明**

| **参数名称** | **用途** |
| :--- | :--- |
| billCode | 运单号 |
| scanType | 扫描类型，事件/操作，详情参见附录[ scanType 编码规范](https://wangqingqi.gitbooks.io/testbook/content/fu-jian.html) |
| scanSite | 扫描网点 |
| scanCity | 扫描城市 |
| scanDate | 扫描时间（yyyy-MM-dd HH:mm:ss） |
| desc | 物流信息描述 |
| contacts | 收\派件业务，签收客户名 |
| contactsTel | 收\派件业务电话 |
| remark1 | 值为\[THIRD\_PARTY\_SIGN\] 时，为代理点信息 |
| remark2 | 备注信息，后期约定，未用到的可以忽略 |
| remark3 | 同上 |
| remark4 | 同上 |
| remark5 | 同上 |
| remark6 | 同上 |

---

### **请求格式**

```
 {
    "billCode": "532246117447",
    "contacts": "签收:同事",
    "contactsTel": "",
    "desc": "在2016-09-07 16:34:16签收,详情可登录www.zto.com查看,感谢使用中通快递",
    "scanCity": "永州市",
    "scanDate": "2016-09-07 16:34:16",
    "scanSite": "永州",
    "scanType": "SIGN",
    "remark1": "",
    "remark2": "",
    "remark3": "",
    "remark4": "",
    "remark5": "",
    "remark6": ""
}
```

### **返回格式**

```
 {
    "message": "",
    "result": "success",
    "status": true,
    "statusCode": "0"
}
```

对接方返回格式需严格按照中通定义的返回格式处理返回报文，如格式不正确，会导致数据推送不全的情况产生。

