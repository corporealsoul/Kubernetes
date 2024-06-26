anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ minikube start --driver=docker
anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ minikube status



### Deployment of NGINX
anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ kubectl create deployment deploy-nginx --image=nginx:latest
anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ kubectl expose deployment deploy-nginx --port=80 --type=LoadBalancer
anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ kubectl expose deployment deploy-nginx --port=80 --type=NodePort
anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ kubectl get services
anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ minikube service deploy-nginx
anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ kubectl port-forward svc/deploy-nginx --address 0.0.0.0 8080:80

anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ kubectl get pods
anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ kubectl get deployments
anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ kubectl get services
anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ minikube service deploy-nginx --url

anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ kubectl delete service deploy-nginx
anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ kubectl delete deployment deploy-nginx




### Want Windows machine to route traffic to the Minikube cluster through the Ubuntu VM
anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ minikube ip
192.168.49.2

anup@blueprintsandco:~/DevOps-SRE/YEAR2024/Infrastructure-as-Code/ansible/roles/minikube$ ifconfig
br-aac05c942e1a: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.49.1
enp0s8: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.56.104

PS C:\WINDOWS\system32> route add 192.168.49.0 mask 255.255.255.0 192.168.56.104
PS C:\WINDOWS\system32> route print





### Deployment of OWN Application
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ minikube status
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ minikube start
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ minikube addons enable metrics-server
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl create deployment training2023-dec25-00 --image=corporealsoul/kubernetes:TRAINING2023-Dec25-00

anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl get deployments
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl get pods -o wide
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl get services

anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl describe pod training2023-dec25-00-f768d6998-8gstn
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl logs training2023-dec25-00-f768d6998-8gstn

anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl expose deployment training2023-dec25-00 --port=3000 --type=NodePort
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl get services
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ minikube service training2023-dec25-00
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl port-forward svc/training2023-dec25-00 --address 0.0.0.0 3000:3000



### Apply Changes (Rollout)
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ docker build -t corporealsoul/kubernetes:TRAINING2023-Dec25-00-01 .
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ docker images
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ docker push corporealsoul/kubernetes:TRAINING2023-Dec25-00-01

anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl get deployments

anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl set image deployment training2023-dec25-00 TRAINING2023-Dec25-00
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl set image deployment training2023-dec25-00 kubernetes=corporealsoul/kubernetes:TRAINING2023-Dec25-00-01
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl get pods -o wide


### Apply Changes (Rollback)
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl rollout status deployment training2023-dec25-00
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_react$ kubectl rollout undo deployment training2023-dec25-00


### Self Healing
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ express training2023_dec25_00_express
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00$ cd training2023_dec25_00_express
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_express$ npm install
anup@blueprintsandco:~/Kubernetes/YEAR2023/TRAINING2023-Dec25-00/training2023_dec25_00_express$ DEBUG=training2023_dec25_00_express:* npm start


