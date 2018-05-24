# V-P-S-ss

## VPS Ubuntu18.04 开启ss服务

> 1. 安装pip
```
sudo apt install python3-pip
```

> 2. 安装ss-3.0

```
pip3 install https://github.com/shadowsocks/shadowsocks/archive/master.zip
```

> 3. 编辑ss-server脚本（密码模式google）
```
sudo vim /etc/shadowsocks.json

{

   	"server":"服务器ip",
    
   	"server_port":6666,
    
   	"local_address": "127.0.0.1",
    
   	"local_port":1080,
    
   	"password":"连接密码",
    
   	"timeout":300,
    
   	"method":"加密方式"
    
}

```

> 4.使用 sysrmctl 设置开机启动

```
vim /lib/systemd/system/shadowsocks.service


[Unit]

Description=Shadowsocks Server

After=network.target


[Service]

ExecStart=/usr/local/bin/ssserver -c /etc/shadowsocks.json

Restart=on-abort



[Install]

WantedBy=multi-user.target
```

> 5.  允许开机启动

```
systemctl enable shadowsocks.service
```

> 6. 启动服务

```
systemctl status shadowsocks.service
```

## 开启bbr 加速
[bbr]

[bbr]:https://github.com/iMeiji/shadowsocks_install/wiki/%E5%BC%80%E5%90%AFTCP-BBR%E6%8B%A5%E5%A1%9E%E6%8E%A7%E5%88%B6%E7%AE%97%E6%B3%95
