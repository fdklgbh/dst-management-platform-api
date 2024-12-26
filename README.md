# [中文文档] | [[English README]](README_EN.md)
## :watermelon: 使用方法
>**建议使用 Ubuntu 24系统，低版本系统可能会出现GLIBC版本报错**  
```shell
# 执行以下命令，根据系统提示输入并回车
cd ~ && wget https://dmp-1257278878.cos.ap-chengdu.myqcloud.com/run.sh && chmod +x run.sh && ./run.sh
```
**更新方法**
```shell
cd ~ && ./run.sh
```
_根据提示输入4_
```shell
# root@VM-0-16-ubuntu:~# cd ~ && ./run.sh
# 请输入需要执行的操作(Please enter the operation to be performed): 
# [0]: 下载并启动服务(Download and start the service) 
# [1]: 启动服务(Start the service) 
# [2]: 关闭服务(Stop the service) 
# [3]: 重启服务(Restart the service) 
# [4]: 更新服务(Update the service)
```
如果下载了发行版，则执行以下命令：
```shell
# -c 为开启日志，建议开启
nohup ./dmp -c > dmp.log 2>&1 &
```
默认启动端口为80，如果您想修改，则修改启动命令：
```shell
# 修改端口为8888
nohup ./dmp -c -l 8888 > dmp.log 2>&1 &
```
也可以指定数据库文件的存储目录  
```shell
# 开启控制台输出，监听8899端口，DstMP.sdb的存储位置为 ./config/DstMP.sdb
nohup ./dmp -c -l 8899 -s ./config > dmp.log 2>&1 &
```
**docker部署方式**  
首先在package页面获取docker镜像tag
```shell
# 绑定80端口
docker run -itd --name dmp -p 80:80 \
-v /app/config:/root/config \
-v /etc/localtime:/etc/localtime:ro \
-v /etc/timezone:/etc/timezone:ro \
ghcr.io/miracleeverywhere/dst-management-platform-api:tag
```
```shell
# 绑定8000端口
docker run -itd --name dmp -p 8000:80 \
-v /app/config:/root/config \
-v /etc/localtime:/etc/localtime:ro \
-v /etc/timezone:/etc/timezone:ro \
ghcr.io/miracleeverywhere/dst-management-platform-api:tag
```
---

## :grapes: 默认用户名密码
>登录后请尽快修改密码
>
>>admin/123456

---

## :cherries: 平台截图
![home-zh](docs/images/home-zh.png)
  

![mobile-zh](docs/images/mobile-zh.png)
  

![room-zh](docs/images/room-zh.png)
  

![world-zh](docs/images/world-zh.png)


![mod1-zh](docs/images/mod1-zh.jpg)


![mod2-zh](docs/images/mod2-zh.jpg)
  

![player-zh](docs/images/player-zh.png)
  

![statistics-zh](docs/images/statistics-zh.png)
  

![menu-tools-zh](docs/images/menu-tools-zh.png)  

---

## :strawberry: 文件介绍
```text
.
├── dmp                 # 主程序
├── dmp.log             # 请求日志
├── dmpProcess.log      # 运行日志
├── DstMP.sdb           # 数据库
├── manual_install.sh   # 饥荒手动安装脚本
└── run.sh              # 运行脚本
```

---

## :peach: 项目介绍
```text
.
├── app
│   ├── auth                    # 登录鉴权
│   ├── externalApi             # 外部接口
│   ├── home                    # 首页
│   ├── logs                    # 日志
│   ├── setting                 # 配置
│   └── tools                   # 工具
├── dist                        # 静态资源
│   ├── assets 
│   ├── index.html
│   ├── index.html.gz
│   └── vite.png
├── docker                      # 容器镜像
│   ├── Dockerfile
│   └── entry-point.sh
├── docs                        # 帮助文档
│   └── images
├── DstMP.sdb                   # 数据库
├── go.mod
├── go.sum
├── LICENSE
├── main.go
├── README.md
├── scheduler                   # 定时任务
│   ├── init.go
│   └── schedulerUtils.go
└── utils                       # 工具集
    ├── constant.go
    ├── exceptions.go
    ├── install.go
    ├── logger.go
    ├── scripts.go
    └── utils.go
```
##  :sparkling_heart: 致谢
本项目[前端页面](https://github.com/miracleEverywhere/dst-management-platform-web)基于**koi-ui**二次开发，感谢开源 [@yuxintao6](https://github.com/yuxintao6)  
[[koi-ui gitee]](https://gitee.com/BigCatHome/koi-ui)  
[[koi-ui github]](https://github.com/yuxintao6/koi-ui)  
