### VirtualBox

#### Configure Network

1. set network mode to "Bridged Adapter"

2. set proxy in Ubuntu system

   ```shell
   http_proxy='http://proxy_username:password@proxy_ip:port'
   https_proxy='https://proxy_username:password@proxy_ip:port'
   ftp_proxy='ftp://proxy_username:password@proxy_ip:port'
   ```

   add above configuration to `/etc/environment`  to load them automatically at login (or system start - I might look that up if it matters).

#### Install  VBoxGuestAdditions.iso

Install  VBoxGuestAdditions.iso into Ubuntu Server version

```shell
scp  VBoxGuestAdditions.iso name@host:/path/to/VBoxGuestAdditions.iso
```



```shell
sudo mkdir /media/GuestAdditionsIS
sudo mount -o loop path/to/VBoxGuestAdditions.iso /media/GuestAdditionsISO
cd /media/GuestAdditionsISO
sudo ./VBoxLinuxAdditions.run
```


If it need you install gcc and perl:

```shell
sudo apt-get install dkms build-essential make gcc automake libssl-dev linux-headers-generic autoconf checkinstall intltool libtool module-assistant perl python python3
```

