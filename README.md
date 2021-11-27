# v2csub
#### Subscriber for V2Ray-core
#### V2Ray-core 的订阅脚本

> V2Ray本身支持均衡策略，即像clash一样选择反应最快的节点
> 
> V2Ray本身支持多文件配置

有以上两点为前提，图形界面已经不重要了。

### 简单说明
增加执行权限

`chmod +x v2csub`



脚本会优先读取`HOME/.config/v2csub/config`的配置文件

若文件不存在则读取`/etc/v2csub/config`

脚本默认输出模板为`/etc/v2csub/templates`

请将此文件夹放到此路径或修改配置文件

修改配置文件中url部分，填入订阅连接

`v2csub`

即可订阅

或使用参数

`v2csub -u [订阅地址]`

#### 详细参数可执行 `v2csub -h`

#### 最后执行 `v2ray -c gfw.json -confdir /tmp/v2csub` 即可成功运行




### 常用配置

留个坑有空再写
