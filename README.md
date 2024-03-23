#### Commands

```bash
docker login 
minikube start

# install ArgoCD in k8s
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

#app code side 
kubectl apply -f application.yaml

#if you receive this error
W0323 16:48:07.168947   21180 main.go:291] Unable to resolve the current Docker CLI context "default": context "default": context not found: open C:\XXXXXX\meta.json: The system cannot find the path specified.
error: error parsing application.yaml: error converting YAML to JSON: yaml: line 11: did not find expected key

#
docker context use default


# access ArgoCD UI
kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 8080:443 -n argocd

# login with admin user and below token (as in documentation):
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo

ArgoCD console :  http://localhost:8080/applications/argocd/myapp-argo-application?view=tree&resource=
# you can change and delete init password

```
</br>

#tests git
update deployment to 1.0 
commit and push 
update deployment to 1.1 
commit and push
udpate 

#update in cluster update outside of git
kubectl edit deployment -n myapp myapp
change replicas to 4 



#### Links

* Config repo: [https://gitlab.com/nanuchi/argocd-app-config](https://gitlab.com/nanuchi/argocd-app-config)

* Docker repo: [https://hub.docker.com/repository/docker/nanajanashia/argocd-app](https://hub.docker.com/repository/docker/nanajanashia/argocd-app)

* Install ArgoCD: [https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd](https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd)

* Login to ArgoCD: [https://argo-cd.readthedocs.io/en/stable/getting_started/#4-login-using-the-cli](https://argo-cd.readthedocs.io/en/stable/getting_started/#4-login-using-the-cli)

* ArgoCD Configuration: [https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/)
