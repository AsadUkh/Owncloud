Installation:

There are two ways of installation of owncloud.
Docker
Kubernetes


DOCKER:


First of all download the code of application, using the given link.

wget https://raw.githubusercontent.com/owncloud/docs/master/modules/admin_manual/examples/installation/docker/docker-compose.yml

Then, create the .env file, do desire configuration.

cat << EOF > .env
OWNCLOUD_VERSION=10.4
OWNCLOUD_DOMAIN=localhost
ADMIN_USERNAME=admin
ADMIN_PASSWORD=admin
HTTP_PORT=8080
EOF

Now run docker compose command

docker-compose up -d

Proxy:

We are using nginx proxy

Download git repo

Git clone https://github.com/iVolve-Tech/owncloud.git

Go to nginx-proxy folder

Open site.conf file, do changes of DNS and IP of host machine

then,
Run docker compose

docker-compose  up -d




KUBERNETES:


Owncloud deployment using Kubernetes

Clone repo from github

git clone https://github.com/iVolve-Tech/owncloud.git 

cd owncloud/kubernetes/db-deployment

kubectl create -f pv-db.yaml -f pv-backup.yaml -f pvc-db.yaml -f pvc-backup.yaml -f db-deployment.yaml -f db-service.yaml

cd ../redis-deployment/

kubectl create -f pv-redis.yaml -f pvc-redis.yaml -f redis-deployment.yaml -f redis-service.yaml

cd ../owncloud-deployment/

kubectl create -f pv-owncloud.yaml -f pvc-owncloud.yaml -f owncloud-deployment.yaml -f owncloud-service.yaml 

Ingress:

cd ../ingress/

Change ingress file according to your url and service, it is for default setting.

kubectl create -f traefik-rbac.yaml -f traefik-ds.yaml -f ingress.yaml -f secret.yaml

