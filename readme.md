# Deploying NET Core Microservices to AKS and CI/CD with Azure DevOps


## K8S Cheatsheet:

### K8S DASHBOARD
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml

### GET ADMIN TOKEN
- kubectl create serviceaccount dashboard-admin -n kubernetes-dashboard
- kubectl get secret $(kubectl get serviceaccount dashboard-admin -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --decode
- kubectl create clusterrolebinding dashboard-admin -n kubernetes-dashboard  --clusterrole=cluster-admin  --serviceaccount=default:dashboard
- kubectl -n kubernetes-dashboard create token dashboard-admin
- kubectl proxy

Navigate to https://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy

### MORE INFO
https://adamtheautomator.com/kubernetes-dashboard/

[![Build Status](https://dev.azure.com/xpander-dev/Prueba/_apis/build/status%2FShopping.MVC?branchName=master)](https://dev.azure.com/xpander-dev/Prueba/_build/latest?definitionId=5&branchName=master)
