# 调用示例

有订阅 `https://dler.cloud/subscribe/ABCDE?clash=vmess`，想转换成 Surge 4 的订阅，且需要开启 TFO 和 UDP 顺便再给节点名加上 EMOJI 同时排除掉订阅中显示流量和官网的节点（节点名为"剩余流量：1024G"，"官网地址：dler.cloud"）

首先，确认需要用到的参数： 

* target=surge&ver=4 
* tfo=true
* udp=true 
* emoji=true
* exclude=\(流量\|官网\)
* url=[https://dler.cloud/subscribe/ABCDE?clash=vmess](https://dler.cloud/subscribe/ABCDE?clash=vmess)

然后，将需要 URLEncode 的部分进行处理： 

* exclude=%28%E6%B5%81%E9%87%8F%7C%E5%AE%98%E7%BD%91%29 
* url=https%3A%2F%2Fdler.cloud%2Fsubscribe%2FABCDE%3Fclash%3Dvmess

接着，将所有元素用 `&` 进行拼接：  
[http://127.0.0.1:25500/sub?target=surge&ver=4&tfo=true&udp=true&emoji=true&exclude=%28%E6%B5%81%E9%87%8F%7C%E5%AE%98%E7%BD%91%29&url=https%3A%2F%2Fdler.cloud%2Fsubscribe%2FABCDE%3Fclash%3Dvmess](http://127.0.0.1:25500/sub?target=surge&ver=4&tfo=true&udp=true&emoji=true&exclude=%28%E6%B5%81%E9%87%8F%7C%E5%AE%98%E7%BD%91%29&url=https%3A%2F%2Fdler.cloud%2Fsubscribe%2FABCDE%3Fclash%3Dvmess)

最后，将该链接填写至 Surge 的订阅处就大功告成了。

