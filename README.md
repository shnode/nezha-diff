修改了使用在线API调用最新的IP定位数据，  
  
一定要先用下面的命令删除之前安装的哪吒镜像  
docker stop nezha-dashboard  
docker rm nezha-dashboard  
  
  
安装git   
sudo apt update && sudo apt install -y git  
  
再clon镜像  
git clone https://github.com/shnode/nezha-diff.git  
  
修改docker-compose.yml里面的配置为你哪吒目录，一般都是这个无需修改，如果你自己diy过的就要修改了  
volumes:  
  - /opt/nezha/dashboard/data:/dashboard/data  
  
  
下载下面2个文件，解压后放到\cmd\dashboard对应的文件夹里面  
https://github.com/nezhahq/admin-frontend/releases  
https://github.com/hamster1963/nezha-dash-v1/releases  
  
再依次执行下面命令就能运行起来了  
cd nezha-diff  
docker compose up -d  
  
后续更新的话，按照下面操作更新  
cd nezha-diff  
git pull  
docker compose down  
docker compose build --no-cache   
  
每次编译都会产生缓存，使用下面命令可以清除  
docker builder prune -af  
  
  
修改版默认使用ipinfo免费额度，每日千次请求，应该是够用的，如果不够用就自己改一下源码使用token  
pkg\geoip\geoip.go里面关于ipinfo的字段  
也可以直接下载离线库放到如下文件夹  
/opt/nezha/dashboard/data  
