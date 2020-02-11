# 链接调用

## 调用地址

```text
http://127.0.0.1:25500/sub?target=%TARGET%&url=%URL%&config=%CONFIG%
```

## 调用说明

| 调用参数 | 必要性 | 示例 | 解释 |
| :--- | :---: | :--- | :--- |
| target | 必要 | surge&ver=4 | 指想要生成的配置类型，详见上方 [适用范围](../yue-qian-ti-shi/shi-yong-fan-wei.md) 中的参数 |
| url | 必要 | https%3A%2F%2Fwww.xxx.com | 指机场所提供的订阅链接，需要经过 [URLEncode](https://www.urlencoder.org/) 处理 |
| config | 可选 | https%3A%2F%2Fwww.xxx.com | 指远程 `pref.ini` \(包含分组和规则部分\)，需要经过 [URLEncode](https://www.urlencoder.org/) 处理，可查看 [示例仓库](https://github.com/lzdnico/subconverteriniexample) 寻找灵感，默认加载本地设置文件 |

{% hint style="success" %}
运行 subconverter 主程序后，按照 [调用示例](tiao-yong-shi-li.md) 的对应内容替换

即可得到一份使用 **神机规则** 的配置文件。
{% endhint %}



