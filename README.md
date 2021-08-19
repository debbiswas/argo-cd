# argo-cd
argo-cd demo

Install Argo-cd - following two steps to unstall argo-cd in your kubernetes cluster

kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.1.0-rc3/manifests/install.yaml

Retrime Initial Password 

User name is admin and we can retrive intial admin password as below 

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

