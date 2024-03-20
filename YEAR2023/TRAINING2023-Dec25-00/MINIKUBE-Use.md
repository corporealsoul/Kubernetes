anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ minikube status



### Deployment of NGINX
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl create deployment deploy-nginx --image=nginx:latest
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl expose deployment deploy-nginx --port=80 --type=LoadBalancer
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl expose deployment deploy-nginx --port=80 --type=NodePort
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ minikube service deploy-nginx
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ minikube ip
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl delete service deploy-nginx

anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl get deployments
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl get pods
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl get services



### Minikube Dashboard
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ minikube dashboard
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl proxy --address='0.0.0.0' --disable-filter=true
http://192.168.56.104:8001/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/



### 
