```
helm install traefik traefik/traefik --set ports.traefik.expose=true --set dashboard.ingressRoute=true
helm install ubuntu ./mirrors --set nfs.host=producers.jackhil.de --set nfs.mountPath=/mirrors/ubuntu --set domainName=apt.jackhil.de
helm install fedora ./mirrors --set nfs.host=producers.jackhil.de --set nfs.mountPath=/mirrors/fedora --set domainName=yum.jackhil.de
kubectl apply -f ./nextcloud/nextcloud-pv.yaml
helm install nextcloud stable/nextcloud \
  --namespace nextcloud \
  --values ./nextcloud/nextcloud.values.yaml
kubectl apply -f ./nextcloud/nextcloud-ingress-route.yaml
```
