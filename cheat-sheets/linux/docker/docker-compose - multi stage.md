### Astro project - with build stage

`docker-compose.yml`

```d
services:
  astro-build:
    container_name: example
    build:
      context: .
      dockerfile: Dockerfile
    restart: always
    ports:
      - 80:8080
```

`Dockerfile`

```dockerfile
FROM node:20-slim AS base
ENV PNPM_HOME="/pnpm"
ENV PATH="$PNPM_HOME:$PATH"
RUN corepack enable
WORKDIR /app

COPY package.json pnpm-lock.yaml ./

FROM base AS prod-deps
RUN pnpm install --production

FROM base AS build-deps
RUN pnpm install --production=false

FROM build-deps AS build
COPY src ./src
COPY public ./public
COPY astro.config.mjs .
COPY components.json .
COPY tailwind.config.mjs .
COPY tsconfig.json .
RUN pnpm run build

FROM nginx:alpine AS runtime
COPY ./nginx/nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/dist /usr/share/nginx/html
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