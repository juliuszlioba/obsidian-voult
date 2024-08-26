
Simple Mysql and Arminer setup::

```yml
services:
  mysql-db:
    image: 'mysql/mysql-server:8.0'
    ports:
      - 3306:3306
    environment:
      MYSQL_ROOT_PASSWORD: '${DB_PASSWORD}'
      MYSQL_ROOT_HOST: '%'
      MYSQL_DATABASE: '${DB_DATABASE}'
      MYSQL_USER: '${DB_USERNAME}'
      MYSQL_PASSWORD: '${DB_PASSWORD}'
      MYSQL_ALLOW_EMPTY_PASSWORD: 1
    volumes:
      - 'mysql:/var/lib/mysql'
    networks:
      - mysql-db

  adminer:
    image: michalhosna/adminer
    depends_on:
      - mysql-db
    environment:
      ADMINER_SERVER: 'mysql-db'
      ADMINER_USERNAME: '${DB_USERNAME}'
      ADMINER_PASSWORD: '${DB_PASSWORD}'
      ADMINER_DB: '${DB_DATABASE}'
      ADMINER_AUTOLOGIN: 1
    restart: always
    ports:
      - 8080:8080
    networks:
      - mysql-db
  # mailpit:
  #   image: 'axllent/mailpit:latest'
  #   ports:
  #     - '${FORWARD_MAILPIT_PORT:-1025}:1025'
  #     - '${FORWARD_MAILPIT_DASHBOARD_PORT:-8025}:8025'

volumes:
  mysql:
    driver: local

networks:
  mysql-db:
    driver: bridge
```