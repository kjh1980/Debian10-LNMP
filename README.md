先重新DD一下debian10<br>

bash <(wget --no-check-certificate -qO- 'https://github.com/GouGoGoal/SSPanel-Uim/raw/master/InstallNET.sh') -d 10 -v 64 -a<br>
国内源 --mirror 'http://mirrors.ustc.edu.cn/debian/'<br>

香港源 --mirror 'http://ftp.hk.debian.org/debian/'<br>
日本源 --mirror 'http://ftp.jp.debian.org/debian/'<br>
台湾源 --mirror 'http://ftp.tw.debian.org/debian/'<br>


#安装常用命令<br>
apt -y install wget vim curl gnupg lsb-release<br>

#添加nginx主线源<br>
echo "deb http://nginx.org/packages/mainline/debian  buster nginx" >>/etc/apt/sources.list<br>
curl -fsSL https://nginx.org/keys/nginx_signing.key |  apt-key add -<br>
apt-key fingerprint ABF5BD827BD9BF62<br>
apt update<br>
apt -y install nginx<br>
#安装完毕后更改 /lib/systemd/system/nginx.service<br>
[Service]<br>
ExecStartPost=/bin/sleep 0.1  <br>
#延迟0.1毫秒<br>
systemctl daemon-reload<br>
#可以避免出现Can't open PID file /run/nginx.pid (yet?) 提示<br>


mysql 源的地址   https://dev.mysql.com/downloads/repo/apt/<br>
#添加mysql源<br>
wget  https://dev.mysql.com/get/mysql-apt-config_0.8.14-1_all.deb<br>
dpkg -i<br>
选择OK<br>

#安装php<br>
apt -y install php7.3-fpm php7.3-mysql php7.3-curl php7.3-gd php7.3-mbstring php7.3-xml php7.3-xmlrpc php7.3-opcache php7.3-zip php7.3 php7.3-json php7.3-bz2 php7.3-bcmath<br>
#添加软链接，方便重启服务<br>
ln -s  /lib/systemd/system/php7.3-fpm.service  /etc/systemd/system/php.service<br>


