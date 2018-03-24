## root/[operationAndMaintenance](../README.md)/linux/testEnv
### [ubuntu](./ubuntu.md)
### git
* sudo add-apt-repository ppa:git-core/ppa
* sudo apt-get update
* sudo apt-get install -y git

### [sftp](./sftp.md)

### docker
* [Ubuntu 16.04安装Docker Compose及简单的使用示例](https://www.centos.bz/2017/08/ubuntu-16-04-install-docker-compose/)

### gitlab 
* [Ubuntu Docker 简单安装 GitLab](http://www.cnblogs.com/xishuai/p/ubuntu-install-gitlab-with-docker.html)
~~~
sudo docker run --detach \
--hostname 192.168.0.118 \
--publish 443:443 --publish 88:80 --publish 8888:22 \
--name gitlab \
--restart always \
--volume /srv/gitlab/config:/etc/gitlab \
--volume /srv/gitlab/logs:/var/log/gitlab \
--volume /srv/gitlab/data:/var/opt/gitlab \
gitlab/gitlab-ce:latest
~~~
* 用户加入了组，项目权限就在组上设置