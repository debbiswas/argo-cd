# argo-cd
argo-cd demo

Install Argo-cd - following steps to install argo-cd in your kubernetes cluster

kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.1.0-rc3/manifests/install.yaml

Check all install component 

kubectl get all -n argocd

Change "service/argocd-server" type as NodePort from ClusterIP

kubectl edit service/argocd-server -n argocd


root@k8s-master: kubectl describe service/argocd-server -n argocd | grep -i type

Type:                     NodePort

root@k8s-master:


Get argocd-server service details


root@k8s-master: kubectl get service/argocd-server -n argocd

NAME            TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)                      AGE

argocd-server   NodePort   10.98.167.82   <none>        80:32659/TCP,443:30441/TCP   39m

root@k8s-master:


  
Access argocd Web UI using any of the worker node IP address and argocd-server port 32659 which redirect to https port 30441 
  
Get Worker node IP adress 

  
root@k8s-master: kubectl get nodes -o wide

NAME         STATUS   ROLES                  AGE    VERSION   INTERNAL-IP      EXTERNAL-IP   OS-IMAGE             KERNEL-VERSION      CONTAINER-RUNTIME

k8s-master   Ready    control-plane,master   6d2h   v1.22.0   192.168.29.231   <none>        Ubuntu 20.04.2 LTS   5.11.0-25-generic   docker://20.10.7

k8s-node1    Ready    worker                 6d2h   v1.22.0   192.168.29.207   <none>        Ubuntu 20.04.2 LTS   5.11.0-25-generic   docker://20.10.7

k8s-node2    Ready    worker                 55m    v1.22.0   192.168.29.5     <none>        Ubuntu 20.04.2 LTS   5.11.0-27-generic   docker://20.10.7

root@k8s-master:


Argo-cd Web UI  : http://192.168.29.207:32659 


User: admin

Initial Password to be trive as bellow.

User name is admin and we can retrive intial admin password as below 

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d



