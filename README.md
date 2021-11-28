# v2csub
#### Subscriber for V2Ray-core
#### V2Ray-core 的订阅脚本

> V2Ray本身支持均衡策略，即像clash一样选择响应最快的节点
> 
> V2Ray本身支持多文件配置

有以上两点为前提，图形界面已经不重要了。

#### 脚本实现的功能
* 支持http/https连接的订阅（v2rayN格式）
 
* 支持tcp/kcp/ws/h2/quic传输协议的节点
 
* 默认为均衡模式（即自动选择响应最快的节点）


### 安装

Archlinux 用户

> yay -S v2csub-git

其它系统用户：

增加执行权限 并按表格放置文件

> chmod +x v2csub


| 文件 | 位置 |
|-----| ---- |
|v2csub|/usr/bin/v2csub|
|config|/etc/v2csub/config 或 $HOME/.config/v2csub/config|
|defaultkeys|/etc/v2csub/defaultkeys|
|gfw.json|/etc/v2csub/gfw.json|
|nonCN.json|/etc/v2csub/nonCN.json|
|templates|/etc/v2csub/templates|
|v2csub.service|/usr/lib/systemd/system/v2csub.service (可选)|


### 运行

修改配置文件中url部分，填入订阅连接，并执行

> v2csub

即可订阅

或使用参数

> v2csub -u [订阅地址]

详细参数可执行 `v2csub -h`

最后执行 `v2ray -c gfw.json -confdir /tmp/v2csub` 即可成功运行


***socks默认代理端口为1080，http端口为1081***


### 或加入自启动 

修改v2ray服务 

`#systemctl edit v2ray`  或直接修改 `/etc/systemd/system/v2ray.service.d/override.conf`

> [Service]
> 
> ExecStart=
> 
> ExecStart=/usr/bin/v2ray -config /etc/v2csub/gfw.json -confdir /tmp/v2csub/

加入自启动项

> #systemctl enable v2csub v2ray

启动

> #systemctl start v2csub v2ray





### FQA

* #### 与图形软件有什么区别？

此脚本只负责订阅，V2Ray功能很强大，图形软件并不能把所有的功能全部展示出来。因此，用脚本来订阅，V2Ray直接以修改文件的方式来配置，会更灵活。但用此脚本来配置也有一定的限制，比如不能手动切换节点，对于一些有ip限制的网站（比如网飞），自动选择节点并不友好。
 
* #### 如何设置自动测速间隔？

修改 `gfw.json` 或 `nonCN.json` 中 `probeInterval` 的值即可

* #### 如果想临时重新测速换节点怎么办？

重启v2ray即可

* #### 我的机场很稳定，我只想用一个节点或只想用某个地区的节点

V2Ray的匹配功能只能从左往右匹配。即节点名称为 "a" "ab" "ba" 的三个节点，如果检索 "a" ，只匹配到 "a" "ab" 。如果你对节点有某些特征的需求，请联系机场主改节点名称，比如"网飞节点xxx01"  "网飞节点xxx02" "香港节点xxx02" 之类的，主要特征在名称前的名字。然后修改 `gfw.json` 或 `nonCN.json` 中 `selector` 和 `subjectSelector` 的值。脚本本身会在所有名称前加V，因此无论检索什么名字，都需要加V。
