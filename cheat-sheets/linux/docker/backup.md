```
docker run -d --name dbbackup -v <volume_name>:/var/www/html wordpress

docker run --rm --volumes-from dbbackup -v $PWD:/backup ubuntu tar cvf /backup/lietuviai-at-wp-data-2023-02-08.tar /var/www/html
```