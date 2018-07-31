## root/[operationAndMaintenance](../README.md)/mysql/pit
### mysql 创建账号
~~~
* ALTER USER 'root'@'%' IDENTIFIED BY 'passwd';
* ALTER USER root@localhost IDENTIFIED BY 'passwd';
* FLUSH PRIVILEGES;
* GRANT ALL PRIVILEGES ON *.* TO 'test'@'%' IDENTIFIED BY 'passwd' WITH GRANT OPTION;
~~~

### docker里面都是远程连接

### 命令行
* 显示用户权限 show grants for jeffrey@'%';