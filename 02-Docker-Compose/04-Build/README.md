```
  603  mkdir 04-Build
  604  ls
  605  cd 04-Build/
  606  ls
  607  cp -rf ../../01-Docker-Introduction/04-Docker-Custom-Images/apache/v4/* .
  608  ls
  609  vim info.html
  610  s
  611  ls
  612  vim docker-compose.yaml
  613  ls
  614  docker-compose up -d
  615  docker-compose ps
  616  curl localhost:8085
  617  curl localhost:8085/info.html
  618  vim info.html
  619  docker-compose up -d
  620  docker-compose up -d --build
  621  docker-compose ps
  622  curl localhost:8085/info.html
  623  docker-compose up -d --build --force-recreate
  624  docker-compose ps
  625  curl localhost:8085/info.html

```
