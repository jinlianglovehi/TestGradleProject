

#### docker 使用总结


#### 需要切换到root 用户
sudo su -                       //切换到root
service docker start      //启动docker service
docker images              //显示所有images
docker run hello-world  //重新运行


#### docker 搜索

> docker  search ubuntu

#### docker 下载

> docker pull learn/tutorial

#### docker run

> 有两个参数,第一个参数: 镜像名,,第二个参数 执行的命令
> docker run learn/tutorial echo "hello word"

#### 在镜像中安装新的程序

在执行apt-get 命令的时候，要带上-y参数。
如果不指定-y参数的话，apt-get命令会进入交互模式，需
要用户输入命令来进行确认，但在docker环境中是无法响应这种交互的
> docker run learn/tutorial apt-get install -y ping

#### 获取操作的 id

> docker ps -l

> docker commit 698 learn/ping

#### 发布自己的镜像文件

>  docker push learn/ping


#### ----------------- docker cmd start  ----------------------------

docker ps //查看运行的容器
docker images//查看已有的images
docker search XXX//搜索images,Search the Docker Hub for images
docker pull xxxx//下载某个镜像
docker push xxxx//推送镜像
docker run xxx /bin/bash //一般xxx为系统image，例如ubuntu或者fedora
docker run xxx sh //这个是busybox
docker start container-id //启动容器
docker stop container-id //停掉容器
docker attach container-id //表示再次attach到一个正在运行的容器上，比如一般使用Start启动容器后会自动退出，此时就可以使用该命令进入容器


#### ----------------- docker cmd end --------------------------