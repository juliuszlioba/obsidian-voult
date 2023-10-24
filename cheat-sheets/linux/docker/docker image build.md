Docker Image build command:

```bash
docker build -t image-tag .
```

create docker container from image:

```bash
docker run -dp 127.0.0.1:3000:8080 image-tag
```

### Example files

`Dockerfile`

```
FROM nginx:alpine AS runtime
COPY ./nginx/nginx.conf /etc/nginx/nginx.conf
COPY /dist /usr/share/nginx/html
EXPOSE 8080
```

`nginx/nginx.conf`

```nginx
worker_processes  1;

events {
  worker_connections  1024;
}

http {
  server {
    listen 8080;
    server_name   _;

    root   /usr/share/nginx/html;
    index  index.html index.htm;
    include /etc/nginx/mime.types;

    gzip on;
    gzip_min_length 1000;
    gzip_proxied expired no-cache no-store private auth;
    gzip_types text/plain text/css application/json application/javascript application/x-javascript text/xml application/xml application/xml+rss text/javascript;

    error_page 404 /404.html;
    location = /404.html {
	    root /usr/share/nginx/html;
	    internal;
    }

    location / {
		try_files $uri $uri/index.html =404;
    }
  }
}
```
