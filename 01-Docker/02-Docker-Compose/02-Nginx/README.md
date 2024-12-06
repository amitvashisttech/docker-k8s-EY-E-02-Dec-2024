## Docker Compose Intro.
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/02-Nginx# vim docker-compose.yaml
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/02-Nginx# ls
docker-compose.yaml
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/02-Nginx# docker-compose up -d
[+] Running 9/9
 ⠿ web Pulled                                                                                                                                                                 7.3s
   ⠿ da9db072f522 Pull complete                                                                                                                                               1.1s
   ⠿ e10e486de1ab Pull complete                                                                                                                                               1.7s
   ⠿ af9c0e53c5a4 Pull complete                                                                                                                                               1.9s
   ⠿ b2eb2b8af93a Pull complete                                                                                                                                               2.1s
   ⠿ e351ee5ec3d4 Pull complete                                                                                                                                               2.2s
   ⠿ fbbf7d28be71 Pull complete                                                                                                                                               2.5s
   ⠿ 471412c08d15 Pull complete                                                                                                                                               2.7s
   ⠿ a2eb5282fbec Pull complete                                                                                                                                               3.8s
[+] Running 2/2
 ⠿ Network 02-nginx_default  Created                                                                                                                                          0.1s
 ⠿ Container 02-nginx-web-1  Started                                                                                                                                          0.8s
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/02-Nginx# docker-compose ps
NAME                COMMAND                  SERVICE             STATUS              PORTS
02-nginx-web-1      "/docker-entrypoint.…"   web                 running             0.0.0.0:8079->80/tcp, :::8079->80/tcp
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/02-Nginx# docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                                     NAMES
e840e8dfef8e   nginx:alpine   "/docker-entrypoint.…"   47 seconds ago   Up 46 seconds   0.0.0.0:8079->80/tcp, [::]:8079->80/tcp   02-nginx-web-1
e9e447b2ad90   ubuntu         "/bin/bash"              10 minutes ago   Up 8 minutes                                              stg-dir-map-2
1d7e880c10e2   ubuntu         "/bin/bash"              11 minutes ago   Up 11 minutes                                             stg-dir-map-1
8569f0590eab   ubuntu         "/bin/bash"              16 minutes ago   Up 16 minutes                                             stg-dynamic-2
b737118ffa28   ubuntu         "/bin/bash"              18 minutes ago   Up 18 minutes                                             stg-dynamic-1
458073e5968a   ubuntu         "/bin/bash"              25 minutes ago   Up 25 minutes                                             stg-2
c45e5653ded9   ubuntu         "/bin/bash"              27 minutes ago   Up 27 minutes                                             stg-1
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/02-Nginx# docker network ls
NETWORK ID     NAME               DRIVER    SCOPE
cd4025221941   02-nginx_default   bridge    local
d220bfa3d634   bridge             bridge    local
2ae5eac7b6a2   host               host      local
e7bfc732cc83   mybr0              bridge    local
60bedccb484d   none               null      local
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/02-Nginx# docker-compose ps
NAME                COMMAND                  SERVICE             STATUS              PORTS
02-nginx-web-1      "/docker-entrypoint.…"   web                 running             0.0.0.0:8079->80/tcp, :::8079->80/tcp
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/02-Nginx# curl localhost:8079
```
```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/02-Nginx# docker-compose ps
NAME                COMMAND                  SERVICE             STATUS              PORTS
02-nginx-web-1      "/docker-entrypoint.…"   web                 running             0.0.0.0:8079->80/tcp, :::8079->80/tcp
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/02-Nginx# docker-compose stop
[+] Running 1/1
 ⠿ Container 02-nginx-web-1  Stopped                                                                                                                                          0.7s
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/02-Nginx# docker-compose ps
NAME                COMMAND                  SERVICE             STATUS              PORTS
02-nginx-web-1      "/docker-entrypoint.…"   web                 exited (0)
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/02-Nginx# docker-compose rm
? Going to remove 02-nginx-web-1 Yes
[+] Running 1/0
 ⠿ Container 02-nginx-web-1  Removed                                                                                                                                          0.0s
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/02-Nginx#

```
