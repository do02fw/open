# Gemini启动命令

```bash
$ docker run -d \
    --name chatgemini \
    --restart always \
    --publish 80:8080 \
    --env REACT_APP_GEMINI_API_KEY="KEY" \
    --env REACT_APP_GEMINI_API_URL="__use_nginx__" \
    --env GENERATIVE_AI_API_VERSION=v1 \
    ghcr.io/bclswl0827/chatgemini
```

# 官方文档

https://openvpn.net/community-resources/reference-manual-for-openvpn-2-6/#encryption-options

# 准备环境

mkdir -p /etc/apt/keyrings

apt-get install gpg

curl -fsSL https://swupdate.openvpn.net/repos/repo-public.gpg | gpg --dearmor > /etc/apt/keyrings/openvpn-repo-public.gpg

echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/testing bookworm main" > /etc/apt/sources.list.d/openvpn-aptrepo.list

如果是Ubuntu则

echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/testing jammy main" > /etc/apt/sources.list.d/openvpn-aptrepo.list

# 安装启动openvpn服务

wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
             \# 选择udp dns 1.1.1.1那个 端口随便输别默认

安装完成后执行

sed -i 's/1.0.0.1/2606:4700:4700::1001/g' /etc/openvpn/server/server.conf

sed -i 's/1.1.1.1/1.0.0.1/g' /etc/openvpn/server/server.conf

echo 'mtu-disc yes' >> /etc/openvpn/server/server.conf

echo 'duplicate-cn' >> /etc/openvpn/server/server.conf

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
