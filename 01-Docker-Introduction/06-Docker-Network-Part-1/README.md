```
  345  docker kill $(docker ps -qa)
  346  docker rm $(docker ps -qa)
  347  ls
  348  docker run -d --name test-1 nginx
  349  docker images
  350  docker ps
  351  docker inspect 95ec4bd89d83
  352  curl 172.17.0.2
  353  ls
  354  docker ps
  355  curl localhost
  356  ip a
  357  curl 10.4.3.161
  358  ip route
  359  curl 172.17.0.2
  360  ip addr
  361  docker ps
  362  docker run -d --name test-2 nginx
  363  ip addr
  364  ls
  365  docker ps
  366  docker run -d --name test-3 -p 8080:80  nginx
  367  apt-get install net-tools -y
  368  netstat -tulnp
  369  systemctl status docker
  370  curl 172.17.0.4:80
  371  curl localhost:80
  372  curl localhost:8080
  373  ip addr
  374  curl 10.4.3.161:8080
  375  docker ps
  376  docker run -d --name test-4 -p 8080:80  nginx
  377  docker run -d --name test-5 -P  nginx
  378  docker ps
  379  curl 10.4.3.161:8080
  380  curl 10.4.3.161:32768
```
