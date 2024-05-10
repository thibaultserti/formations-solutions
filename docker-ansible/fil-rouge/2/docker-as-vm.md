# Docker as VM

## Run container

```bash
docker run -it ubuntu
```

## Install app

```bash
apt update
apt install python3 python3-pip python3.12-venv wget curl

python3 -m venv .venv
source .venv/bin/activate

wget https://raw.githubusercontent.com/thibaultserti/formations/main/docker-ansible/fil-rouge/api-python/requirements.txt
wget https://raw.githubusercontent.com/thibaultserti/formations/main/docker-ansible/fil-rouge/api-python/main.py

pip3 install -r requirements.txt

uvicorn main:app --host 0.0.0.0
```

## In another tab

```bash
docker run -it $(docker ps -a -q) /bin/bash
```

```bash
curl http://localhost:8000/
```

## Clean

```bash
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
docker rmi ubuntu
```