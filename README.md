# docker
docker相关

docker start [containerID/Names] # 启动容器


这是因为Mysql5.6以上的版本修改了Password算法，这里需要更新密码算法，操作步骤如下：

mysql> ALTER user 'root'@'%' IDENTIFIED BY '123456' PASSWORD EXPIRE NEVER;
Query OK, 0 rows affected (0.09 sec)
mysql>
mysql> ALTER user 'root'@'%' IDENTIFIED WITH mysql_native_password BY '123456';
Query OK, 0 rows affected (0.01 sec)
mysql> 
mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.01 sec)
 
mysql>
————————————————
版权声明：本文为CSDN博主「Fatal Error」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/gf0515/article/details/80466213
