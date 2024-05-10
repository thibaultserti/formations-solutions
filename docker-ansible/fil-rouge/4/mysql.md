# Run MySQL

```bash
docker run --name mysql -v $(PWD)/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=pw -d mysql:8
```
# Exec in it

```bash
docker exec -it mysql /bin/bash
```

```bash
mysql -u root -p fb < script/script.sql
```

# Clean
```bash
docker stop mysql
docker rm mysql
```


```bash
mysql -u root -p db
```

```sql
SELECT * FROM users
```
