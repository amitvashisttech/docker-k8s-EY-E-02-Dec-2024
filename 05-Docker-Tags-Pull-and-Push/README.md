```
  288  docker images
  289  docker push python-webapp:v3
  290  docker login -u amitvashist7
  291  docker push python-webapp:v3
  292  docker tag python-webapp:v3 amitvashist7/docker-k8s-ey-e-02-dec-2024-python-webapp:v3
  293  docker images
  294  docker push amitvashist7/docker-k8s-ey-e-02-dec-2024-python-webapp:v3
  295  docker tag python-webapp:v2 amitvashist7/docker-k8s-ey-e-02-dec-2024-python-webapp:v2
  296  docker tag python-webapp:v1 amitvashist7/docker-k8s-ey-e-02-dec-2024-python-webapp:v1
  297  docker images
  298  docker push amitvashist7/docker-k8s-ey-e-02-dec-2024-python-webapp:v2
  299  docker push amitvashist7/docker-k8s-ey-e-02-dec-2024-python-webapp:v1
  300  ls
  301  docker kill $(docker ps -q)
  302  docker rm $(docker ps -qa)
  303  docker images
  304  docker images -q
  305  docker rmi $(docker images -q)
  306  docker rmi $(docker images -q) --force
  307  docker images
  308  ls
  309  ld
  310  ls
  311  docker run -d amitvashist7/docker-k8s-ey-e-02-dec-2024-python-webapp:v3
  312  docker ps
  313  curl 172.17.0.2:5000
  314  curl 172.17.0.2:5000/info
```
