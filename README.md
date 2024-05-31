```bash
apt install screen -y;
screen -S ok;
python3 start.py ICMP 127.0.0.1 30 999999;
```
CTRL+A+D退出
# 系统更新
Debian12更新系统
```bash
sudo apt update && sudo apt full-upgrade -y
```
```bash
sudo apt autoremove -y && sudo apt autoclean && sudo reboot
```
Debian12更新到测试版
```bash
sed -i 's/bookworm/trixie/g' /etc/apt/sources.list && sudo apt update && sudo apt full-upgrade -y -y
```
```bash
apt autoremove -y && sudo apt autoclean && sudo reboot
```
Ubuntu LTS版更新系统
```bash
sudo apt install ubuntu-release-upgrader-core -y && sudo apt update && sudo apt upgrade -y
```
```bash
apt autoremove -y && sudo apt autoclean && sudo reboot
```
```bash
sudo apt update && sudo do-release-upgrade
```
```bash
apt autoremove -y && sudo apt autoclean && sudo reboot
```
Ubuntu LTS版更新到正式版
```bash
sudo sed -i 's/Prompt=lts/Prompt=normal/g' /etc/update-manager/release-upgrades && sudo apt update && sudo apt full-upgrade -y
```
```bash
apt autoremove -y && sudo apt autoclean && sudo reboot
```
```bash
sudo apt update && sudo do-release-upgrade
```
```bash
apt autoremove -y && sudo apt autoclean && sudo reboot
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
Ubuntu官方源
```bash
archive.ubuntu.com
```
Ubuntu24.04添加源签名
```bash
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
```
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
# 安装openvpn，安装前系统必须是最新版
Ubuntu24
```bash
mkdir -p /etc/apt/keyrings && apt-get install gpg && sudo curl -fsSL https://swupdate.openvpn.net/repos/repo-public.gpg | gpg --dearmor > /etc/apt/keyrings/openvpn-repo-public.gpg && echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/release/2.6 mantic main" > /etc/apt/sources.list.d/openvpn-aptrepo.list && wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
```
Debian12
```bash
mkdir -p /etc/apt/keyrings && apt-get install gpg && sudo curl -fsSL https://swupdate.openvpn.net/repos/repo-public.gpg | gpg --dearmor > /etc/apt/keyrings/openvpn-repo-public.gpg && echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/release/2.6 bookworm main" > /etc/apt/sources.list.d/openvpn-aptrepo.list && wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
```
选UDP 端口65535 DNS选Google         
# 安装完成后执行
```bash
sed -i 's/8.8.4.4/2001:4860:4860::8844/g' /etc/openvpn/server/server.conf; 
sed -i 's/8.8.8.8/8.8.4.4/g' /etc/openvpn/server/server.conf; 
echo '--data-ciphers AES-256-GCM' >> /etc/openvpn/server/server.conf; 
echo 'duplicate-cn' >> /etc/openvpn/server/server.conf
```
# 服务器没有IPV6的话需要禁用IPv6流量
```bash
echo 'push "redirect-gateway ipv6 def1 bypass-dhcp"' >> /etc/openvpn/server/server.conf
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

# 安装openvpn-dco模块
```bash
apt install openvpn-dco-dkms
```
# 编译哔哩哔哩
JDK下载
https://jdk.java.net/23/
```bash
sudo apt install openjdk-22-jdk -y
```
```bash
wget https://github.com/zjns/revanced-cli/releases/download/v4.6.0.1/revanced-cli.jar && wget https://github.com/BiliRoamingX/BiliRoamingX/releases/download/v1.20.3/BiliRoamingX-integrations.apk && wget https://github.com/BiliRoamingX/BiliRoamingX/releases/download/v1.20.3/BiliRoamingX-patches.jar && wget https://dl.hdslb.com/mobile/latest/android64/iBiliPlayer-bili.apk
```
```bash
java -jar revanced-cli.jar patch --merge BiliRoamingX-integrations.apk --patch-bundle BiliRoamingX-patches.jar --signing-levels 2,3 iBiliPlayer-bili.apk
```
