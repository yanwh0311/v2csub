# v2csub
#### Subscriber for V2Ray-core
#### V2Ray-core 的订阅脚本

> V2Ray本身支持均衡策略，即像clash一样选择反应最快的节点
> 
> V2Ray本身支持多文件配置

有以上两点为前提，图形界面已经不重要了。

### 简单说明
增加执行权限 并按表格放置文件

`chmod +x v2csub`


| 文件 | 位置 |
|-----| ---- |
|v2csub|/usr/bin/|
|config|/etc/v2csub/config 或 $HOME/.config/v2csub/config|
|gfw.json|/etc/v2csub/gfw.json|
|nonCN.json|/etc/v2csub/nonCN.json|
|templates|/etc/v2csub/templates|
|v2csub.service|/usr/lib/systemd/system/v2csub.service (可选)|



修改配置文件中url部分，填入订阅连接

`v2csub`

即可订阅

或使用参数

`v2csub -u [订阅地址]`

#### 详细参数可执行 `v2csub -h`

#### 最后执行 `v2ray -c gfw.json -confdir /tmp/v2csub` 即可成功运行

#### 注意：若使用 nonCN.json 需修改nonCN.json，将服务器的地址加入直连




### 常用配置

留个坑有空再写
