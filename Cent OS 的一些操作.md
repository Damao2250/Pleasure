# 安装 wget
+ yum install wget

# 安装 nodejs
+ curl -sL https://rpm.nodesource.com/setup_8.x | bash -
+ sudo yum install -y nodejs
+ node -v
+ npm -v

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
+ nginx -t