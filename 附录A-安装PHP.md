## Ubuntu

1. 下载一个最新的Ubuntu `docker pull ubuntu`
2. `docker run -i -t ubuntu /bin/bash`
3. `apt-get update && apt-get upgrade`
4. `# apt-get install software-properties-common`

```sh
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt-get install -y php7.4

sudo apt-cache search php7*

apt-get install php7.4-mysql php7.4-curl php7.4-json php7.4-cgi php7.4-xsl php7.4-gd
```
## Centos

- EPEL(企业版Linux的额外包)
- epel
- remi
- `docker run -i -t centos /bin/bash`
```sh
    //1、添加EPEL仓库  8修改成7
    rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm

    rpm -Uvh https://mirrors.tuna.tsinghua.edu.cn/remi/enterprise/remi-release-7.rpm

    /etc/yum.repos.d目录下epel.repo  remi.repo

    //2、安装PHP
    //yum --enablerepo=remi search <keyword>

    yum -y --enablerepo=epel,remi,remi-php74 install php-cli

    PHP 7.2.24 (cli) (built: Oct 22 2019 08:28:36) ( NTS )

    yum -y --enablerepo=epel,remi,remi-php72 install php-gd php-mbstring php-mcrypt php-mysqlnd php-opcache php-pdo

    yum install php-bcmath

    yum search bcmath

    php -m

```

```sh
    yum remove epel-release
    yum clean all
```

## 其他

> release 8 怎么不能用，用7的话，默认php-7.2了

- [ppa](https://launchpad.net/~ondrej/+archive/ubuntu/php/)
- https://tecadmin.net/install-php-7-on-ubuntu/
- https://blog.remirepo.net/