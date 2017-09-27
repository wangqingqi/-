# 

测试

[http://58.40.16.125:9001/](http://58.40.16.125:9001/)zto/api\_utf8/subBillLog\(外网\)

正式

UTF-8:[http://japi.zto.cn/zto/api\_utf8/subBillLog](http://japi.zto.cn/zto/api_utf8/subBillLog)

### 模拟CURL：

```js
curl -X POST \
  http://10.9.20.34:9001/zto/api_utf8/subBillLog \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 532698be-96e4-4fcd-c730-68bfd9bebe6f' \
  -F company_id=test \
  -F 'data=[{"id":"7f93ef16-8251-4c34-a5fa-bc4a831d92d9","billCode":"680000000000","pushCategory":"callBack","pushTarget":"http://192.168.1.1/pushdata/callback","pushTime":1,"subscriptionCategory":31,"subscriptionSource":"order","createBy":"test","key":"ad99bb5f7d0ce8ac0f583a0f5fd494c6","sitecode":"02183","pushmobile":"18351186985","contents":"desc","type":"0","partnerid":"1000071435","isEnble":"1"}]' \
  -F msg_type=SUB \
  -F data_digest=WwnqBWQLBJAuBu6NgWnSTg==
```



