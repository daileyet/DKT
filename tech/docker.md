# Docker

## Install Docker-CE

```text
sudo apt-get remove docker docker-engine docker.io

sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo apt-key fingerprint 0EBFCD88

sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"


sudo apt-get update

sudo apt-get install docker-ce
```

## China registry mirror

```text
https://registry.docker-cn.com
```

### docker-oracle-xe-11g

[https://hub.docker.com/r/sath89/oracle-xe-11g/](https://hub.docker.com/r/sath89/oracle-xe-11g/)

### GitLab docker

[https://hub.docker.com/r/gitlab/gitlab-ce/](https://hub.docker.com/r/gitlab/gitlab-ce/)

[https://docs.gitlab.com/omnibus/docker/](https://docs.gitlab.com/omnibus/docker/)

```text
 docker run --detach \
    --hostname gitlab.example.com \
    --publish 443:443 --publish 80:80 --publish 22:22 \
    --name gitlab \
    --restart always \
    --volume /srv/gitlab/config:/etc/gitlab \
    --volume /srv/gitlab/logs:/var/log/gitlab \
    --volume /srv/gitlab/data:/var/opt/gitlab \
    gitlab/gitlab-ce:latest
```

```text
docker run --detach
    --hostname SGHZ001017761.szh.apac.bosch.com \
    --publish 443:443 --publish 80:80 --publish 22:22 \
    --name gitlab \
    --restart always \
    --volume D:\DEV\Data\gitlab\config:/etc/gitlab \
    --volume D:\DEV\Data\gitlab\logs:/var/log/gitlab \
    --volume D:\DEV\Data\gitlab\data:/var/opt/gitlab \
    gitlab/gitlab-ce:latest
```

Mariadb

```text
docker volume create mariadb-vol

docker run --restart unless-stopped --name mariadb-dailey -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 --mount type=volume,src=mariadb-vol,dst=/var/lib/mysql -d mariadb

docker run --name mariadb-dailey -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 --mount type=volume,src=mariadb-vol,dst=/var/lib/mysql -d mariadb

docker exec -it mariadb-dailey bash

GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '123456' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```

### Tomcat

```text
docker run --name tomcat-dailey -p 8088:8080 tomcat

docker run -it --rm -p 8088:8080 -v /tmp/tomcat-users.xml:/usr/local/tomcat/conf/tomcat-users.xml:ro -v /tmp/webapps:/usr/local/tomcat/webapps:rw tomcat

docker run -it --rm --name tomcat-dailey -p 8088:8080 -v /home/geek/webapps:/usr/local/tomcat/webapps:rw -d tomcat

docker run -it --rm --name tomcat-dailey -p 8088:8080 -v d:/DEV/Data/docker/tomcat/webapps:/usr/local/tomcat/webapps:rw -d tomcat

docker run -it --rm --name tomcat-dailey -p 8088:8080 -v d:/DEV/Data/docker/tomcat/webapps:/usr/local/tomcat/webapps -v d:/DOC/Book:/user/local/Book -d tomcat
```

### Nginx

```text
docker run --name nginx-dailey -v d:/DEV/Data/docker/nginx/www:/usr/share/nginx/html:ro -p 90:80 -d nginx
```

### docker network

```text
docker network create cms-application
```

### mongo

```text
docker run -d --name mongodb-dailey --net cms-application -p 27017:27017 mongo

docker run -d --link mongodb:mongo --net cms-application -p 8081:8081 mongo-express
```

### PostgreSQL

```text
docker pull postgres:9.6.6-alpine

docker run -d --name postgres-dailey --net cms-application -p 5432:5432 -e POSTGRES_PASSWORD=123456
postgres:9.6.6-alpine
```

### Alpine-java

```text
docker pull anapsix/alpine-java

docker run -it --rm --name alpinej-dailey-w -p 9090:9090 anapsix/alpine-java  /bin/bash

docker run -it --name alpinej-dailey-w -d -p 9090:9090 anapsix/alpine-java  /bin/bash

docker run -it --rm --name alpinej-dailey-c -p 8889:8889/udp anapsix/alpine-java /bin/bash

docker run -it --name alpinej-dailey-c -d -p 8889:8889/udp anapsix/alpine-java /bin/bash

docker run -it --name alpinej-dailey-wc -d -p 8889:8889/udp -p 9090:9090 anapsix/alpine-java /bin/bash
```

### Nginx + PHP-FPM

```text
docker run --name npf-dailey -p 8000:80 -v D:\DEV\Data\docker\nginx\www:/var/www/html -d richarvey/nginx-php-fpm

docker run --name npf-dailey -p 8000:80 -v D:\DEV\Data\docker\nginx\www:/var/www/html --link mariadb-dailey:openthinks
-d richarvey/nginx-php-fpm
```

