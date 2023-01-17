Activate website:
``` shell
sudo ln -s /etc/nginx/sites-available/your_domain /etc/nginx/sites-enabled/
```

Deactivate website:
```shell
sudo unlink /etc/nginx/sites-enabled/default
```

Test configuration:
```shell
sudo nginx -t
```

Reload Nginx:
```shell
sudo systemctl reload nginx
```

___
### useful Links
[How To Install LEMP on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu-22-04)