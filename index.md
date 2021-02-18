安装docker：
curl -fsSL https://get.docker.com -o get-docker.sh  && \
bash get-docker.sh
service docker restart
systemctl enable docker


面板添加节点
kr158.asoobear.com;443;2;ws;;path=/hls/cctv5phd.m3u8|kr158.asoobear.com

中转地址
kr158.asoobear.com;443;2;ws;;path=/hls/cctv5phd.m3u8|host=kr158.asoobear.com|relayserver=122.192.189.41|

outside_port=10016

后端数据库对接：
docker run -d --name=v2ray \
-e speedtest=6  -e api_port=2333 -e usemysql=1 -e downWithPanel=0 \
-e node_id=42 -e sspanel_url=https://v.oobear.vip -e key=izchuan  -e MYSQLHOST=64.64.244.11  \
-e MYSQLDBNAME=v_oobear_vip -e MYSQLUSR=v_oobear_vip -e MYSQLPASSWD=xS8hZiekpW64FKL3 -e MYSQLPORT=3306 \
--log-opt max-size=10m --log-opt max-file=5 \
--network=host --restart=always \
izchuan/v2ray_v3:go_pay


一键中转：
wget -qO natcfg.sh http://arloor.com/sh/iptablesUtils/natcfg.sh && bash natcfg.sh

中转项目：https://github.com/arloor/iptablesUtils

如果你参数输入错误，想重新配置
可以输入：
docker rm -f v2ray

关闭防火墙
查看防火墙状态：firewall-cmd --state
停止firewall：systemctl stop firewalld.service
禁止firewall开机启动：systemctl disable firewalld.service

安装 BBR
wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod 

+x tcp.sh && ./tcp.sh
