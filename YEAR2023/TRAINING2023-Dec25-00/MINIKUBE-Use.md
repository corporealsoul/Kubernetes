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