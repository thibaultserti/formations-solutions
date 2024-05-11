# Memory and CPU

```bash
docker run -it --network app --name api-python -p 8080:8000 -e DB_HOST=mysql -e DB_USER=root -e DB_PASSWORD=root -e DB_NAME=db --memory="256m" --cpu=".5" api-python
```
