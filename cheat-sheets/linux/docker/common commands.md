run bash on container

```bash
docker exec -it <container_id> bash
```

clean up (complete)

```bash
docker system prune --volumes
```

follow container logs

```bash
docker logs <container_id> -f
```