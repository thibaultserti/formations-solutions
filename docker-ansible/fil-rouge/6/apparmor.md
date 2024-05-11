# AppArmor

## To add to profile

```
network inet6 tcp,
/app rwmlk,
/sys/kernel/mm/transparent_hugepage/hpage_pmd_size r,
/dev/pts/0 rw,
```

```bash
docker run -it --name api-golang -p 8080:8000 --security-opt apparmor=docker-container-e PORT=8000 api-golang
```
