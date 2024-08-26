
Simple Mysql and Arminer setup::

```yml
services:
  mysql-db:
    image: 'mariadb:10.8.3'
    command: --default-authentication-plugin=mysql_native_password
    restart: always
    ports:
      - 3306:3306
    environment:
      MYSQL_DATABASE: '${DB_DATABASE}'
      MYSQL_USER: '${DB_USERNAME}'
      MYSQL_ROOT_PASSWORD: '${DB_PASSWORD}'
    volumes:
      - 'mysql:/var/lib/mysql'

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
  # mailpit:
  #   image: 'axllent/mailpit:latest'
  #   ports:
  #     - '${FORWARD_MAILPIT_PORT:-1025}:1025'
  #     - '${FORWARD_MAILPIT_DASHBOARD_PORT:-8025}:8025'

volumes:
  mysql:
    driver: local
```