Owncloud Deployment using Docker Compose

git clone https://github.com/iVolve-Tech/owncloud.git

chown -R --ref owncloud-docker-server traefik

chmod -R --ref owncloud-docker-server traefik

chmod 600 traefik/data/acme.json

docker network create proxy

cd owncloud-docker-server/

There is the .env file, change your desired configuration

docker-compose up -d

cd ../traefik/

docker-compose up -d

vi /etc/hosts

127.0.0.1 owncloud.local cloud.owncloud.local traefik.owncloud.local

Add above line in hosts file.

Add this line in a machine of vi /etc/hosts, where you want to access application

<ip-deployed-application> owncloud.local cloud.owncloud.local traefik.owncloud.local
