# Statistics

Analyze data using python and R-studio.

<a href="https://stat.readthedocs.io" target="_blank"> https://stat.readthedocs.io </a>


---

**Wonyoung Cho**.

<bourbaki10@gmail.com>

---
# R-Studio installation
## CentOS
```
$ wget https://cran.r-project.org/src/base/R-4/R-4.0.3.tar.gz
$ sudo tar -zxvf R-4.0.3.tar.gz -C /usr/bin/R

$ cd /usr/bin/R/R-3.6.0
$ sudo ./configure  --enable-R-shlib --with-readline=no --with-x=no
$ sudo make

> If below message is shown, then install **libcurl-devel**.
libcurl >= 7.22.0 library and headers are required with support for https

$ sudo yum install libcurl-devel

$ cd /usr/bin/R/R-3.6.0/bin
$ ./R
```
or
```
$ sudo yum install epel-release
$ sudo yum update
$ sudo yum install -y R
```

## Ububtu
Add repository in `/etc/apt/sources.list` matching with your OS.
```
deb https://cloud.r-project.org/bin/linux/ubuntu disco-cran35/
deb https://cloud.r-project.org/bin/linux/ubuntu cosmic-cran35/
deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/
deb https://cloud.r-project.org/bin/linux/ubuntu xenial-cran35/
deb https://cloud.r-project.org/bin/linux/ubuntu trusty-cran35/

$ sudo apt-get update
```
If some error about **publick key** is shown during the update, you need to fetch the public key in your system.
```
ex) The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9867KJ2741IO09

$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9867KJ2741IO09
```
After then, update and install R.
```
$ sudo apt-get update
$ sudo apt-get install r-base r-base-dev
```
Installation and compilation of R or some of its packages may require Ubuntu packages from the “backports” repositories. Therefore, it is suggested to activate the backports repositories with an entry like
```
deb https://<my.favorite.ubuntu.mirror>/ bionic-backports main restricted universe
```
in your /etc/apt/sources.list file.

<https://cran.r-project.org/bin/linux/ubuntu/README.html>


# R-Studio server installation
## CentOS
```
$ wget https://download2.rstudio.org/server/centos6/x86_64/rstudio-server-rhel-1.2.1335-x86_64.rpm
$ sudo yum install rstudio-server-rhel-1.2.1335-x86_64.rpm
```

## Ubuntu
```
$ sudo apt-get install -y apt-transport-https (if needed)
$ sudo apt install gdebi-core
$ cd Download
$ wget https://download2.rstudio.org/server/bionic/amd64/rstudio-server-1.2.5001-amd64.deb
$ sudo gdebi rstudio-server-1.2.5001-amd64.deb
```
<https://rstudio.com/products/rstudio/download-server/debian-ubuntu/>

## Configure
```
$ sudo emacs /etc/rstudio/rserver.conf
www-port=8787
www-address=192.168.0.1 # it is a pc ip address which the R-server has been installed.
rsession-which-r=/usr/bin/R/R-3.6.0/bin/R

$ sudo emacs /etc/rstudio/rsession.conf
www-port=8787

$ rstudio-server stop
$ rstudio-server verify-installation
$ rstudio-server start
```
- Open R-studio.

> Open web browser - Connect to http://192.168.0.1:8787 - Log in with pc ID and PASSWORD.

- If the connection is refused, allow the port.
```
$ sudo firewall-cmd --permanent --zone=public --add-port=8787/tcp
$ sudo firewall-cmd --reload
$ sudo ufw allow 8787
```

- Install packages
```
> install.packages("devtools")
> install.packages(c("devtools","curl"))
```
Reference

> <http://ds.sumeun.org/?p=832>
