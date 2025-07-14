![](https://images.weserv.nl/?url=raw.githubusercontent.com/jlesage/docker-templates/master/jlesage/images/handbrake-icon.png&w=110)![](https://images.placeholders.dev/?width=288&height=110&fontFamily=monospace&fontWeight=400&fontSize=52&text=HandBrake&bgColor=rgba(0,0,0,0.0)&textColor=rgba(121,121,121,1))

## **HandBrake汉化版**

**HandBrake 是一种工具，用于将视频从几乎任何格式转换为选区 的现代、广泛支持的编解码器。**

**注意**： 本快速入门中提供的 Docker 命令是一个示例，参数 应进行调整以满足您的需求。

使用以下命令启动 HandBrake docker 容器：

```shell
docker run -d \
    --name=handbrake \
    -p 5800:5800 \
    -v /docker/appdata/handbrake:/config:rw \
    -v /home/user:/storage:ro \
    -v /home/user/HandBrake/watch:/watch:rw \
    -v /home/user/HandBrake/output:/output:rw \
    gz1903/handbrake
```

配置信息：

- `/docker/appdata/handbrake`：存储应用程序的配置、状态、日志和任何需要持久性的文件。
- `/home/user`：包含主机中需要可供应用程序访问的文件。
- `/home/user/HandBrake/watch`：视频自动转换的位置。
- `/home/user/HandBrake/output`：转换后的视频文件的目标。

通过浏览到 来访问 HandBrake GUI。 主机中的文件显示在容器中的文件夹下。`http://your-host-ip:5800` `/storage`

docker-compose:

```shell
services:
  handbrake:
    image: gz1903/handbrake:latest
    container_name: handbrak
    restart: unless-stopped
    ports:
     - 5800:5800
    volumes:
     - ./config:/config
     - ./output:/output
     - ./storage:/storage:ro
     - ./watch:/watch
    environment:
     - LANG=zh_CN.UTF-8
     - TZ=Asia/Shanghai
    devices:
     - /dev/dri:/dev/dri
```



#### 文档

完整文档可在[https://github.com/jlesage/docker-handbrake⁠](https://github.com/jlesage/docker-handbrake).
