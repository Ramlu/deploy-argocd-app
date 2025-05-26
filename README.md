# deploy-argocd-app

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl port-forward svc/argocd-server -n argocd 8080:443
argocd admin initial-password -n argocd
PzXmOsZ0QGjxH9Xh
kubectl apply -f default_project.yaml 
kubectl apply -f disable_project.yaml  

kubectl apply -f dev_project.yaml 
kubectl apply -f test_project.yaml 
kubectl apply -f prod_project.yaml 

App
kubectl apply -f dev.yaml 
kubectl apply -f test.yaml 
kubectl apply -f prod.yaml 

argocd login localhost:8080 --insecure --username admin --password "PzXmOsZ0QGjxH9Xh"
argocd account list
kubectl apply -f cm.yaml 

argocd account update-password \
  --account devops \
  --current-password "PzXmOsZ0QGjxH9Xh" \
  --new-password devops123

argocd account update-password \
  --account developer \
  --current-password "PzXmOsZ0QGjxH9Xh" \
  --new-password developer123

argocd login localhost:8080 --insecure --username devops --password "devops123"


kubectl get events -n argocd --sort-by=.metadata.creationTimestamp

