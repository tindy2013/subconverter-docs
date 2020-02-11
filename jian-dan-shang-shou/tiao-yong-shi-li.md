# 调用示例

{% tabs %}
{% tab title="处理单份订阅" %}
如果你需要将一份 Surge 订阅转换成 Clash 的订阅, 可以按以下操作：

```text
有以下一个订阅，且想转换成 Clash 的订阅:
1. https://dler.cloud/subscribe/ABCDE?surge=ss

首先将订阅通过 URLEncode 后可以得到:
https%3A%2F%2Fdler.cloud%2Fsubscribe%2FABCDE%3Fsurge%3Dss

然后将想要的 %TARGET% (即 clash) 和上一步所得到的 %URL% 填入调用地址中:
http://127.0.0.1:25500/sub?target=clash&url=https%3A%2F%2Fdler.cloud%2Fsubscribe%2FABCDE%3Fsurge%3Dss

最后将该链接填写至 Clash 的订阅处就大功告成了。
```
{% endtab %}

{% tab title="处理多份订阅" %}
如果你需要将多个订阅合成一份, 则要在上方所提及的 URLEncode 之前使用 '\|' 来分隔链接, 可以按以下操作：

```text
有以下两个订阅，且想合并转换成 Clash 的订阅:
1. https://dler.cloud/subscribe/ABCDE?clash=vmess
2. https://rich.cloud/subscribe/ABCDE?clash=vmess

首先使用 '|' 将两个订阅分隔开:
https://dler.cloud/subscribe/ABCDE?clash=vmess|https://rich.cloud/subscribe/ABCDE?clash=vmess

接着通过 URLEncode 后可以得到:
https%3A%2F%2Fdler.cloud%2Fsubscribe%2FABCDE%3Fclash%3Dvmess%7Chttps%3A%2F%2Frich.cloud%2Fsubscribe%2FABCDE%3Fclash%3Dvmess

然后将想要的 %TARGET% (即 clash) 和上一步所得到的 %URL% 填入调用地址中:
http://127.0.0.1:25500/sub?target=clash&url=https%3A%2F%2Fdler.cloud%2Fsubscribe%2FABCDE%3Fclash%3Dvmess%7Chttps%3A%2F%2Frich.cloud%2Fsubscribe%2FABCDE%3Fclash%3Dvmess

最后将该链接填写至 Clash 的订阅处就大功告成了。
```
{% endtab %}

{% tab title="处理单份链接" %}
如果你需要将自建的一条 SS 的 SIP002 链接转换成 Clash 的订阅, 可以按以下操作：

```text
有以下自建的一条 SS 的 SIP002 链接，且想转换成 Clash 的订阅:
1. ss://YWVzLTEyOC1nY206dGVzdA==@192.168.100.1:8888#Example1

首先将订阅通过 URLEncode 后可以得到:
ss%3A%2F%2FYWVzLTEyOC1nY206dGVzdA%3D%3D%40192%2E168%2E100%2E1%3A8888%23Example1

然后将想要的 %TARGET% (即 clash) 和上一步所得到的 %URL% 填入调用地址中:
http://127.0.0.1:25500/sub?target=clash&url=ss%3A%2F%2FYWVzLTEyOC1nY206dGVzdA%3D%3D%40192%2E168%2E100%2E1%3A8888%23Example1

最后将该链接填写至 Clash 的订阅处就大功告成了。
```
{% endtab %}

{% tab title="处理多份链接" %}
如果你需要将多个链接合成一份, 则要在上方所提及的 URLEncode 之前使用 '\|' 来分隔链接, 可以按以下操作：

```text
有以下两个链接，且想合并转换成 Clash 的订阅:
1. ss://YWVzLTEyOC1nY206dGVzdA==@192.168.100.1:8888#Example1
2. vmess://eyJ2IjoiMiIsInBzIjoidm1lc3MtcHJveHkxIiwiYWRkIjoiZXhhbXBsZS5jb20iLCJwb3J0Ijo0NDMsInR5cGUiOiIiLCJpZCI6IjEyMzQ1Njc4LWFiY2QtMTIzNC0xMjM0LTQ3ZmZjYTBjZTIyOSIsImFpZCI6NDQzLCJuZXQiOiJ3cyIsInBhdGgiOiIvdjIiLCJob3N0IjoiZXhhbXBsZS5jb20iLCJ0bHMiOiJ0bHMifQ==

首先使用 '|' 将两个链接分隔开:
ss://YWVzLTEyOC1nY206dGVzdA==@192.168.100.1:8888#Example1|vmess://eyJ2IjoiMiIsInBzIjoidm1lc3MtcHJveHkxIiwiYWRkIjoiZXhhbXBsZS5jb20iLCJwb3J0Ijo0NDMsInR5cGUiOiIiLCJpZCI6IjEyMzQ1Njc4LWFiY2QtMTIzNC0xMjM0LTQ3ZmZjYTBjZTIyOSIsImFpZCI6NDQzLCJuZXQiOiJ3cyIsInBhdGgiOiIvdjIiLCJob3N0IjoiZXhhbXBsZS5jb20iLCJ0bHMiOiJ0bHMifQ==

接着通过 URLEncode 后可以得到:
ss%3A%2F%2FYWVzLTEyOC1nY206dGVzdA%3D%3D%40192%2E168%2E100%2E1%3A8888%23Example1%7Cvmess%3A%2F%2FeyJ2IjoiMiIsInBzIjoidm1lc3MtcHJveHkxIiwiYWRkIjoiZXhhbXBsZS5jb20iLCJwb3J0Ijo0NDMsInR5cGUiOiIiLCJpZCI6IjEyMzQ1Njc4LWFiY2QtMTIzNC0xMjM0LTQ3ZmZjYTBjZTIyOSIsImFpZCI6NDQzLCJuZXQiOiJ3cyIsInBhdGgiOiIvdjIiLCJob3N0IjoiZXhhbXBsZS5jb20iLCJ0bHMiOiJ0bHMifQ%3D%3D

然后将想要的 %TARGET% (即 clash) 和上一步所得到的 %URL% 填入调用地址中:
http://127.0.0.1:25500/sub?target=clash&url=ss%3A%2F%2FYWVzLTEyOC1nY206dGVzdA%3D%3D%40192%2E168%2E100%2E1%3A8888%23Example1%7Cvmess%3A%2F%2FeyJ2IjoiMiIsInBzIjoidm1lc3MtcHJveHkxIiwiYWRkIjoiZXhhbXBsZS5jb20iLCJwb3J0Ijo0NDMsInR5cGUiOiIiLCJpZCI6IjEyMzQ1Njc4LWFiY2QtMTIzNC0xMjM0LTQ3ZmZjYTBjZTIyOSIsImFpZCI6NDQzLCJuZXQiOiJ3cyIsInBhdGgiOiIvdjIiLCJob3N0IjoiZXhhbXBsZS5jb20iLCJ0bHMiOiJ0bHMifQ%3D%3D

最后将该链接填写至 Clash 的订阅处就大功告成了。
```
{% endtab %}
{% endtabs %}

