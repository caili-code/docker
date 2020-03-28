# docker
docker相关

docker start [containerID/Names] # 启动容器


Mysql5.6以上的版本修改了Password算法，需要更新密码算法，操作步骤如下：

mysql> ALTER user 'root'@'%' IDENTIFIED BY '123456' PASSWORD EXPIRE NEVER;
Query OK, 0 rows affected (0.09 sec)

mysql> ALTER user 'root'@'%' IDENTIFIED WITH mysql_native_password BY '123456';
Query OK, 0 rows affected (0.01 sec)
 
mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.01 sec)

启动mysql容器:docker start mysql

启动redis容器:docker run -itd --name redis-test -p 6379:6379 redis

通过 redis-cli 连接测试使用 redis 服务:docker exec -it redis-test /bin/bash

docker run -p 8081:8081 -t myp:7.0 -link=mysql myp


需要先在本地打包，后mysql修改为172.0.02

linux 安装docker：
由于apt官方库里的docker版本可能比较旧，所以先卸载可能存在的旧版本：
$ sudo apt-get remove docker docker-engine docker-ce docker.io
更新apt包索引：
$ sudo apt-get update
安装以下包以使apt可以通过HTTPS使用存储库（repository）：
$ sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
添加Docker官方的GPG密钥：
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
使用下面的命令来设置stable存储库：
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
再更新一下apt包索引：
$ sudo apt-get update
安装最新版本的Docker CE：
$ sudo apt-get install -y docker-ce
     

错误提示：

E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavialable)
E: Unable to acquire the dpkg fronted lock (/var/lib/dpkg/lock-frontend), is another process using it?

出现这个问题可能是有另外一个程序正在运行，导致资源被锁不可用。而导致资源被锁的原因可能是上次运行安装或更新时没有正常完成，才导致这个问题发生。

解决方法：
删掉之前遗留下来的进程

sudo rm /var/cache/apt/archives/lock-frontend
sudo  rm /var/lib/dpkg/lock-frontend


验证docker
查看docker服务是否启动：
$ systemctl status docker

mysql持久化:
1.拉取mysql镜像文件
拉取最新版本(也可以指定版本)

docker pull mysql
1
检查本地镜像文件

docker images
1


2.创建配置文件
创建配置文件存放位置 和数据映射位置

mkdir -p /mysql/config /mysql/data
1
创建编辑配置文件

vi /mysql/config/my.conf
1
my.conf配置文件内容如下

[mysqld]
user=mysql
character-set-server=utf8
default_authentication_plugin=mysql_native_password

[client]
default-character-set=utf8

[mysql]
default-character-set=utf8
————————————————

3.启动容器
docker run -d -p 3306:3306 --restart always --privileged=true --name dream_mysql -e MYSQL_ROOT_PASSWORD=123456 -v /mysql/config/my.conf:/etc/my.cof -v=/mysql/data:/var/lib/mysql mysql
虚拟机配置成桥接模式就可以和桌面通讯了

springboot jar包打成镜像:docker build -t live:v1 .

运行springbooot在docker:docker run -d -p 8081:8081 live:v1 livep
查看springboot的日志:docker logs --since 30m CONTAINER_ID




