# 目录解释

```text
./subconverter
│
│  gistconf.ini  # 有关于上传至 Gist 的相关设定
│  pref.ini      # 主要配置文件 (优先级低于 pref.yml )
│  pref.yml      # 主要配置文件 (优先级高于 pref.ini )
│  
├─base           # 各软件的基础配置文件 (如 Clash, Surge, Quantumult 等)
│      
├─config         # 外部配置文件 (取代 主要配置文件， 优先级最高)
│      
├─rules          # 规则片段 (用于存放常用的规则片段, 如 神机, lhei1, ACL4SSR 等)
│              
└─snippets       # 复用片段 (用于存放常用的配置片段, 可使用 import 引用)
```



