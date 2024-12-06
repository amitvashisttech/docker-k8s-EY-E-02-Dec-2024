```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# docker-compose up -d
[+] Running 7/7
 ⠿ db Pulled                                                                                                                                                                  6.6s
   ⠿ bc0965b23a04 Already exists                                                                                                                                              0.0s
   ⠿ d7ad38c6dd97 Pull complete                                                                                                                                               0.9s
   ⠿ 4f4fb700ef54 Pull complete                                                                                                                                               1.1s
   ⠿ 79b49624e34b Pull complete                                                                                                                                               1.7s
   ⠿ 7d9f97915db2 Pull complete                                                                                                                                               3.2s
   ⠿ 9bd25d4f7b77 Pull complete                                                                                                                                               3.3s
[+] Running 4/4
 ⠿ Network 03-mywebapp_default     Created                                                                                                                                    0.1s
 ⠿ Container 03-mywebapp-proxy-1   Started                                                                                                                                    1.4s
 ⠿ Container 03-mywebapp-db-1      Started                                                                                                                                    1.3s
 ⠿ Container 03-mywebapp-python-1  Started                                                                                                                                    1.4s
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# docker-compose ps
NAME                   COMMAND                  SERVICE             STATUS              PORTS
03-mywebapp-db-1       "httpd-foreground"       db                  running             0.0.0.0:3306->80/tcp, :::3306->80/tcp
03-mywebapp-proxy-1    "/docker-entrypoint.…"   proxy               running             0.0.0.0:8079->80/tcp, :::8079->80/tcp
03-mywebapp-python-1   "python app.py"          python              running             0.0.0.0:8080->5000/tcp, :::8080->5000/tcp
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# curl localhost:3306
<html><body><h1>It works!</h1></body></html>
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# curl localhost:8079
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
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# curl localhost:8080
Hello, World!root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# curl localhost:8080/info
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp#
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# docker-compose ps
NAME                   COMMAND                  SERVICE             STATUS              PORTS
03-mywebapp-db-1       "httpd-foreground"       db                  running             0.0.0.0:3306->80/tcp, :::3306->80/tcp
03-mywebapp-proxy-1    "/docker-entrypoint.…"   proxy               running             0.0.0.0:8079->80/tcp, :::8079->80/tcp
03-mywebapp-python-1   "python app.py"          python              running             0.0.0.0:8080->5000/tcp, :::8080->5000/tcp
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# docker-compose kill python
[+] Running 1/1
 ⠿ Container 03-mywebapp-python-1  Killed                                                                                                                                     0.7s
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# docker-compose ps
NAME                   COMMAND                  SERVICE             STATUS              PORTS
03-mywebapp-db-1       "httpd-foreground"       db                  running             0.0.0.0:3306->80/tcp, :::3306->80/tcp
03-mywebapp-proxy-1    "/docker-entrypoint.…"   proxy               running             0.0.0.0:8079->80/tcp, :::8079->80/tcp
03-mywebapp-python-1   "python app.py"          python              exited (137)
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# docker-compose rm python
? Going to remove 03-mywebapp-python-1 Yes
[+] Running 1/0
 ⠿ Container 03-mywebapp-python-1  Removed                                                                                                                                    0.0s
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# docker-compose ps
NAME                  COMMAND                  SERVICE             STATUS              PORTS
03-mywebapp-db-1      "httpd-foreground"       db                  running             0.0.0.0:3306->80/tcp, :::3306->80/tcp
03-mywebapp-proxy-1   "/docker-entrypoint.…"   proxy               running             0.0.0.0:8079->80/tcp, :::8079->80/tcp
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# docker-compose up -d
[+] Running 3/3
 ⠿ Container 03-mywebapp-python-1  Started                                                                                                                                    0.5s
 ⠿ Container 03-mywebapp-db-1      Running                                                                                                                                    0.0s
 ⠿ Container 03-mywebapp-proxy-1   Running                                                                                                                                    0.0s
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# docker-compose up -d
[+] Running 3/0
 ⠿ Container 03-mywebapp-proxy-1   Running                                                                                                                                    0.0s
 ⠿ Container 03-mywebapp-python-1  Running                                                                                                                                    0.0s
 ⠿ Container 03-mywebapp-db-1      Running                                                                                                                                    0.0s
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# docker-compose up -d
[+] Running 3/0
 ⠿ Container 03-mywebapp-proxy-1   Running                                                                                                                                    0.0s
 ⠿ Container 03-mywebapp-db-1      Running                                                                                                                                    0.0s
 ⠿ Container 03-mywebapp-python-1  Running                                                                                                                                    0.0s
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# docker-compose ps
NAME                   COMMAND                  SERVICE             STATUS              PORTS
03-mywebapp-db-1       "httpd-foreground"       db                  running             0.0.0.0:3306->80/tcp, :::3306->80/tcp
03-mywebapp-proxy-1    "/docker-entrypoint.…"   proxy               running             0.0.0.0:8079->80/tcp, :::8079->80/tcp
03-mywebapp-python-1   "python app.py"          python              running             0.0.0.0:8080->5000/tcp, :::8080->5000/tcp
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# curl localhost:8080/info
Welcome to the world of Docker based Python WebServer 

```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# docker-compose kill
[+] Running 3/3
 ⠿ Container 03-mywebapp-db-1      Killed                                                                                                                                     1.2s
 ⠿ Container 03-mywebapp-python-1  Killed                                                                                                                                     0.8s
 ⠿ Container 03-mywebapp-proxy-1   Killed                                                                                                                                     1.2s
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp# docker-compose rm
? Going to remove 03-mywebapp-python-1, 03-mywebapp-proxy-1, 03-mywebapp-db-1 Yes
[+] Running 3/0
 ⠿ Container 03-mywebapp-db-1      Removed                                                                                                                                    0.0s
 ⠿ Container 03-mywebapp-proxy-1   Removed                                                                                                                                    0.0s
 ⠿ Container 03-mywebapp-python-1  Removed                                                                                                                                    0.0s
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Docker-Compose/03-MyWebApp#
```

