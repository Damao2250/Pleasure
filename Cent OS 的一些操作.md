# 打开/关闭防火墙
+ systemctl start/stop firewalld

# 安装 wget
+ yum install wget

# 安装 nodejs
+ curl -sL https://rpm.nodesource.com/setup_8.x | bash -
+ sudo yum install -y nodejs
+ node -v
+ npm -v

# 检验安装
+ rpm -qa|grep lrzsz
+ rz   // 上传文件

# 重命名
+ mv node_12.10.0 node

# 移动文件
+ mv node /usr/loacl

# 删除文件
+ rm -rf node

# 配置 Nginx
启动
+ systemctl start nginx.service
结束
+ systemctl stop nginx.service
重启
+ systemctl restart nginx.service

开机启动
+ cd /lib/systemd/system/
+ vim nginx.service
+ 设置 PrivateTmp=true

修改后重启
+ nginx -s reload

查看配置是否有问题
+ nginx -tzwe4r  

# 安装mysql 5.7
+ wget https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm
+ rpm -ivh mysql80-community-release-el7-3.noarch.rpm
+ yum install -y mysql-community-server

运行数据库
+ systemctl start mysqld     // 开启数据库
+ systemctl enable mysqld    // 开机自启数据库

停止服务
+ service mysqld stop

查看初开密码
+ grep 'password' /var/log/mysqld.log
或
+ vi /var/log/mysqld.log

修改初始密码
 1.先通过初始密码登录
 mysql -u root -p
 2.修改密码
 ALTER USER 'root'@'localhost' IDENTIFIED BY 'Root123!@#'   // 密码必须大小写字母数字组合
(上面只是可以在服务器上访问，Mysql默认不允许远程登录，所以必须设置下，并且防火墙开放3306端口)

