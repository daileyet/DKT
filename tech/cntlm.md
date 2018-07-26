# CNTLM

一款验证网络代理环境的软件；一般在公司内部都需要代理才能上网，且大部分代理需要用户名和密码进行认证；当一些软件和工具不支持设置用户名和密码的代理设置；另外设置的密码往往是SSO账号，这样配置在给软件工具中，非常不安全。（大部分公司代理验证都是使用NTLM）

Cntlm 是一种工具能封装NTLM验证然后对外提供普通的HTTP代理服务，第三方应用就能够通过配置普通的代理訪问网络了



## 安装

由于Cntlm是开源软件，可以到 http://cntlm.sourceforge.net/ 下载。

推荐使用默认路径安装

## 配置

安装完成后在安装目录下修改文件cntlm.ini （下载的是window版本）

```ini
#公司代理需要的用户名
Username	my_company_proxy_user_name
#公司网络的domain
Domain		my_company_proxy_domain
#hash转换后的密码
PassNTLMv2	D5826E9C665C37C80B53397D5C07BBCB
#公司代理地址和端口
Proxy		my.company-proxy.com:8080
#Cntlm listens
Listen		8088
```

其中PassNTLMv2是密码转化后的hash，可以使用如下方式测试和生成

```powershell
cntlm -c /path/to/cntlm.ini -I -M http://www.baidu.com
```

运行后会要求输入登录代理的密码，输入后，如果配置正确，会返回200响应和PassNTLMv2

## 运行

```powershell
net start cntlm

net stop cntlm
```
在本地浏览器设置代理 127.0.0.1:8088

## 排错

一般遇到  `starting service 'cntlm' failed: fork 11, Resource temporarily unavailable` 

按如下方法：

1. Open `regedit.exe` and go to `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\cntlm\Parameters`. 
2. Then change the AppArgs key to `-f -c "C:\Program Files(x86)\Cntlm\cntlm.ini"`
