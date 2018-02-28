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

#### 步骤
* docker build -t josephkl/kl:v3 .
  * 或 docker pull josephkl/kl
* docker run -d -v $PWD:/www -p 7001:7001 --name kl3 josephkl/kl:v3
* docker exec -it kl3 bash
* cd /www