## Container Commands

```
  622  docker version
  623  systemctl status docker
  624  docker images
  625  docker run hello-world
  626  docker container ls
  627  docker container ls -a
  628  docker run --name test-av-1 hello-world
  629  docker container ls
  630  docker container ls -a
  631  docker run --name test-av-1 hello-world
  632  docker run --name test-av-2 hello-world
  633  docker run -d  --name test-av-3 hello-world
  634  docker container ls -a
  635  docker run -it --name test-ubuntu-1 ubuntu bash
  636  cat /etc/os-release
  637  docker run -it --name test-ubuntu-1 ubuntu bash
  638  docker run -it --name test-ubuntu-2 ubuntu:18.04 bash
  639  docker run -it --name test-ubuntu-3 ubuntu:18.04 bash
  640  docker ps
  641  docker ps -a
  642  docker start test-ubuntu-1
  643  docker ps -a
  644  docker attach 6d65981b8444
       docker logs -f <container-id / name >
       docker exec -it <container-id / name > ps -ef 
```
