# ocserv配置教程

完成后执行

sudo sed -i '/net.core.default_qdisc=fq\|net.ipv4.tcp_congestion_control=bbr/d' /etc/sysctl.conf

sudo sed -i 's/keepalive = 3000/keepalive = 32400/g' /etc/ocserv/ocserv.conf

sudo sed -i 's/dpd = 60/dpd = 0/g' /etc/ocserv/ocserv.conf

sudo sed -i 's/mobile-dpd = 300/mobile-dpd = 0/g' /etc/ocserv/ocserv.conf

sudo sed -i 's/compression = true/compression = false/g' /etc/ocserv/ocserv.conf

sudo sed -i 's/^no-compress-limit = 256/# no-compress-limit = 256/' /etc/ocserv/ocserv.conf

sudo sed -i 's/tls-priorities = "NORMAL:%SERVER_PRECEDENCE:%COMPAT:-RSA:-VERS-SSL3.0:-ARCFOUR-128:-VERS-TLS1.0:-VERS-TLS1.1"/tls-priorities = "NORMAL:%SERVER_PRECEDENCE:%COMPAT:-RSA:-VERS-SSL3.0:-ARCFOUR-128:-VERS-TLS1.0:-VERS-TLS1.1:-VERS-TLS1.2"/' /etc/ocserv/ocserv.conf

sudo sed -i 's/dns = 8.8.8.8/dns = 1.0.0.1/' /etc/ocserv/ocserv.conf

sudo sed -i 's/^dns = 8.8.4.4/#dns = 8.8.4.4/' /etc/ocserv/ocserv.conf

sudo sed -i 's/^#net-priority = 3/net-priority = 6/' /etc/ocserv/ocserv.conf

sudo sed -i 's/#mtu = 1420/mtu = 1420/g' /etc/ocserv/ocserv.conf

sudo sed -i 's/try-mtu-discovery = true/try-mtu-discovery = false/g' /etc/ocserv/ocserv.conf

开启IPV6（可选）

sudo sed -i 's/#dns = 8.8.4.4/dns = 2606:4700:4700::1001/' /etc/ocserv/ocserv.conf

sudo sed -i 's/#ipv6-network = fda9:4efe:7e3b:03ea::\/48/ipv6-network = fda9:4efe:7e3b:03ea::\/48/' /etc/ocserv/ocserv.conf

sudo sed -i 's/#ipv6-subnet-prefix = 64/ipv6-subnet-prefix = 64/' /etc/ocserv/ocserv.conf


# Gemini搭建教程和环境变量

安全等级修改

/app/client/platforms/google.ts

里面的BLOCK_ONLY_HIGH改成BLOCK_NONE

修改面具中的prompt

/app/masks/cn.ts

越狱prompt

https://github.com/trinib/ZORG-Jailbreak-Prompt-Text

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

echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/testing bookworm main" > /etc/apt/sources.list.d/openvpn-aptrepo.list

如果是Ubuntu则

echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/testing jammy main" > /etc/apt/sources.list.d/openvpn-aptrepo.list

如果是Ubuntu测试版则

echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/testing lunar main" > /etc/apt/sources.list.d/openvpn-aptrepo.list


# 安装启动openvpn服务

wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
             \# 选择udp dns 1.1.1.1那个 端口随便输别默认

安装完成后执行

sed -i 's/1.0.0.1/2606:4700:4700::1001/g' /etc/openvpn/server/server.conf

sed -i 's/1.1.1.1/1.0.0.1/g' /etc/openvpn/server/server.conf

echo 'mtu-disc yes' >> /etc/openvpn/server/server.conf

echo 'duplicate-cn' >> /etc/openvpn/server/server.conf

禁用IPV6



# 重启openvpn服务

sudo service openvpn restart


# 使用IPV6连接

修改配置文件vim /etc/openvpn/server/server.conf

添加
local <IPv6地址>

客户端和服务器的配置文件中的proto udp需要改为proto udp6

# 官方客户端下载

https://openvpn.net/client/client-connect-vpn-for-windows/

https://www.apkmirror.com/apk/openvpn/openvpn-connect/
