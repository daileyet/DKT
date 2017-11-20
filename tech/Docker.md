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
```

