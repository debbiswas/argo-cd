# argo-cd
argo-cd demo

Install Argo-cd - following two steps to unstall argo-cd in your kubernetes cluster

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.1.0-rc3/manifests/install.yaml
