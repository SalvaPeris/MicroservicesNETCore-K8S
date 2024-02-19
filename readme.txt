K8S DASHBOARD
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml

GET ADMIN TOKEN

kubectl create serviceaccount dashboard-admin -n kubernetes-dashboard
kubectl get secret $(kubectl get serviceaccount dashboard-admin -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --decode
kubectl create clusterrolebinding dashboard-admin -n kubernetes-dashboard  --clusterrole=cluster-admin  --serviceaccount=default:dashboard
kubectl -n kubernetes-dashboard create token dashboard-admin

Copy token

kubectl proxy

Navegar a http o https://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy


MÁS INFO:
https://adamtheautomator.com/kubernetes-dashboard/