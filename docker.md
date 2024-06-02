打包、部署应用程序，解决了应用和基础环境异构的问题。

## 服务
```
systemctl start | stop | status | restart docker
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

查看本地镜像  
```
docker images
```

查询镜像  
```
docker search   
```
[docker hub](https://hub.docker.com)  镜像查询网站

删除镜像
```
docker rmi {image-id}
```

## 容器
查看本地容器  
```
docker ps -a
```

创建容器
```
docker run -id -name="*" {image_name} bash 守护式容器  
           -it                           交互式容器  
```

进入容器
```
docker exec -it [-u root] {container_id} bash
```

开启 | 关闭 | 删除 容器
```
docker start | stop | rm {container_id}
```

## 数据卷
将容器中的目录与宿主机的目录绑定，双方的修改会同步  
