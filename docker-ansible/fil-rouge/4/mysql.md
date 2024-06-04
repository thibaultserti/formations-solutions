# Run MySQL

```bash
docker run --name mysql -v $(PWD)/data:/var/lib/mysql -v $(PWD):/script -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=db -d mysql:8
```

# Exec in it

```bash
docker exec -it mysql /bin/bash
```

```bash
mysql -u root -p db < script/script.sql
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
SELECT * FROM users;
```
