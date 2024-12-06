## Service 

## Genrate a Service YAML
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl expose rc helloworld-controller --type=ClusterIP --dry-run  -o yaml > helloworld-svc.yaml
W1206 11:55:47.848190   20983 helpers.go:704] --dry-run is deprecated and can be replaced with --dry-run=client.
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# ls
README.md  helloworld-rc.yaml  helloworld-svc.yaml
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service#
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# ls
README.md  helloworld-rc.yaml  helloworld-svc.yaml
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# cat helloworld-svc.yaml
apiVersion: v1
kind: Service
metadata:
  creationTimestamp: null
  labels:
    app: get-started
  name: helloworld-controller
spec:
  ports:
  - port: 8081
    protocol: TCP
    targetPort: 8081
  selector:
    app: get-started
  type: ClusterIP
status:
  loadBalancer: {}
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl apply -f helloworld-svc.yaml
service/helloworld-controller created
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl get svc
NAME                    TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
helloworld-controller   ClusterIP   10.96.154.196   <none>        8081/TCP   3s
kubernetes              ClusterIP   10.96.0.1       <none>        443/TCP    3h16m
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# ^C
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# curl 10.96.154.196:8081
^C
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# ls
README.md  helloworld-rc.yaml  helloworld-svc.yaml
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl get svc
NAME                    TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
helloworld-controller   ClusterIP   10.96.154.196   <none>        8081/TCP   9m53s
kubernetes              ClusterIP   10.96.0.1       <none>        443/TCP    3h26m
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# vim helloworld-svc.yaml
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl apply -f helloworld-svc.yaml
service/helloworld-controller configured
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl get svc
NAME                    TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
helloworld-controller   NodePort    10.96.154.196   <none>        8081:32305/TCP   10m
kubernetes              ClusterIP   10.96.0.1       <none>        443/TCP          3h27m
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl get nodes -o wide
NAME                STATUS   ROLES           AGE     VERSION   INTERNAL-IP   EXTERNAL-IP   OS-IMAGE                         KERNEL-VERSION      CONTAINER-RUNTIME
k8s-control-plane   Ready    control-plane   3h27m   v1.30.0   172.23.0.3    <none>        Debian GNU/Linux 12 (bookworm)   5.15.0-1074-azure   containerd://1.7.15
k8s-worker          Ready    <none>          3h27m   v1.30.0   172.23.0.4    <none>        Debian GNU/Linux 12 (bookworm)   5.15.0-1074-azure   containerd://1.7.15
k8s-worker2         Ready    <none>          3h27m   v1.30.0   172.23.0.2    <none>        Debian GNU/Linux 12 (bookworm)   5.15.0-1074-azure   containerd://1.7.15
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# curl 172.23.0.3:32305
<h1>Hello From Flask App.!</h1>root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service#
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl get nodes -o wide
NAME                STATUS   ROLES           AGE     VERSION   INTERNAL-IP   EXTERNAL-IP   OS-IMAGE                         KERNEL-VERSION      CONTAINER-RUNTIME
k8s-control-plane   Ready    control-plane   3h30m   v1.30.0   172.23.0.3    <none>        Debian GNU/Linux 12 (bookworm)   5.15.0-1074-azure   containerd://1.7.15
k8s-worker          Ready    <none>          3h30m   v1.30.0   172.23.0.4    <none>        Debian GNU/Linux 12 (bookworm)   5.15.0-1074-azure   containerd://1.7.15
k8s-worker2         Ready    <none>          3h30m   v1.30.0   172.23.0.2    <none>        Debian GNU/Linux 12 (bookworm)   5.15.0-1074-azure   containerd://1.7.15
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl get po -o wide
NAME                          READY   STATUS    RESTARTS   AGE   IP            NODE          NOMINATED NODE   READINESS GATES
helloworld-controller-8qtqx   1/1     Running   0          17m   10.244.1.11   k8s-worker2   <none>           <none>
helloworld-controller-9mqpj   1/1     Running   0          17m   10.244.2.10   k8s-worker    <none>           <none>
helloworld-controller-xhzpw   1/1     Running   0          17m   10.244.2.11   k8s-worker    <none>           <none>
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# curl 172.23.0.3:32305
<h1>Hello From Flask App.!</h1>root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# curl 172.23.0.3:32305/info
<h2> Hey Python Web Server</h2><b> Hostname: </b> helloworld-controller-8qtqx<br/><b> IP Address: </b> 10.244.1.11<br/>root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# curl 172.23.0.3:32305/info
<h2> Hey Python Web Server</h2><b> Hostname: </b> helloworld-controller-xhzpw<br/><b> IP Address: </b> 10.244.2.11<br/>root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# curl 172.23.0.3:32305/info
<h2> Hey Python Web Server</h2><b> Hostname: </b> helloworld-controller-xhzpw<br/><b> IP Address: </b> 10.244.2.11<br/>root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# curl 172.23.0.3:32305/info
<h2> Hey Python Web Server</h2><b> Hostname: </b> helloworld-controller-9mqpj<br/><b> IP Address: </b> 10.244.2.10<br/>root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# curl 172.23.0.3:32305/info
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl get rc
NAME                    DESIRED   CURRENT   READY   AGE
helloworld-controller   3         3         3       19m
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl scale --replicas=1 rc helloworld-controller
replicationcontroller/helloworld-controller scaled
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl get po -o wide
NAME                          READY   STATUS        RESTARTS   AGE   IP            NODE          NOMINATED NODE   READINESS GATES
helloworld-controller-8qtqx   1/1     Terminating   0          19m   10.244.1.11   k8s-worker2   <none>           <none>
helloworld-controller-9mqpj   1/1     Terminating   0          19m   10.244.2.10   k8s-worker    <none>           <none>
helloworld-controller-xhzpw   1/1     Running       0          19m   10.244.2.11   k8s-worker    <none>           <none>
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# curl 172.23.0.3:32305/info
<h2> Hey Python Web Server</h2><b> Hostname: </b> helloworld-controller-xhzpw<br/><b> IP Address: </b> 10.244.2.11<br/>root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# curl 172.23.0.3:32305/info
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl scale --replicas=2 rc helloworld-controller
replicationcontroller/helloworld-controller scaled
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl get po -o wide
NAME                          READY   STATUS    RESTARTS   AGE   IP            NODE          NOMINATED NODE   READINESS GATES
helloworld-controller-mw8kq   1/1     Running   0          2s    10.244.1.12   k8s-worker2   <none>           <none>
helloworld-controller-xhzpw   1/1     Running   0          20m   10.244.2.11   k8s-worker    <none>           <none>
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# curl 172.23.0.3:32305/info
<h2> Hey Python Web Server</h2><b> Hostname: </b> helloworld-controller-xhzpw<br/><b> IP Address: </b> 10.244.2.11<br/>root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# curl 172.23.0.3:32305/info

```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl get svc
NAME                    TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
helloworld-controller   NodePort    10.96.154.196   <none>        8081:32305/TCP   17m
kubernetes              ClusterIP   10.96.0.1       <none>        443/TCP          3h33m
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl describe svc helloworld-controller
Name:                     helloworld-controller
Namespace:                default
Labels:                   app=get-started
Annotations:              <none>
Selector:                 app=get-started
Type:                     NodePort
IP Family Policy:         SingleStack
IP Families:              IPv4
IP:                       10.96.154.196
IPs:                      10.96.154.196
Port:                     <unset>  8081/TCP
TargetPort:               8081/TCP
NodePort:                 <unset>  32305/TCP
Endpoints:                10.244.1.12:8081,10.244.2.11:8081
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl get po -o wide
NAME                          READY   STATUS    RESTARTS   AGE   IP            NODE          NOMINATED NODE   READINESS GATES
helloworld-controller-mw8kq   1/1     Running   0          79s   10.244.1.12   k8s-worker2   <none>           <none>
helloworld-controller-xhzpw   1/1     Running   0          21m   10.244.2.11   k8s-worker    <none>           <none>
```
```
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service# kubectl get po --show-labels
NAME                          READY   STATUS    RESTARTS   AGE   LABELS
helloworld-controller-mw8kq   1/1     Running   0          90s   app=get-started
helloworld-controller-xhzpw   1/1     Running   0          21m   app=get-started
root@ubuntugui:~/docker-k8s-EY-E-02-Dec-2024/02-Kubernetes/06-Service#

```
