# ITDB-docker
Use ITDB by  docker

##build images
docker build -t itdb:v1.0 .

##start container

docker run --name itdb  -p 80:80 -d itdb:v1.0
