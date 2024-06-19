# DDOS
安装git
https://git-scm.com/download/win

安装环境
```bash
git clone https://github.com/MatrixTM/MHDDoS.git
cd MHDDoS
pip install -r requirements.txt
```
例子
```bash
apt install screen -y;
screen -S ok;
python3 start.py ICMP 127.0.0.1 200 999999;
python3 start.py TCP 127.0.0.1:443 200 999999;
```
CTRL+A+D退出

https://sourceforge.net/projects/pynuker/

https://sourceforge.net/projects/gns-3/
# 系统更新
Debian12更新系统
```bash
sudo apt update && sudo apt full-upgrade -y
```
```bash
sudo apt autoremove -y && sudo apt autoclean && sudo reboot
```
Ubuntu LTS版更新系统
```bash
sudo apt install ubuntu-release-upgrader-core -y && sudo apt update && sudo apt upgrade -y
```
```bash
apt autoremove -y && sudo apt autoclean && sudo reboot
```
Ubuntu LTS版更新到正式版
```bash
sudo sed -i 's/Prompt=lts/Prompt=normal/g' /etc/update-manager/release-upgrades && sudo apt update && sudo apt full-upgrade -y
```
```bash
sudo apt autoclean && sudo apt update && sudo do-release-upgrade
```
```bash
apt autoremove -y && sudo apt autoclean
```
Ubuntu正式版更新到开发版
```bash
sudo apt update && sudo do-release-upgrade -d
```
```bash
apt autoremove -y && sudo apt autoclean && sudo reboot
```
Ubuntu如果依赖包更新失败强制更新
```bash
sudo apt install aptitude -y && sudo aptitude full-upgrade -y
```
Ubuntu如果出现DNS错误执行
```bash
sudo rm -rf /etc/resolv.conf;
sudo touch /etc/resolv.conf;
sudo echo "nameserver 1.1.1.1" >> /etc/resolv.conf;
```
Ubuntu官方源
```bash
archive.ubuntu.com
```
Ubuntu24.04添加源签名
```bash
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
```
# ocserv
安装
```bash
wget https://raw.githubusercontent.com/do02fw/open/main/ocserv.sh;
chmod 777 ocserv.sh;
bash ocserv.sh;
```
```bash
cd /etc/ocserv;
wget https://raw.githubusercontent.com/do02fw/open/main/ocserv.conf;
```
修改/etc/sysctl.conf开启IPV6
```bash
sudo ip6tables -t nat -A POSTROUTING -j MASQUERADE && sudo ip6tables-save > /etc/iptables/rules.v6
```
更新系统后没网的话执行一下
```bash
sudo iptables -t nat -A POSTROUTING -j MASQUERADE && sudo iptables-save > /etc/iptables/rules.v4
```
客户端下载

https://www.catpaws2011.com/docs/?p=420

https://gitlab.com/openconnect/openconnect-gui/-/releases

https://www.apkmirror.com/apk/cisco-systems-inc/anyconnect
# Gemini搭建教程和环境变量
安全等级修改/app/client/platforms/google.ts里面的BLOCK_ONLY_HIGH改成BLOCK_NONE

参考 https://github.com/do02fw/ChatGPT-Next-Web/blob/main/app/client/platforms/google.ts

修改面具中的prompt删除多余的面具/app/masks/cn.ts和/app/masks/en.ts

越狱prompt https://github.com/trinib/ZORG-Jailbreak-Prompt-Text

参考

https://github.com/do02fw/ChatGPT-Next-Web/blob/main/app/masks/cn.ts

https://github.com/do02fw/ChatGPT-Next-Web/blob/main/app/masks/en.ts

搭建和更新教程 https://github.com/do02fw/ChatGPT-Next-Web/blob/main/docs/vercel-cn.md#%E5%A6%82%E4%BD%95%E6%96%B0%E5%BB%BA%E9%A1%B9%E7%9B%AE

Vercel https://vercel.com/

环境变量 https://github.com/do02fw/ChatGPT-Next-Web/blob/main/README_CN.md
```bash
CUSTOM_MODELS -all,+gemini-1.5-flash-latest
DISABLE_FAST_LINK 1
HIDE_USER_API_KEY 1
GOOGLE_API_KEY 密钥
```
# openvpn官方文档
https://openvpn.net/community-resources/reference-manual-for-openvpn-2-6
# 安装openvpn，服务器必须有IPV6地址
Ubuntu24
```bash
mkdir -p /etc/apt/keyrings && apt-get install gpg && sudo curl -fsSL https://swupdate.openvpn.net/repos/repo-public.gpg | gpg --dearmor > /etc/apt/keyrings/openvpn-repo-public.gpg && echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/release/2.6 noble main" > /etc/apt/sources.list.d/openvpn-aptrepo.list && wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
```
Debian12
```bash
mkdir -p /etc/apt/keyrings && apt-get install gpg && sudo curl -fsSL https://swupdate.openvpn.net/repos/repo-public.gpg | gpg --dearmor > /etc/apt/keyrings/openvpn-repo-public.gpg && echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/release/2.6 bookworm main" > /etc/apt/sources.list.d/openvpn-aptrepo.list && wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
```
选UDP 端口65535 DNS选Google         
# 安装完成后执行
```bash
echo 'push "dhcp-option DNS 2001:4860:4860::8844' >> /etc/openvpn/server/server.conf;
echo 'push "dhcp-option DNS 2001:4860:4860::8888' >> /etc/openvpn/server/server.conf;
echo '--data-ciphers AES-256-GCM' >> /etc/openvpn/server/server.conf;
echo 'duplicate-cn' >> /etc/openvpn/server/server.conf;
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
# 安装openvpn dco
```bash
apt install openvpn-dco-dkms -y
```
https://openvpn.net/as-docs/tutorials/tutorial--turn-on-openvpn-dco.html#step-3--verify-openvpn-dco-is-now-in-use
# 官方客户端下载
https://openvpn.net/client/client-connect-vpn-for-windows/

https://www.apkmirror.com/apk/openvpn/openvpn-connect/
# 编译哔哩哔哩
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
