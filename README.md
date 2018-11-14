# ah-ah-ah
This will block all access to the fission-functions path 

There are a ton of variables that you need to fill out... Run the following command to find them:
```bash
grep -r '<' * | grep '>'
```
Ignore: `ah-ah-ah/ah-ah-ah.configmap.yaml`

Deploy Nginx Ingress Controller
```bash
helm install --namespace kube-system stable/nginx-ingress -f nginx/values.yaml
```

Deploy Cert-Manager
```bash
kubectl create -f cert-manager/
```

Deploy Ah-Ah-Ah
```bash
kubectl apply -f ah-ah-ah/
```

Deploy Fission
```bash
helm install --name fission --namespace fission --set serviceType=ClusterIP,routerServiceType=ClusterIP https://github.com/fission/fission/releases/download/0.11.0/fission-all-0.11.0.tgz
kubectl apply -f fission/
```
