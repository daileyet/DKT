# MySQL 主从复制搭建

\[基于Docker的Mysql主从复制搭建

## 拉取MYSQL镜像

```text
docker pull mysql:5.7
```

## 创建主从容器

### Master

```text
docker run -p 3339:3306 --name mysql-master -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7
```

### Slave

```text
docker run -p 3340:3306 --name mysql-slave -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7
```

## 配置主从容器

### 配置Master

```text
docker exec -it mysql-master /bin/bash

cd /etc/mysql/

vi my.cnf
# https://packages.debian.org/stable/editors/nano
nano my.cnf
```

my.cnf

```text
[mysqld]
## 同一局域网内注意要唯一
server-id=100  
## 开启二进制日志功能，可以随便取（关键）
log-bin=mysql-bin
```

需要重启mysql服务使配置生效

```text
service mysql restart
```

再启动容器

```text
docker container start mysql-master
```

创建数据同步用户

```text
CREATE USER 'slave'@'%' IDENTIFIED BY '123456';

GRANT REPLICATION SLAVE, REPLICATION CLIENT ON *.* TO 'slave'@'%';
```

### 配置Slave\(从\)

my.cnf

```text
[mysqld]
## 设置server_id,注意要唯一
server-id=101  
## 开启二进制日志功能，以备Slave作为其它Slave的Master时使用
log-bin=mysql-slave-bin   
## relay_log配置中继日志
relay_log=edu-mysql-relay-bin
```

配置完成后也需要重启mysql服务和docker容器，操作和配置Master\(主\)一致。

## 链接主从

### 进入Master mysql

```text
mysql -uroot -p

show master status;
```

File和Position字段的值后面将会用到，在后面的操作完成之前，需要保证Master库不能做任何操作，否则将会引起状态变化，File和Position字段的值变化

### 进入Slave mysql

```text
change master to master_host='172.17.0.2', master_user='slave', master_password='123456', master_port=3306, master_log_file='mysql-bin.000001', master_log_pos= 617, master_connect_retry=30;
```

**master\_host** ：Master的地址，指的是容器的独立ip,可以通过`docker inspect -- format='{{.NetworkSettings.IPAddress}}' 容器名称|容器id`查询容器的ip

**master\_port**：Master的端口号，指的是容器的端口号

**master\_user**：用于数据同步的用户

**master\_password**：用于同步的用户的密码

**master\_log\_file**：指定 Slave 从哪个日志文件开始复制数据，即上文中提到的 File 字段的值

**master\_log\_pos**：从哪个 Position 开始读，即上文中提到的 Position 字段的值

**master\_connect\_retry**：如果连接失败，重试的时间间隔，单位是秒，默认是60秒

### 开启Slave

在Slave 中的mysql终端执行`show slave status \G;`用于查看主从同步状态。

正常情况下，SlaveIORunning 和 SlaveSQLRunning 都是No，因为我们还没有开启主从复制过程

```text
start slave;
show slave status \G;
```

SlaveIORunning 和 SlaveSQLRunning 都是Yes，说明主从复制已经开启。此时可以测试数据同步是否成功。

## 测试主从复制

在Master创建一个数据库 test, 然后检查Slave是否存在此数据库。

