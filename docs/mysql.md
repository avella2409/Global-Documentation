# MySQL

## MySQL with docker

- -d, detach
- -p, publish port
- -v, specify volume for persistence

```bash
docker run --name CONTAINER_NAME -v VOLUME_NAME:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=PASSWORD -d -p 3306:3306 mysql:TAG
```

We can interact with mysql directly from the container. First we need to interact with the container shell.

```bash
docker exec -it CONTAINER_NAME bash
```

After we just need to type `mysql -pPASSWORD` in the interactive shell.
