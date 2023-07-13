# Docker + Docker Compose + Nginx + PHP-FPM + MySQL

## Commands

### Build
```bash
docker compose build
# docker build -t php:8.2-fpm-alpine-pdo-mysql .
```

### Run
```bash
docker compose up -d
```

### Down
```bash
docker down -v
```

### Test DB _(container needs be up)_
```bash
docker compose exec db bash

mysql -u root –proot
show databases;
```

### Test DB externally _(container needs be up)_
```bash
mysql -u root -proot -h 127.0.0.1 -P 3311
show databases;
```

### Access nginx container _(container needs be up)_
```bash
docker exec -it docker-example-nginx sh
```

### Install php extension manually _(container needs be up, done on build)_
```bash
docker exec -it php-fpm docker-php-ext-install pdo pdo_mysql
docker compose restart
```

## Config

Add in `/etc/hosts` this line:
```bash
127.0.0.1 docker.localhost
```

## Application access

- Home html: [http://docker.localhost:8080](http://docker.localhost:8080) 
- Home php: [http://docker.localhost:8080/index.php](http://docker.localhost:8080/index.php) 
- Database test: [http://docker.localhost:8080/db.php](http://docker.localhost:8080/db.php) 

## Inspired in
- [Como criar containers com PHP, MySQL e NGINX utilizando o Docker Compose](https://nunesjr1993.medium.com/como-criar-containers-com-php-mysql-e-nginx-utilizando-o-docker-compose-e50a211b571b)
- [Docker repository](https://github.com/jrnunes1993/Docker)
