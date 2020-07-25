Owncloud deployment using Kubernetes

git clone https://github.com/iVolve-Tech/owncloud.git 

cd owncloud/kubernetes/db-deployment

kubectl create -f pv-db.yaml -f pv-backup.yaml -f pvc-db.yaml -f pvc-backup.yaml -f db-deployment.yaml -f db-service.yaml

cd ../redis-deployment/

kubectl create -f pv-redis.yaml -f pvc-redis.yaml -f redis-deployment.yaml -f redis-service.yaml

cd ../owncloud-deployment/

kubectl create -f pv-owncloud.yaml -f pvc-owncloud.yaml -f owncloud-deployment.yaml -f owncloud-service.yaml 

cd ../ingress/

Change ingress file according to your url and service, it will for default setting.

kubectl create -f traefik-rbac.yaml -f traefik-ds.yaml -f ingress.yaml -f secret.yaml



