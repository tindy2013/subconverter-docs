# \[common\] 部分

{% hint style="info" %}
该部分主要涉及到的内容为 **全局的节点排除或保留** 、**各配置文件的基础**

其他设置项目可以保持默认或者在知晓作用的前提下进行修改
{% endhint %}

##  **api\_mode**

> API 模式，设置为 true 以防止直接加载本地订阅或直接提供本地文件，多用于架设于服务器上

* 当值为 `false` 时, 每次更新配置都会读取 `pref.ini` ；
* 当值为 `true` 时则仅启动时读取。

## default\_url

> 无 %URL% 参数时，默认加载的订阅链接， **不需要 URLEncode**  
> 如果有多个链接，仍然需要使用 "\|" 分隔，支持`文件`/`url`

例如：`default_url=https://dler.cloud/subscribe/ABCDE?clash=vmess`

此时调用链接：`http://127.0.0.1:25500/sub?target=clash`   
等同于调用：`http://127.0.0.1:25500/sub?target=clash&url=https%3A%2F%2Fdler.cloud%2Fsubscribe%2FABCDE%3Fclash%3Dvmess`

## **exclude\_remarks**

> 排除匹配到的节点，支持正则匹配

例如：`exclude_remarks=(流量|时间|官网|产品)`

##  **include\_remarks**

> 仅包含匹配到的节点，支持正则匹配

例如：`exclude_remarks=(流量|时间|官网|产品)`

即为：仅包含订阅中节点名中包含 `流量、时间、官网、产品`  的节点

##  clash\_rule\_base

> 生成的 Clash 配置文件基础，支持 `本地文件` 和 `在线URL`

例如：

```text
clash_rule_base=clash.yaml # 加载本地的 clash.yaml 文件作为基础
clash_rule_base=https://raw.githubusercontent.com/ConnersHua/Profiles/master/Clash/Pro.yaml # 加载神机的 Github 中相关文件作为基础
```

## 

