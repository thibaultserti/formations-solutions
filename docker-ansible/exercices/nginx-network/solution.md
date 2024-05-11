# Network base use case

## Create containers and network
```bash
docker network create nginx
docker run -it --network nginx --name nginx1 -p 8080:80 nginx
docker run -it --network nginx --name nginx2 -p 8081:80 nginx
```

## Test it

## Get IP

```bash
docker inspect nginx1 | grep "IPAddress"
```

## Exec in container 2

```bash
docker exec -it nginx2 /bin/bash
```

## Run

```bash
curl http://<IP>
curl http://nginx1
```