# 阿里云修改软件源

Ubuntu22.04

sudo sed -i.bak 's/http:\/\/mirrors.cloud.aliyuncs.com\/ubuntu/http:\/\/archive.ubuntu.com\/ubuntu/g' /etc/apt/sources.list

# 系统更新

Debian12更新系统

sudo apt update && sudo apt full-upgrade -y

sudo apt autoremove -y && sudo reboot

Ubuntu22更新系统LTS版本

sudo apt install ubuntu-release-upgrader-core -y && sudo apt update && sudo do-release-upgrade

apt autoremove -y && sudo reboot

Ubuntu22从LTS版更新到正式版

sudo sed -i 's/Prompt=lts/Prompt=normal/g' /etc/update-manager/release-upgrades && sudo apt update && sudo apt full-upgrade -y

apt autoremove -y && sudo reboot

sudo apt update && sudo do-release-upgrade

apt autoremove -y && sudo reboot

Ubuntu22如果依赖包更新失败强制更新

sudo apt install aptitude && sudo aptitude full-upgrade

# ocserv配置教程

安装chmod +x ocserv.sh && bash ocserv.sh

完成后执行或者直接替换配置文件ocserv.conf

开启IPV6

修改/etc/sysctl.conf开启IPV6转发

sudo ip6tables -t nat -A POSTROUTING -j MASQUERADE

sudo ip6tables-save > /etc/iptables/rules.v6

更新系统后没网的话执行一下

sudo iptables -t nat -A POSTROUTING -j MASQUERADE

sudo iptables-save > /etc/iptables/rules.v4

客户端下载

https://www.catpaws2011.com/docs/?p=420 或者 https://gitlab.com/openconnect/openconnect-gui/-/releases

https://www.apkmirror.com/apk/cisco-systems-inc/anyconnect

# Gemini搭建教程和环境变量

安全等级修改/app/client/platforms/google.ts里面的BLOCK_ONLY_HIGH改成BLOCK_NONE

参考https://github.com/do02fw/ChatGPT-Next-Web/blob/main/app/client/platforms/google.ts

修改面具中的prompt删除多余的面具/app/masks/cn.ts和/app/masks/en.ts

越狱prompt https://github.com/trinib/ZORG-Jailbreak-Prompt-Text

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

CUSTOM_MODELS -all,+gemini-1.5-pro
DISABLE_FAST_LINK 1
HIDE_USER_API_KEY 1
GOOGLE_API_KEY 密钥

```

# openvpn官方文档

https://openvpn.net/community-resources/reference-manual-for-openvpn-2-6

# 安装openvpn

Ubuntu23系统

mkdir -p /etc/apt/keyrings && apt-get install gpg && sudo curl -fsSL https://swupdate.openvpn.net/repos/repo-public.gpg | gpg --dearmor > /etc/apt/keyrings/openvpn-repo-public.gpg && echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/testing mantic main" > /etc/apt/sources.list.d/openvpn-aptrepo.list && sudo wget https://git.io/vpn -O openvpn-install.sh && sudo bash openvpn-install.sh

Debian12系统

mkdir -p /etc/apt/keyrings && apt-get install gpg && sudo curl -fsSL https://swupdate.openvpn.net/repos/repo-public.gpg | gpg --dearmor > /etc/apt/keyrings/openvpn-repo-public.gpg && echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/testing bookworm main" > /etc/apt/sources.list.d/openvpn-aptrepo.list && sudo wget https://git.io/vpn -O openvpn-install.sh && sudo bash openvpn-install.sh

选择udp dns 1.1.1.1 端口65535
             
# 安装完成后执行

sed -i 's/1.0.0.1/2606:4700:4700::1001/g' /etc/openvpn/server/server.conf && sed -i 's/1.1.1.1/1.0.0.1/g' /etc/openvpn/server/server.conf && echo '--data-ciphers AES-256-GCM' >> /etc/openvpn/server/server.conf && echo 'mtu-disc maybe' >> /etc/openvpn/server/server.conf && echo 'duplicate-cn' >> /etc/openvpn/server/server.conf

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

# 编译哔哩哔哩

sudo apt install openjdk-21-jdk -y

wget https://github.com/zjns/revanced-cli/releases/download/v4.6.0.1/revanced-cli.jar && wget https://github.com/BiliRoamingX/BiliRoamingX/releases/download/v1.20.3/BiliRoamingX-integrations-1.20.3.apk && wget https://github.com/BiliRoamingX/BiliRoamingX/releases/download/v1.20.3/BiliRoamingX-patches-1.20.3.jar && wget https://dl.hdslb.com/mobile/latest/android64/iBiliPlayer-bili.apk

java -jar revanced-cli.jar patch --merge BiliRoamingX-integrations-1.20.3.apk --patch-bundle BiliRoamingX-patches-1.20.3.jar --signing-levels 2,3 iBiliPlayer-bili.apk

