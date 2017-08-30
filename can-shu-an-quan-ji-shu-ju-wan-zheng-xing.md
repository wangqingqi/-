### **参数定义** {#id-运单状态订阅-4.1.参数定义}

| **参数名称** | **用途** |
| :--- | :--- |
| data | 消息内容 |
| data\_digest | 消息签名 |
| msg\_type | 消息类型\(SUB 订阅,         CANCEL 取消,SUB\_BILL 订阅并返回物流信息\) |
| company\_id | 合作商ID |

---

### **安全及数据完整性** {#id-运单状态订阅-4.2.安全及数据完整性}

1、中通支持的消息接收方式为 HTTP POST 和 GET；如 果 以 HTTP POST 方式发送，请求方法的编码格式：“application/x-www-form-urlencoded; charset=GBK”；如果以GET方式发送，请将参数链接在 URL 的后面；

2、 在POST 时用“data”字段表示要发送的 JSON 内容；

3、在POST时用“data\_digest”字段进行签名验证。签名使用MD5方式，对 data的内容进行签名。原理为：通知内容JSON+key\(联调时分配\)，然后进行 MD5，转换为Base64 字符串。

详细解释如下：

u 假设 JSON内容为： JSON， key为 123456那么要签名的内容为JSON123456（默认 GBK 编码），经过 md5 和base64 后的内容就为 yhmQhg2ZiWCMc91nH0/vsg==

最终要发送的数据为

data=JSON&data\_digest=yhmQhg2ZiWCMc91nH0/vsg==& msg\_type =?company\_id=?

4、要求合作商收到消息后，一定要验证数据是否完整及正确；

5、合作商收到消息后，内容不正确？请检查字符集是否为 GBK/UTF-8；所有的参数都是通过URL 编码传送的，符合 HTTP 协议，注意客户端是否解码正确，有些控件已经自带 URL 解码功能，请开发人员注意。

---

### **数据发送和接收** {#id-运单状态订阅-4.3.数据发送和接收}

数据发送流程：压缩（可选）-&gt; BASE64 编码（可选）-&gt; 数字签名-&gt; 发送；



数据接收流程：接收-&gt; 数字签名校验-&gt; BASE64 解码（可选）-&gt; 解压（可选）-&gt;处理；

