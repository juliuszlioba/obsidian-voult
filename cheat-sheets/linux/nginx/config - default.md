```nginx
server {

    server_name domain.com www.domain.com;

    root /var/www/domain.com/html;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }

	# Node App Proxy
    location /send-email {
        proxy_pass http://localhost:5069;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
    }

    location ~ /\.ht {
        deny all;
    }

    listen 443 ssl default_server; # managed by Certbot

    ssl_certificate /etc/letsencrypt/live/domain.com/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/domain.com/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

}

server {

    if ($host = www.domain.com) {
        return 301 https://$host$request_uri;
    } # managed by Certbot

    if ($host = domain.com) {
        return 301 https://$host$request_uri;
    } # managed by Certbot

    listen 80;

    server_name domain.com www.domain.com;
    return 404; # managed by Certbot
}
```