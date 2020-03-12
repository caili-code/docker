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
