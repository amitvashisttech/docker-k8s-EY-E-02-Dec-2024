```
docker service create --name my_web_2 --replicas 3 --publish published=8005,target=8081 amitvashist7/python-web-app
```


```
curl 172.17.0.2:8005/info
```