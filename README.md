# ITDB-docker
Use ITDB by  docker

ITDB项目源码：
https://github.com/sivann/itdb
参考资料：
http://www.sivann.gr/software/itdb/

## build images
docker build -t itdb:v1.0 .

## start container

docker run --name itdb  -p 80:80 -d itdb:v1.0
