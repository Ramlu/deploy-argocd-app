argocd login localhost:8080 --insecure --username admin --password "7XdJgf-7vM2JeJzJ"
argocd account update-password \
  --account nidhi \
  --current-password 7XdJgf-7vM2JeJzJ \
  --new-password abc123412