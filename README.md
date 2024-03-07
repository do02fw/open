https://openvpn.net/community-resources/reference-manual-for-openvpn-2-6/#encryption-options

# 准备环境

mkdir -p /etc/apt/keyrings

apt-get install gpg

curl -fsSL https://swupdate.openvpn.net/repos/repo-public.gpg | gpg --dearmor > /etc/apt/keyrings/openvpn-repo-public.gpg

echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/testing jammy main" > /etc/apt/sources.list.d/openvpn-aptrepo.list

# 安装启动openvpn服务

wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh             \# 选择udp dns 1.1.1.1那个 端口随便输别默认

echo 'mtu-disc yes' >> /etc/openvpn/server/server.conf

echo 'duplicate-cn' >> /etc/openvpn/server/server.conf

# 重启openvpn服务

service openvpn restart

ipv6的dns:

2606:4700:4700::1001


# 开启IPV6转发

修改/etc/sysctl.conf 取消ipv6注释


# 使用IPV6连接

修改/etc/openvpn/server/server.conf的IP地址为服务器IPV6地址以及客户端配置文件的地址为IPV6地址
服务器端配置文件中，添加以下行：
local <IPv4地址>
local <IPv6地址>

