## root/[operationAndMaintenance](../README.md)/[docker](./README.md)/laradock
### 相关链接
* <http://laradock.io/introduction/>
### 相关操作
  * docker-compose up -d workspace nginx mysql jenkins
  * docker-compose down
  * docker-compose build
  
### .env 说明
  * DOCKER_HOST_IP // xdebug 通过调用这个接口，和ide通信
  
### 关于egg的部署
* 1.php-fpm容器和其他环境隔离，没有node npm环境,以www-data身份执行
* 2.在php-fpm环境，hosts映射容器宿主的ip 3.3.3.3 egg
* 3.容器外监听workspace容器的7001端口
* 4.php-fpm容器 file_get_contents('http://egg:7001/') 成功!

