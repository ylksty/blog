## root/[operationAndMaintenance](../README.md)/docker/dockerJenkinsNodeWebpackVue
### node/jenkins/docker 标准统一化开发流程
#### 技术选型
* 1.git
* 2.docker 
* 3.npm
* 4.jenkins
* 5.[vuejs-templates](https://github.com/vuejs-templates/webpack)
#### 针对前端开发的问题
* 1.统一环境

#### 部署步骤
* 1.docker build -t ylkget/kl:v2 .
* 2.docker run -d -v $PWD:/data/www -p 7001:7001 -p 8088:8080 --name kl2 ylkget/kl:v2
* 3.docker exec -it kl2 bash
* 4.cd /data/www
* 5.npm run ...