``` 
 1629  cd 20-Helm-Custom-Charts/
 1631  mkdir v1
 1633  cd v1/
 1635  helm  create mywebapp
 1637  apt-get install tree -y
 1639  tree .
 1641  cd mywebapp/
 1643  vim Chart.yaml
 1645  cat templates/service.yaml
 1647  tree templates/
 1649  vim values.yaml
 1651  cd ..
 1653  helm list
 1654  helm install my-webapp-a mywebapp --dry-run
 1655  helm install my-webapp-a mywebapp
 1656  helm list
 1657  kubectl get deploy
 1658  kubectl get pd
 1659  kubectl get po
 1660  kubectl get svc
 1661  kubectl get sa
```
