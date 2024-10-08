升级到Debian 12：
修改 /etc/apt/sources.list 文件，将所有 bullseye 替换为 bookworm。
更新软件包列表并进行升级：

sudo apt update

sudo apt upgrade

sudo apt full-upgrade

sudo reboot

检查系统版本

cat /etc/debian_version
# 阿里云卸载监控
以root用户登录云监控插件所在主机。

执行以下命令，停止云监控插件。
```bash
bash /usr/local/cloudmonitor/cloudmonitorCtl.sh stop
```
执行以下命令，卸载云监控插件。
```bash
bash /usr/local/cloudmonitor/cloudmonitorCtl.sh uninstall
```
执行以下命令，删除目录cloudmonitor。
```bash
rm -rf /usr/local/cloudmonitor
```
# 安装.NET8.0
https://learn.microsoft.com/zh-cn/dotnet/core/install/linux-debian#debian-12
# Linux运行控制台程序
```bash
chmod 777 ok.dll
dotnet ok.dll
```
# 端口扫描
安装nmap
https://nmap.org/download.html#windows
# 网络模拟器
https://sourceforge.net/projects/gns-3/
# 系统更新
Debian搜索安装内核
```bash
sudo apt search linux-image
```
```bash
sudo apt install linux-image-6.10.11-cloud-amd64
```
```bash
sudo apt autoremove -y && sudo apt autoclean && sudo reboot
```
Debian12更新系统
```bash
sudo apt update && sudo apt full-upgrade -y
```
```bash
sudo apt autoremove -y && sudo apt autoclean && sudo reboot
```
```bash
rm -rf /etc/apt/sources.list
sudo sh -c 'echo "deb https://deb.debian.org/debian trixie main contrib" >> /etc/apt/sources.list' 
sudo apt update && sudo apt full-upgrade -y  # 更新软件包列表并进行升级
```
```bash
sudo apt autoremove -y && sudo apt autoclean && sudo reboot
```
# Gemini搭建教程和环境变量
安全等级修改/app/client/platforms/google.ts里面的BLOCK_ONLY_HIGH改成BLOCK_NONE

app/constant.ts

app/store/access.ts

修改面具中的prompt删除多余的面具/app/masks/cn.ts和/app/masks/en.ts

越狱prompt https://github.com/trinib/ZORG-Jailbreak-Prompt-Text

参考

https://github.com/do02fw/ChatGPT-Next-Web/blob/main/app/masks/cn.ts

https://github.com/do02fw/ChatGPT-Next-Web/blob/main/app/masks/en.ts

搭建和更新教程 https://github.com/do02fw/ChatGPT-Next-Web/blob/main/docs/vercel-cn.md#%E5%A6%82%E4%BD%95%E6%96%B0%E5%BB%BA%E9%A1%B9%E7%9B%AE

Vercel https://vercel.com/

模型版本

https://ai.google.dev/gemini-api/docs/models/gemini?hl=zh-cn#gemini-1.5-flash

环境变量 https://github.com/do02fw/ChatGPT-Next-Web/blob/main/README_CN.md
```bash
CUSTOM_MODELS -all,+gemini-1.5-flash-latest
DISABLE_FAST_LINK 1
HIDE_USER_API_KEY 1
GOOGLE_API_KEY 密钥
```
# openvpn官方文档
https://openvpn.net/community-resources/reference-manual-for-openvpn-2-6
# 安装openvpn
Ubuntu24
```bash
mkdir -p /etc/apt/keyrings && apt-get install gpg && sudo curl -fsSL https://swupdate.openvpn.net/repos/repo-public.gpg | gpg --dearmor > /etc/apt/keyrings/openvpn-repo-public.gpg && echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/release/2.6 noble main" > /etc/apt/sources.list.d/openvpn-aptrepo.list && wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
```
Debian12
```bash
mkdir -p /etc/apt/keyrings && apt-get install gpg && sudo curl -fsSL https://swupdate.openvpn.net/repos/repo-public.gpg | gpg --dearmor > /etc/apt/keyrings/openvpn-repo-public.gpg && echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/release/2.6 bookworm main" > /etc/apt/sources.list.d/openvpn-aptrepo.list && wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
```
选UDP端口65535 DNS选1.1.1.1   
# 安装openvpn-dco
```bash
apt install openvpn-dco-dkms
```
# 安装完成后执行
包括IPV6
```bash
echo 'push "dhcp-option DNS 2606:4700:4700::1111"' >> /etc/openvpn/server/server.conf;
echo 'push "dhcp-option DNS 2606:4700:4700::1001"' >> /etc/openvpn/server/server.conf;
echo 'duplicate-cn' >> /etc/openvpn/server/server.conf;
```
不包括IPV6
```bash
echo 'duplicate-cn' >> /etc/openvpn/server/server.conf;
```
# 阻止IPV6流量的办法
redirect-gateway def1 ipv6 bypass-dhcp改为redirect-gateway def1 bypass-dhcp

删除服务器配置文件里分配的IPV6地址

服务器配置文件添加
```bash
# 将 IPv6 流量重定向到 VPN
push "redirect-gateway ipv6"
# 在服务器端阻止 IPv6 流量
block-ipv6
```
客户端配置文件添加
```bash
# 将 IPv6 流量重定向到 VPN
redirect-gateway ipv6
# 在客户端阻止 IPv6 流量
block-ipv6 
```
# 重启openvpn服务，最好重启服务器
```bash
sudo service openvpn restart
```
# 使用IPV6连接
修改配置文件vim /etc/openvpn/server/server.conf

添加
local <IPv6地址>

客户端和服务器的配置文件中的proto udp需要改为proto udp6
# 官方客户端下载
https://openvpn.net/client/client-connect-vpn-for-windows/

https://www.apkmirror.com/apk/openvpn/openvpn-connect/
# 编译哔哩哔哩
https://github.com/BiliRoamingX/BiliRoamingX

下载JDK并配置环境
https://jdk.java.net/23/

打开系统属性 -> 高级系统设置 -> 环境变量。

在系统变量中，找到 Path 变量，点击编辑。

在变量值末尾添加JDK的安装路径，例如：C:\Program Files\Java\jdk-11.0.16\bin

新建一个系统变量，变量名为 JAVA_HOME，变量值为JDK的安装路径，例如：C:\Program Files\Java\jdk-11.0.16

下载所需文件

https://github.com/zjns/revanced-cli/releases/download/v4.6.0.1/revanced-cli.jar 

https://github.com/BiliRoamingX/BiliRoamingX/actions/workflows/ci.yml

https://dl.hdslb.com/mobile/latest/android64/iBiliPlayer-bili.apk

cmd执行
```bash
java -jar revanced-cli.jar patch --merge BiliRoamingX-integrations.apk --patch-bundle BiliRoamingX-patches.jar --signing-levels 2,3 iBiliPlayer-bili.apk
```
