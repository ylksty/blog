## root/[operationAndMaintenance](../README.md)/docker/docker
### 最佳实例
- `docker build -t ylkget/kl:v1 .`

- docker run
  - 运行并,进入容器内部 `docker run -it ylkget/kl:v1 bash`
  - 启动容器,并后台运行 `docker run -d ylkget/kl:v1 sh -c "do echo hello world;"`
  - 查看镜像支持的环境变量 `docker run ylkget/kl:v1 env`
  - `docker run -d -v $PWD:/data/www -p 7001:7001 -p 8088:8080 --name kl ylkget/kl:v1`

- 容器操作
  - 查看 `docker ps -a`
  - 删除所有 `docker rm $(docker ps -a | awk '{print $1}')`
  - 批量清理已经停止的容器 `docker container prune`
  - 停止 `docker stop`
  - 停止所有正在运行的容器 `docker kill $(docker ps -q)`
  - 开启 `docker start`
  - 重启 `docker restart`
  - `docker attach`
  - 进入运行中容器内部 `docker exec -it kbB bash`

- docker images
  - 查看 `docker images -a`
  - 删除全部 `docker rmi $(docker images | grep -v RESPOSITORY | awk '{print $3}')`
  - 批量清理临时镜像 `docker image prune`
  
- `docker logs`

- `docker history`

### 拾遗
