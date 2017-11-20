### create user

```shell
sudo useradd new-admin-username -s /bin/bash -g sudo -m
passwd new-admin-username
```

- `-s` sets the user's login shell
- `-m` makes the user's home directory if it doesn't exist: `/home/new-admin-username`
- `-g` adds the user to the sudo group so they will have admin privileges (>11.10)



### install shadowsocks

[shadowsocks-libev](https://github.com/shadowsocks/shadowsocks-libev#install-from-repository)

For **Ubuntu 14.04 and 16.04** users, please install from PPA:

```shell
sudo apt-get install software-properties-common -y
sudo add-apt-repository ppa:max-c-lv/shadowsocks-libev -y
sudo apt-get update
sudo apt install shadowsocks-libev
```

使用配置文件

sudo vim /etc/shadowsocks-libev/config.json

```json
{
    "server":"my_server_ip",
    "server_port":8388,
    "local_port":1080,
    "password":"mypassword",
    "timeout":60,
    "method":"chacha20-ietf-poly1305",
    "fast-open": false
}

```

```shell
# Edit the configuration file
sudo vim /etc/shadowsocks-libev/config.json

# Edit the default configuration for debian
sudo vim /etc/default/shadowsocks-libev

# Start the service
sudo /etc/init.d/shadowsocks-libev start    # for sysvinit, or
sudo systemctl start shadowsocks-libev      # for systemd
```

出现以下问题时

```
This system doesn't provide enough entropy to quickly generate high-quality random numbersInstalling the rng-utils/rng-tools or haveged packages may help.On virtualized Linux environments, also consider using virtio-rng.The service will not start until enough entropy has been collected.
```

安装rng-tools
```shell
apt-get update

apt-get install rng-tools
```
编辑配置文件
```shell
vi /etc/default/rng-tools
```
添加如下内容
```
HRNGDEVICE=/dev/urandom
```
重启服务器


### Samba
