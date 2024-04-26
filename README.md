# ocserv配置教程

ocserv.sh是脚本，改为777权限后才能执行

完成后执行或者直接替换配置文件ocserv.conf

sudo sed -i '/net.core.default_qdisc=fq\|net.ipv4.tcp_congestion_control=bbr/d' /etc/sysctl.conf

开启IPV6（可选）

sudo ip6tables -t nat -A POSTROUTING -j MASQUERADE

sudo ip6tables-save > /etc/iptables/rules.v6

修改/etc/sysctl.conf开启ipv6转发


Ubuntu更新到正式版命令

sudo apt install ubuntu-release-upgrader-core

sudo sed -i 's/Prompt=lts/Prompt=normal/g' /etc/update-manager/release-upgrades

sudo do-release-upgrade

更新到开发版

sudo do-release-upgrade -d


更新系统后没网的话执行一下

sudo iptables -t nat -A POSTROUTING -j MASQUERADE

sudo iptables-save > /etc/iptables/rules.v4

更新后iptables和ocserv.conf需要重新设置

客户端下载

www.catpaws2011.com/docs/?p=420 或者 gitlab.com/openconnect/openconnect-gui/-/releases

www.apkmirror.com/apk/cisco-systems-inc/anyconnect

debian12更新到测试版

sed -i 's/bookworm/testing/g' /etc/apt/sources.list

apt update

apt upgrade

# Gemini搭建教程和环境变量

安全等级修改

/app/client/platforms/google.ts

里面的BLOCK_ONLY_HIGH改成BLOCK_NONE

参考https://github.com/do02fw/ChatGPT-Next-Web/blob/main/app/client/platforms/google.ts

修改面具中的prompt删除多余的面具

/app/masks/cn.ts和/app/masks/en.ts

越狱prompt

https://github.com/trinib/ZORG-Jailbreak-Prompt-Text

参考

https://github.com/do02fw/ChatGPT-Next-Web/blob/main/app/masks/cn.ts

https://github.com/do02fw/ChatGPT-Next-Web/blob/main/app/masks/en.ts


搭建和更新教程

https://github.com/do02fw/ChatGPT-Next-Web/blob/main/docs/vercel-cn.md#%E5%A6%82%E4%BD%95%E6%96%B0%E5%BB%BA%E9%A1%B9%E7%9B%AE

Vercel

https://vercel.com/

环境变量 

https://github.com/do02fw/ChatGPT-Next-Web/blob/main/README_CN.md

```bash

CUSTOM_MODELS -all,+gemini-pro
DISABLE_FAST_LINK 1
HIDE_USER_API_KEY 1
GOOGLE_API_KEY 密钥

```

# openvpn官方文档

https://openvpn.net/community-resources/reference-manual-for-openvpn-2-6/#encryption-options

# openvpn准备环境

mkdir -p /etc/apt/keyrings

apt-get install gpg

curl -fsSL https://swupdate.openvpn.net/repos/repo-public.gpg | gpg --dearmor > /etc/apt/keyrings/openvpn-repo-public.gpg

如果是Debian12.X或更高

echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/testing bookworm main" > /etc/apt/sources.list.d/openvpn-aptrepo.list

如果是Ubuntu23.X或更高

echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/testing mantic main" > /etc/apt/sources.list.d/openvpn-aptrepo.list

# 安装启动openvpn服务

wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
             
# 选择udp dns 1.1.1.1 端口65535

安装完成后执行

sed -i 's/1.0.0.1/2606:4700:4700::1001/g' /etc/openvpn/server/server.conf

sed -i 's/1.1.1.1/1.0.0.1/g' /etc/openvpn/server/server.conf

echo '--data-ciphers AES-256-GCM' >> /etc/openvpn/server/server.conf

echo 'duplicate-cn' >> /etc/openvpn/server/server.conf

# 禁用客户端的IPv6流量

echo 'push "redirect-gateway ipv6 def1 bypass-dhcp"' >> /etc/openvpn/server/server.conf

# 重启openvpn服务，最好重启服务器

sudo service openvpn restart

# 使用IPV6连接

修改配置文件vim /etc/openvpn/server/server.conf

添加
local <IPv6地址>

客户端和服务器的配置文件中的proto udp需要改为proto udp6

# 官方客户端下载

https://openvpn.net/client/client-connect-vpn-for-windows/

https://www.apkmirror.com/apk/openvpn/openvpn-connect/
