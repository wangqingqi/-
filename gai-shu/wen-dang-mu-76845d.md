### 2.1. **文档目的** {#id-运单状态订阅-2.1.文档目的}

本文档主要规范运单的跟踪日志订阅 取消订阅 并在产生物流信息后主动推送物流信息到订阅方提供的接口上，需要订阅方根据该文档开发一个接受消息的接口。

每一个订阅方都有唯一的订阅标识,这是以后双方平台互相识别的依据

### 2.2. **名词说明** {#id-运单状态订阅-2.2.名词说明}

订阅方：订阅运单日志的合作方\(商家\)。

订阅：订阅方订阅所关注的单号。

取消：订阅方取消所关注的单号。

推送：中通系统产生新的单号物流信息,推送给订阅方。

问题件：是指快件运输过程中出现异常的情况，如快件丢失、延误，以及客户拒签、无法联系导收件人等产生的一系列问题的统称。

![](http://wiki.dev.ztosys.com/download/attachments/2983665/3Y%242B_GI1OSRL6~K%2909%60X_I.png?version=1&modificationDate=1494398598000&api=v2)

### 2.3. **重要说明** {#id-运单状态订阅-2.3.重要说明}

1、中通官网的问题件数据会在正常签收后取消展示。

2、该文档提供的推送功能，推送的数据为实时的增量数据，即当订阅的单号产生物流信息后，会立即推送到订阅方。如果推送失败后，会再次进行重推，最多推送6次。（含第一次失败推送）。但仍会有存在物流轨迹缺失的情况，所以订阅接口不能完全替代快件跟踪查询接口。对接方可进行自身业务，同时使用快件跟踪接口和订阅接口进行完整的物流轨迹补全的工作。

3、商家提供的回调地址请求的响应耗时控制在1000ms以内，中通对接口超时时间设置为1500ms。

4、订阅接口和回调推送使用的key 不相同，注意，订阅时使用createBy字段请不要使用开放平台申请的company\_id。

**例如：**

**订阅接口：company\_id=zto,key=123456,craate=test**

**回调接口：company\_id=test,key=789789**

5、测试订阅单号使用【680000000020】，该单号会每5分钟推送单号状态变更信息。该单号订阅状态只为测试使用，订阅信息只保留1天。（每日凌晨会清除该单号的所有的订阅信息）





