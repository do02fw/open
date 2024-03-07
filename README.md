https://openvpn.net/community-resources/reference-manual-for-openvpn-2-6/#encryption-options


mkdir -p /etc/apt/keyrings

curl -fsSL https://swupdate.openvpn.net/repos/repo-public.gpg | gpg --dearmor > /etc/apt/keyrings/openvpn-repo-public.gpg

echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/openvpn-repo-public.gpg] http://build.openvpn.net/debian/openvpn/testing jammy main" > /etc/apt/sources.list.d/openvpn-aptrepo.list



mtu-disc yes

2606:4700:4700::1001
