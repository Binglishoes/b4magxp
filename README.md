

* `https://<PaaS云服务商分配的域名>/<UUID>.html` 展示了各种配置以及客户端二维码。
* `https://<PaaS云服务商分配的域名>/<UUID>.json` 为对应的 v 客户端文件。
* 增加订阅模式，以防止每次 CloudFlare 分配的域名改变。可在 V2rayA 和安卓上的 V中添加订阅，地址为`https://<PaaS云服务商分配的域名>/<UUID>.txt`。每次发现之前的地址不可用之后先刷新下订阅再尝试连接，如果还不行过30秒刷一次再试，因为容器启动需要时间。
* `https://<PaaS云服务商分配的域名>/cf.txt` 为最新的Cloudflare分配域名。
* 增加 Cloudflared 多次重试，应对 CloudFlare 偶尔抽风。
* 在连接路径后面增加 `_warp` 来使流量全程走Cloudflare WARP。
* `https://<PaaS云服务商分配的域名>/<UUID>.rootfs/` 可直接下载rootfs中的内容（可在nginx.conf中删除相关段以禁用）。
* 增加ssh服务器，可连接至后台。该ssh服务在公网上不可见，需要以无"_warp"的路径连接到节点，然后通过proxychains劫持来连接：`proxychains ssh root@127.0.0.1 -v`。
* ssh服务器仅支持Key的方式登录，可以设置环境变量 `SSH_PUBKEY`、`SSH_PUBKEY2`、`SSH_PUBKEY3` 和`SSH_PUBKEY4`，最多支持 4 个 Key。






