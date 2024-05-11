# Network base use case

## Build containers

```bash
docker build -t api-python:latest .
docker build -t api-golang:latest .
```


## Create network
```bash
docker network create app
```

## Create python container and dependency

```bash
docker run --name mysql --network app -v $(PWD)/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=db -d mysql:8
docker run -it --network app --name api-python -p 8080:8000 -e DB_HOST=mysql -e DB_USER=root -e DB_PASSWORD=root -e DB_NAME=db api-python
```

## Create golang container and dependency
```bash
docker run --network app --name redis -d redis:6
docker run -it --network app --name api-golang -p 8081:8000 -e REDIS_ADDR=redis:6379 -e PORT=8000 api-golang
```


## Test

```bash
curl http://localhost:8080/version
curl -X 'POST' \
  'http://localhost:8080/items/' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "name": "ball",
  "description": "Un ballon"
}'
curl -X 'DELETE' \
  'http://localhost:8080/items/ball' \
  -H 'accept: application/json'


curl -X POST http://localhost:8081/message -d '{"message":"hello world"}'
curl -X GET http://localhost:8081/message
```
