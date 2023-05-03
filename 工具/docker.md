docker: 打包、部署应用程序，解决了应用和基础环境异构的问题。

打包应用、操作系统、库、依赖。  

## 服务
```
systemctl start | stop | status | restart | enable docker
```

## 镜像
镜像代理
```
sudo mkdir -p /etc/docker
sudo vim /etc/docker/daemon.json 
输入以下内容，添加镜像
{
  "registry-mirrors": ["https://obx2wnav.mirror.aliyuncs.com"]
}
sudo systemctl daemon-reload
sudo systemctl restart docker
```

```
查看本地镜像：docker images
查询镜像：docker search
[docker hub](https://hub.docker.com)  镜像查询网站
拉取镜像：docker pull 
更新后台镜像：docker load -i  | tag | push
删除镜像：docker rmi {image-id}
```
## 容器
镜像运行的实体  
### 命令
```
创建容器
docker run -it --name="*" {image_name} bash  前台交互式启动，exit退出之后容器关闭
docker run -d  --name="*" {image_name}           后台守护式启动 

查看本地容器：docker ps -a
进入容器：docker exec -it [-u root] {container_id} bash
开启 | 关闭 | 删除 容器：docker start | stop | rm {container_id}
拷贝文件：docker cp {container_id}:容器内文件或目录 本地文件或目录
查看容器信息：docker inspect
查看日志：docker logs
```

### DockerFile
```
Cmd 容器默认启动命令  
Entrypoint 进入点
当Entrypoint 和Cmd同时存在时，Cmd会被当作Entrypoint的参数
docker exec -it entrypoint sh {image_id} "*" 会覆盖Entrypoint和Cmd
```

## 数据卷
容器删除后，数据会丢失  
数据卷挂载，将容器中的目录（或文件）与宿主机的目录（或文件）绑定，双方的修改会同步  
```
docker run -it --name="*" {image_name} -v 宿主机目录(文件)：容器内目录(文件) bash  

[pc-wg ~]# docker run -d -p 3306:3306 --name=mysql -e MYSQL_ROOT_PASSWORD=296513 mysql:5.6
```

## 网络
```
docker network ls
```