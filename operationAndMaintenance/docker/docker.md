## root/[operationAndMaintenance](../README.md)/docker/docker
### 最佳实例
- `docker build -t ylkget/kl:v1 .`

- docker run
  - docker run --rm -it ylkget/kl:v3 bash
  - docker run -d -v $PWD:/www -p 7001:7001 -p 8088:8080 --name k3 ylkget/kl:v3

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

- `docker inspect`
  - 查看已存在的容器所挂载的目录 `docker inspect container_name | grep Mounts -A 20`
  - Once you have the ID, look for its IP address with: `docker inspect -f "{{ .NetworkSettings.IPAddress }}" <ID>`

### 拾遗

