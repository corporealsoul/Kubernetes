anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ minikube status



### Deployment of NGINX
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl create deployment deploy-nginx --image=nginx:latest
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl expose deployment deploy-nginx --port=80 --type=LoadBalancer
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl expose deployment deploy-nginx --port=80 --type=NodePort
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ minikube service deploy-nginx


### Want  Windows machine to route traffic to the Minikube cluster through the Ubuntu VM
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ minikube ip
192.168.49.2

anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ ifconfig
br-aac05c942e1a: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.49.1
enp0s8: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.56.104

PS C:\WINDOWS\system32> route add 192.168.49.0 mask 255.255.255.0 192.168.56.104




anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl delete service deploy-nginx

anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl get deployments
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl get pods
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl get services



### Minikube Dashboard
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ minikube dashboard
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ kubectl proxy --address='0.0.0.0' --disable-filter=true
http://192.168.56.104:8001/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/

💡  Some dashboard features require the metrics-server addon. To enable all features please run:
        minikube addons enable metrics-server
anup@blueprintsandco:~$ minikube addons enable metrics-server


### 
