### Install Docker-CE

```shell
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



### China registry mirror

```
https://registry.docker-cn.com
```



#### docker-oracle-xe-11g

https://hub.docker.com/r/sath89/oracle-xe-11g/

#### GitLab docker

https://hub.docker.com/r/gitlab/gitlab-ce/

https://docs.gitlab.com/omnibus/docker/



```dockerfile
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

```dockerfile
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

```shell
docker volume create mariadb-vol

docker run --restart unless-stopped --name mariadb-dailey -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 --mount type=volume,src=mariadb-vol,dst=/var/lib/mysql -d mariadb

docker exec -it mariadb-dailey bash

GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '123456' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```



#### Tomcat

```shell
docker run --name tomcat-dailey -p 8088:8080 tomcat

docker run -it --rm -p 8088:8080 -v /tmp/tomcat-users.xml:/usr/local/tomcat/conf/tomcat-users.xml:ro -v /tmp/webapps:/usr/local/tomcat/webapps:rw tomcat

docker run -it --rm --name tomcat-dailey -p 8088:8080 -v /home/geek/webapps:/usr/local/tomcat/webapps:rw -d tomcat
```

