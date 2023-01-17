```nginx
server {

    server_name subdomain.domain.com;
    
    listen 80;
    
    location / {
        proxy_pass http://100.80.150.128:$server_port$uri;
        proxy_set_header Host $host;
    }

}

server {

    server_name subdomain.domain.com;
    
    listen 443 ssl;

    location / {
	    proxy_pass http://subdomain.domain.com;
    }

}
```