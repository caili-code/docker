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
验证docker
查看docker服务是否启动：
$ systemctl status docker


