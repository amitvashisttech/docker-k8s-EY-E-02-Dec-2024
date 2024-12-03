## Python WebApp:

```
55  docker run -d --name python-webapp-1 python-webapp:v1
   56  docker ps
   57  docker inspect python-webapp-1
   58  docker ps
   59  curl 172.17.0.4
   60  curl 172.17.0.3
   61  curl 172.17.0.2
   62  curl 172.17.0.3
   63  docker ps
   64  curl 172.17.0.6
   65  curl 172.17.0.6:5000
   66  curl 172.17.0.6:5000/info
   67  ls
   68  cd docker-k8s-EY-E-02-Dec-2024/
   69  ls
   70  d 04-Docker-Custom-Images/
   71  ls
   72  cd 04-Docker-Custom-Images/python-webapp/
   73  ls
   74  mkdir v1
   75  mv * v1/
   76  ls
   77  cp -rf v1 v2
   78  ls
   79  cd v2/
   80  ls
   81  vim Dockerfile
   82  ls
   83  docker build -t python-webapp:v2 .
   84  docker images
   85  docker run -d --name python-webapp-2 python-webapp:v2
   86  docker ps
   87  curl 172.17.0.7:5000/info
   88  ls
   89  cd ..
   90  ls
   91  cp -rf v2 v3
   92  ls
   93  cd v3/
   94  ls
   95  vim Dockerfile
   96  ls
   97  docker build -t python-webapp:v3 .
   98  ls
   99  docker run -d --name python-webapp-3 python-webapp:v3
  100  docker ps
  101  curl 172.17.0.8:5000/info
  102  curl 172.17.0.8:3306/info
```
