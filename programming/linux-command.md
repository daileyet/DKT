# Linux Command

## Ubuntu remove mysql

```text
sudo apt-get purge mysql-server mysql-client mysql-common mysql-server-core-* mysql-client-core-*
sudo rm -rf /etc/mysql /var/lib/mysql
sudo apt-get autoremove
sudo apt-get autoclean
```

## Linux jar包 后台运行

```text
java -jar shareniu.jar
```

当前ssh窗口被锁定，可按CTRL + C打断程序运行，或直接关闭窗口，程序退出

```text
java -jar shareniu.jar &
```

&代表在后台运行。

当前ssh窗口不被锁定，但是当窗口关闭时，程序中止运行。

```text
nohup java -jar shareniu.jar &
```

nohup 意思是不挂断运行命令,当账户退出或终端关闭时,程序仍然运行

当用 nohup 命令执行作业时，缺省情况下该作业的所有输出被重定向到nohup.out的文件中，除非另外指定了输出文件

```text
nohup java -jar shareniu.jar >temp.txt &
nohup java -jar shareniu.jar >/dev/null &
```

command &gt;out.file是将command的输出重定向到out.file文件，即输出内容不打印到屏幕上，而是输出到out.file文件中。

```text
jobs
```

可通过jobs命令查看后台运行任务

## Add SSH key

```text
ssh-keygen -t rsa

# copy content in path "~/.ssh/id_rsa.pub" to server path "~/.ssh/authorized_keys"
cat ~/.ssh/id_rsa.pub | ssh user@hostname 'cat >> ~/.ssh/authorized_keys'
```

