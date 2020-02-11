# index

在各种订阅格式之间进行转换的实用程序.

## 进阶用法

> 在不满足于本程序所提供的神机规则或者对应的分组时，可以考虑尝试进阶用法
>
> 即 对 `调用地址` 甚至程序目录下的 `pref.ini` 进行个性化的编辑以满足不同的需求

### 阅前提示

在进行下一步操作前，十分推荐您阅读以下内容：

1. 与 `pref.ini` 相关的：[INI 语法介绍](https://zh.wikipedia.org/wiki/INI%E6%96%87%E4%BB%B6)
2. 与 `Clash` 配置相关的： [YAML 语法介绍](https://zh.wikipedia.org/wiki/YAML#%E8%AA%9E%E6%B3%95)
3. 会经常涉及到的： [正则表达式入门](https://github.com/ziishaned/learn-regex/blob/master/translations/README-cn.md)
4. 当遇到问题需要提交 ISSUE 时的： [提问的智慧](https://github.com/ryanhanwu/How-To-Ask-Questions-The-Smart-Way/blob/master/README-zh_CN.md)

当您尝试进行进阶操作时，即默认您有相关的操作能力，本程序仅保证在默认配置文件下能够正常运行。

### 进阶地址

#### 调用地址 \(进阶\)

```text
http://127.0.0.1:25500/sub?target=%TARGET%&url=%URL%&emoji=%EMOJI%····
```

#### 调用说明 \(进阶\)

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

举个例子：

```text

```

### 配置文件

> 关于 subconverter 主程序目录中 `pref.ini` 文件的解释

由于此部分篇幅较长，点击下方条目即可展开详解：

 &gt; 该部分主要涉及到的内容为 \*\*全局的节点排除或保留\*\* 、\*\*各配置文件的基础\*\* &gt; &gt; 其他设置项目可以保持默认或者在知晓作用的前提下进行修改 1. \*\*api\_mode\*\* &gt; API 模式，设置为 true 以防止直接加载本地订阅或直接提供本地文件。（多用于架设于服务器上） - 当值为 \`false\` 时, 每次更新配置都会读取 \`pref.ini\` , 为 \`true\` 时则仅启动时读取。 1. \*\*default\_url\*\* &gt; 无 %URL% 参数时，默认加载的订阅链接， \*\*不需要 URLEncode\*\*。 如果有多个链接，仍然需要使用 "\|" 分隔，支持\`文件\`/\`url\` - 例如: \`\`\`ini default\_url='https://dler.cloud/subscribe/ABCDE?clash=vmess' \`\`\` - 解释： \`\`\`txt 此时订阅链接: http://127.0.0.1:25500/sub?target=clash 等同于: http://127.0.0.1:25500/sub?target=clash&url=https%3A%2F%2Fdler.cloud%2Fsubscribe%2FABCDE%3Fclash%3Dvmess \`\`\` 1. \*\*exclude\_remarks\*\* &gt; 排除匹配到的节点，支持正则匹配 - 例如: \`\`\`ini exclude\_remarks=\(流量\|时间\|官网\|产品\) \`\`\` 1. \*\*include\_remarks\*\* &gt; 仅保留匹配到的节点，支持正则匹配 - 例如: \`\`\`ini include\_remarks=\(? 生成的 Clash 配置文件基础。支持 \`本地文件\` 和 \`在线URL\` - 例如: \`\`\`ini clash\_rule\_base=clash.yaml \# 加载本地的 clash.yaml 文件作为基础 \# 或者 clash\_rule\_base=https://raw.githubusercontent.com/ConnersHua/Profiles/master/Clash/Pro.yaml \# 加载神机的 Github 中相关文件作为基础 \`\`\` 1. \*\*surge\_rule\_base\*\* &gt; 生成的 Surge 配置文件基础，用法同上 1. \*\*surfboard\_rule\_base\*\* &gt; 生成的 Surfboard 配置文件基础，用法同上 1. \*\*mellow\_rule\_base\*\* &gt; 生成的 Mellow 配置文件基础，用法同上 1. \*\*proxy\_ruleset\*\* &gt; 更新 RuleSet 时是否使用代理 &gt; &gt; 填写 \`NONE\` 或者空白禁用，或者填写 \`SYSTEM\` 使用系统代理 &gt; &gt; 也可填写如同 \`socks5://127.0.0.1:1080\` 的 HTTP 或 SOCKS 代理 - 例如: \`\`\`ini proxy\_ruleset=SYSTEM \# 使用系统代理 \# 或者 proxy\_ruleset=socks5://127.0.0.1:1080 \# 使用本地的 1080 端口进行 SOCKS5 代理 \`\`\` 1. \*\*proxy\_subscription\*\* &gt; 更新 原始订阅 时是否使用代理，用法同上 1. \*\*append\_proxy\_type\*\* &gt; 节点名称是否需要加入属性，设置为 true 时在节点名称前加入 \\[SS\\] \\[SSR\\] \\[VMess\\] 以作区别， &gt; &gt; 默认为 false - 例如（设置为 true时）： \`\`\`txt \[SS\] 香港中转 \[VMess\] 美国 GIA \`\`\`**\[node\_pref\] 部分** &gt; 该部分主要涉及到的内容为 \*\*开启节点的 UDP 及 TCP Fast Open\*\* 、\*\*节点的重命名\*\* 、\*\*重命名节点后的排序\*\* &gt; &gt; 相关设置项目建议保持默认或者在知晓作用的前提下进行修改 1. \*\*udp\_flag\*\* &gt; 为节点打开 UDP 模式，设置为 true 时打开，默认为 false - 当不清楚机场的设置时\*\*请勿调整此项\*\*。 1. \*\*tcp\_fast\_open\_flag\*\* &gt; 为节点打开 TFO \(TCP Fast Open\) 模式，设置为 true 时打开，默认为 false - 当不清楚机场的设置时\*\*请勿调整此项\*\*。 1. \*\*sort\_flag\*\* &gt; 对生成的订阅中的节点进行 A-Z 的排序，设置为 true 时打开，默认为 false 1. \*\*skip\_cert\_verify\_flag\*\* &gt; 关闭 TLS 节点的证书检查。设置为 true 时打开，默认为 false - \*\*请勿随意将此设置修改为 true\*\* 1. \*\*rename\_node\*\* &gt; 重命名节点，支持正则匹配 &gt; &gt; 使用方式：原始命名@重命名 - 例如: \`\`\`ini rename\_node=中国@中 rename\_node=\\(?\(\(x\|X\)?\(\d+\)\(\.?\d+\)?\)\(\(\s?倍率?:?\)\|\(x\|X\)\)\\)?@\(倍率:$1\) \`\`\`**\[managed\_config\] 部分** &gt; 该部分主要涉及到的内容为 \*\*订阅文件的更新地址\*\* 1. \*\*write\_managed\_config\*\* &gt; 是否将 '\#!MANAGED-CONFIG' 信息附加到 Surge 或 Surfboard 配置，设置为 true 时打开，默认为 true 1. \*\*managed\_config\_prefix\*\* &gt; 具体的 '\#!MANAGED-CONFIG' 信息，地址前缀不用添加 "/"。Surge 或 Surfboard 会向此地址发出更新请求 &gt; &gt; 局域网用户需要将此处改为本程序运行设备的局域网 IP - 例如: \`\`\`ini managed\_config\_prefix = http://192.168.1.5:25500 \`\`\`**\[surge\_external\_proxy\] 部分** &gt; 为 Surge 添加 SSR 的支持路径**\[emojis\] 部分** 1. \*\*add\_emoji\*\* &gt; 是否在节点名称前加入下面自定义的 Emoji，设置为 true 时打开，默认为 true 1. \*\*remove\_old\_emoji\*\* &gt; 是否移除原有订阅中存在的 Emoji，设置为 true 时打开，默认为 true 1. \*\*rule\*\* &gt; 在匹配到的节点前添加自定义 emojis，支持正则匹配 - 例如: \`\`\`ini rule=\(流量\|时间\|应急\),⌛time rule=\(美\|美国\|United States\),🇺🇸 \`\`\`**\[ruleset\] 部分** &gt; 如果你对原本订阅自带的规则不满意时，可以使用如下配置 1. \*\*enabled\*\* &gt; 启用自定义规则集的\*\*总开关\*\*，设置为 true 时打开，默认为 true 1. \*\*overwrite\_original\_rules\*\* &gt; 覆盖原有规则，即 \[common\] 中 xxx\_rule\_base 中的内容，设置为 true 时打开，默认为 false 1. \*\*update\_ruleset\_on\_request\*\* &gt; 根据请求执行规则集更新，设置为 true 时打开，默认为 false 1. \*\*surge\_ruleset\*\* &gt; 从本地或 url 获取规则片段 &gt; &gt; \[\] 前缀后的文字将被当作规则，而不是链接或路径，主要包含 \`\[\]GEOIP\` 和 \`\[\]MATCH\`\(等同于 \`\[\]FINAL\`\)。 - 例如： \`\`\`ini surge\_ruleset=🍎 苹果服务,https://raw.githubusercontent.com/ConnersHua/Profiles/master/Surge/Ruleset/Apple.list \# 表示引用 https://raw.githubusercontent.com/ConnersHua/Profiles/master/Surge/Ruleset/Apple.list 规则 \# 且将此规则指向 \[clash\_proxy\_group\] 所设置 🍎 苹果服务 策略组 surge\_ruleset=🎯 全球直连,rules/NobyDa/Surge/Download.list \# 表示引用本地 rules/NobyDa/Surge/Download.list 规则 \# 且将此规则指向 \[clash\_proxy\_group\] 所设置 🎯 全球直连 策略组 surge\_ruleset=🎯 全球直连,\[\]GEOIP,CN \# 表示引用 GEOIP 中关于中国的所有 IP \# 且将此规则指向 \[clash\_proxy\_group\] 所设置 🎯 全球直连 策略组 \`\`\`**\[clash\_proxy\_group\] 部分** &gt; 为 Clash 、Mellow 、Surge 以及 Surfboard 等程序创建策略组, 可用正则来筛选节点 &gt; &gt; \[\] 前缀后的文字将被当作引用策略组 \`\`\`ini custom\_proxy\_group=🍎 苹果服务\`url-test\`\(美国\|US\)\`http://www.gstatic.com/generate\_204\`300 \# 表示创建一个叫 🍎 苹果服务 的 url-test 策略组,并向其中添加名字含'美国','US'的节点，每隔300秒测试一次 custom\_proxy\_group=🇯🇵 日本延迟最低\`url-test\`\(日\|JP\)\`http://www.gstatic.com/generate\_204\`300 \# 表示创建一个叫 🇯🇵 日本延迟最低 的 url-test 策略组,并向其中添加名字含'日','JP'的节点，每隔300秒测试一次 custom\_proxy\_group=🇯🇵 JP\`select\`沪日\`日本\`\[\]🇯🇵 日本延迟最低 \# 表示创建一个叫 🇯🇵 JP 的 select 策略组,并向其中\*\*依次\*\*添加名字含'沪日','日本'的节点，以及引用上述所创建的 🇯🇵 日本延迟最低 策略组 \`\`\` - 还可使用一些特殊筛选条件 \`\`\`ini custom\_proxy\_group=g1\`select\`!!GROUPID=0 \# 指订阅链接中的第一条订阅 custom\_proxy\_group=g2\`select\`!!GROUPID=1 \# 指订阅链接中的第二条订阅 custom\_proxy\_group=v2ray\`select\`!!GROUP=V2RayProvider \# 指订阅链接中组名为 V2RayProvider 的节点 \`\`\` - 现在也可以使用双条件进行筛选 \`\`\`ini custom\_proxy\_group=g1hk\`select\`!!GROUPID=0!!\(HGC\|HKBN\|PCCW\|HKT\|hk\|港\) \# 订阅链接中的第一条订阅内名字含 HGC、HKBN、PCCW、HKT、hk、港 的节点 \`\`\`**\[server\] 部分** &gt; 此部分通常\*\*保持默认\*\*即可 1. \*\*listen\*\* &gt; 绑定到 Web 服务器的地址，将地址设为 0.0.0.0，则局域网内设备均可使用。 1. \*\*port\*\* &gt; 绑定到 Web 服务器地址的端口，默认为 25500

**\[advanced\] 部分** &gt; 此部分通常\*\*保持默认\*\*即可

### 外部配置

> 本部分用于 链接参数 `**&config=**`

将文件按照以下格式写好，上传至 Github Gist 或者 其他**可访问**网络位置 经过 [URLEncode](https://www.urlencoder.org/) 处理后，添加至 `&config=` 即可调用 需要注意的是，由外部配置中所定义的值会**覆盖** `pref.ini` 里的内容 即，如果你在外部配置中定义了

```text
emoji=(流量|时间|应急),🏳️‍🌈
emoji=阿根廷,🇦🇷
```

那么本程序只会匹配以上两个 Emoji，不再使用 `pref.ini` 中所定义的 国别 Emoji

**点击查看文件内容** \`\`\`ini \[custom\] ;这是一个外部配置文件示例 ;所有可能的自定义设置如下所示 ;用于自定义组的选项 会覆盖 pref.ini 里的内容 ;使用以下模式生成 Clash 代理组，带有 "\[\]" 前缀将直接添加 ;Format: Group\_Name\`select\`Rule\_1\`Rule\_2\`... ; Group\_Name\`url-test\|fallback\|load-balance\`Rule\_1\`Rule\_2\`...\`test\_url\`interval ;Rule with "\[\]" prefix will be added directly. custom\_proxy\_group=Proxy\`select\`.\*\`\[\]AUTO\`\[\]DIRECT\`.\* custom\_proxy\_group=UrlTest\`url-test\`.\*\`http://www.gstatic.com/generate\_204\`300 custom\_proxy\_group=FallBack\`fallback\`.\*\`http://www.gstatic.com/generate\_204\`300 custom\_proxy\_group=LoadBalance\`load-balance\`.\*\`http://www.gstatic.com/generate\_204\`300 ;custom\_proxy\_group=g1\`select\`!!GROUPID=0 ;custom\_proxy\_group=g2\`select\`!!GROUPID=1 ;custom\_proxy\_group=v2ray\`select\`!!GROUP=V2RayProvider ;custom\_proxy\_group=g1hk\`select\`!!GROUPID=0!!\(HGC\|HKBN\|PCCW\|HKT\|hk\|港\) ;custom\_proxy\_group=sstw\`select\`!!GROUP=V2RayProvider!!\(深台\|彰化\|新北\|台\|tw\) ;用于自定义规则的选项 会覆盖 pref.ini 里的内容 ;Ruleset addresses, supports local files/URL ;Format: Group name,URL ; Group name,\[\]Rule enable\_rule\_generator=false overwrite\_original\_rules=false ;surge\_ruleset=DIRECT,https://raw.githubusercontent.com/ConnersHua/Profiles/master/Surge/Ruleset/Unbreak.list ;surge\_ruleset=🎯 全球直连,rules/LocalAreaNetwork.list ;surge\_ruleset=🎯 全球直连,\[\]GEOIP,CN ;surge\_ruleset=🐟 漏网之鱼,\[\]FINAL ;用于自定义基础配置的选项 会覆盖 pref.ini 里的内容 clash\_rule\_base=base/forcerule.yml ;surge\_rule\_base=base/surge.conf ;surfboard\_rule\_base=base/surfboard.conf ;mellow\_rule\_base=base/mellow.conf ;quan\_rule\_base=base/quan.conf ;quanx\_rule\_base=base/quanx.conf ;用于自定义重命名的选项 会覆盖 pref.ini 里的内容 ;rename=Test-\(.\*?\)-\(.\*?\)-\(.\*?\)\\(\(.\*?\)\\)@\1\4x测试线路\_自\2到\3 ;rename=\\(?\(\(x\|X\)?\(\d+\)\(\.?\d+\)?\)\(\(\s?倍率?\)\|\(x\|X\)\)\\)?@$1x ;用于自定义 Emoji 的选项 会覆盖 pref.ini 里的内容 ;emoji=\(流量\|时间\|应急\),🏳️‍🌈 ;emoji=阿根廷,🇦🇷 \`\`\`

## 自动上传

> 自动上传 gist ，可以用于 Clash For Android / Surge 等进行远程订阅

在程序目录内的 [gistconf.ini](base/gistconf.ini) 中添加 `Personal Access Token`（[在此创建](https://github.com/settings/tokens/new?scopes=gist&description=Subconverter)）例如：

```text
[common]
;uncomment the following line and enter your token to enable upload function
token = xxxxxxxxxxxxxxxxxxxxxxxx(所生成的 Personal Access Token)
```

在 [调用地址]() 或 [调用地址 \(进阶\)]() 所生成的链接后加上 `&upload=true` 就会在更新好后自动上传 gist 此时，subconverter 程序窗口内会出现如下所示的**神秘代码**：

```text
No gist id is provided. Creating new gist...
Writing to Gist success!
Generator: surge4
Path: surge4
Raw URL: https://gist.githubusercontent.com/xxxx/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx/raw/surge4
Gist owner: xxxx
```

上方所提到的 `Raw URL: https://gist.githubusercontent.com/xxxx/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx/raw/surge4` 中的 `https://gist.githubusercontent.com/xxxx/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx/raw/surge4` 即是你的在线订阅链接。

注意，本程序默认会将此链接设为**秘密状态**

根据 [`官方手册 - 创建 Gist`](https://help.github.com/cn/github/writing-on-github/creating-gists) 的解释为：

> 秘密 gists 不会显示在 Discover 中，也不可搜索。
>
> 秘密 gists 不是私人的。 如果将秘密 gist 的 URL 发送给朋友，他们可以查看。
>
> 但是，如果您不认识的人发现该 URL，也能看到您的 gist。

所以请务必保管好所生成的 `Raw URL` 链接。

