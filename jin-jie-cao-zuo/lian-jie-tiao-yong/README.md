# 链接调用

## 调用地址

```text
http://127.0.0.1:25500/sub?target=%TARGET%&url=%URL%&emoji=%EMOJI%····
```

## 调用说明

| 调用参数 | 必要性 | 示例 | 解释 |
| :--- | :---: | :--- | :--- |
| target | 必要 | surge&ver=4 | 指想要生成的配置类型，详见上方 [支持类型]() 中的参数 |
| url | 可选 | https%3A%2F%2Fwww.xxx.com | 指机场所提供的订阅链接，需要经过 [URLEncode](https://www.urlencoder.org/) 处理，**可选的前提是在 `default_url` 中进行指定** |
| config | 可选 | https%3A%2F%2Fwww.xxx.com | 指远程 `pref.ini` \(包含分组和规则部分\)，需要经过 [URLEncode](https://www.urlencoder.org/) 处理，可查看 [示例仓库](https://github.com/lzdnico/subconverteriniexample) 寻找灵感，默认加载本地设置文件 |
| upload | 可选 | true / false | 指将生成的订阅文件上传至 `Gist`，需要填写`gistconf.ini`，默认为 false \(即不上传\) |
| upload\_path | 可选 | MySS.yaml | 指将生成的订阅文件上传至 `Gist` 后的名称，需要经过 [URLEncode](https://www.urlencoder.org/) 处理 |
| emoji | 可选 | true / false | 指在节点名称前加入 Emoji，默认为 true |
| group | 可选 | MySS | 指设置该订阅的组名，多用于 SSD/SSR |
| tfo | 可选 | true / false | 指开启该订阅链接的 TCP Fast Open，默认为 false |
| udp | 可选 | true / false | 指开启该订阅链接的 UDP，默认为 false |
| scv | 可选 | true / false | 指关闭 TLS 节点的证书检查，默认为 false |
| list | 可选 | true / false | 指输出 Surge Node List 或者 Clash Proxy Provider 或者 解码后的 SIP002 |
| sort | 可选 | true / false | 指对输出的节点或策略组进行再次排序，默认为 false |
| include | 可选 | 详见下文中 `include_remarks` | 指仅保留匹配到的节点，支持正则匹配，需要经过 [URLEncode](https://www.urlencoder.org/) 处理，会覆盖配置文件里的设置 |
| exclude | 可选 | 详见下文中 `exclude_remarks` | 指排除匹配到的节点，支持正则匹配，需要经过 [URLEncode](https://www.urlencoder.org/) 处理，会覆盖配置文件里的设置 |

