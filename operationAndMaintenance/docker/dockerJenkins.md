## root/[operationAndMaintenance](../README.md)/docker/dockerJenkins
## 相关链接
### jenkins docker部署
* [Docker系列之Jenkins自动化部署](https://juejin.im/entry/5958f544f265da6c317d9c8f)
* [一步一步打造jenkins+docker+nodejs项目的自动部署环境](https://www.jianshu.com/p/052a2401595a)
~~~
docker run -d --name jenkins -p 9090:8080 -v /etc/localtime:/etc/localtime -v $(pwd)/timezone:/etc/timezone -v /home/yanglk/dj/jenkins_node:/var/jenkins_home jenkinsci/jenkins:lts
~~~

