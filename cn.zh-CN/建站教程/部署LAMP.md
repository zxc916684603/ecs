# 部署LAMP {#concept_vm4_crt_2fb .concept}

LAMP指Linux+Apache+MySQL/MariaDB+Perl/PHP/Python，是一组常用来搭建动态网站或者服务器的开源软件。它们本身都是各自独立的程序，但是因为常被放在一起使用，拥有了越来越高的兼容度，共同组成了一个强大的Web应用程序平台。

## 部署方式 {#section_ib3_drt_2fb .section}

您可以使用三种方式在云服务器ECS上部署LAMP：

-   [镜像部署](http://help.aliyun.com/document_detail/25427.html)：方便快捷，适合不太了解Linux命令的用户。
-   [一键安装包部署](http://help.aliyun.com/document_detail/44595.html)：适合对Linux命令有基本了解的用户。
-   手动部署：可以满足用户个性化部署需求，适合对Linux命令有基本了解的用户。

本文介绍如何在云服务器ECS上手动部署LAMP。

## 软件版本说明 {#section_xty_frt_2fb .section}

本文操作的镜像和软件版本说明如下 ：

-   操作系统：CentOS 7.2 64位
-   Apache：2.4.23
-   MySQL：5.7.17
-   PHP：7.0.12

## 前提条件 {#section_r55_grt_2fb .section}

在部署之前，需要确认：

-   实例所在安全组已经 [放行了服务所需的端口](http://help.aliyun.com/document_detail/25471.html)：

    |服务|SSH|HTTP|MySQL|
    |端口|TCP 22|TCP 80|TCP 3306|

-   [已经远程连接到实例](http://help.aliyun.com/document_detail/25434.html)。

## 准备工作 {#section_v22_krt_2fb .section}

**设置防火墙**

CentOS 7.2系统默认开启防火墙firewalld。您可以关闭firewalld放行80、22等端口。

**说明：** 您也可以参考 [firewalld 官方文档](http://www.firewalld.org/documentation/howto/enable-and-disable-firewalld.html) 在防火墙里放行这些端口。

1.  运行命令关闭防火墙。

    ```
    systemctl stop firewalld.service
    ```

2.  运行命令关闭防火墙开机自启动。

    ```
    systemctl disable firewalld.service
    ```


**安装软件**

运行命令下载软件、编辑和解压文件。

```
yum install -y wget vim unzip
```

## 操作步骤 {#section_rfz_prt_2fb .section}

按以下步骤部署LAMP。

**步骤1：编译安装Apache**

1.  运行命令安装相关依赖包。

    ```
    yum install -y gcc gcc-c++ autoconf libtool
    ```

2.  依次运行以下命令安装apr。

    ```
    cd /usr/local/src/
    wget http://oss.aliyuncs.com/aliyunecs/onekey/apache/apr-1.5.0.tar.gz
    tar zxvf apr-1.5.0.tar.gz
    cd apr-1.5.0
    ./configure --prefix=/usr/local/apr
    make && make install
    ```

3.  依次运行以下命令安装apr-util。

    ```
    cd /usr/local/src/
    wget http://oss.aliyuncs.com/aliyunecs/onekey/apache/apr-util-1.5.3.tar.gz
    tar zxvf apr-util-1.5.3.tar.gz
    cd apr-util-1.5.3
    ./configure --prefix=/usr/local/apr-util --with-apr=/usr/local/apr
    make && make install
    ```

4.  依次运行以下命令安装pcre。

    ```
    cd /usr/local/src/
    wget http://zy-res.oss-cn-hangzhou.aliyuncs.com/pcre/pcre-8.38.tar.gz 
    tar zxvf pcre-8.38.tar.gz
    cd pcre-8.38
    ./configure --prefix=/usr/local/pcre
    make && make install
    ```

5.  依次运行以下命令编译安装Apache。

    ```
    cd /usr/local/src/
    wget http://zy-res.oss-cn-hangzhou.aliyuncs.com/apache/httpd-2.4.23.tar.gz 
    tar zxvf httpd-2.4.23.tar.gz
    cd httpd-2.4.23
    ./configure \
    --prefix=/usr/local/apache --sysconfdir=/etc/httpd \
    --enable-so --enable-cgi --enable-rewrite \
    --with-zlib --with-pcre=/usr/local/pcre \
    --with-apr=/usr/local/apr \
    --with-apr-util=/usr/local/apr-util \
    --enable-mods-shared=most --enable-mpms-shared=all \
    --with-mpm=event
    make && make install
    ```

6.  修改httpd.conf配置文件参数：
    1.  运行 `cd /etc/httpd/` 切换到/etc/httpd/目录。
    2.  运行 `vim httpd.conf` 打开httpd.conf文件，按 `i` 键进入编辑模式。
    3.  找到 `Directory` 参数，注释掉 `Require all denied`，并添加 `Require all granted`。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/154105670312349_zh-CN.png)

    4.  找到 `ServerName` 参数，添加 `ServerName localhost:80`。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/154105670412350_zh-CN.png)

    5.  设置 `PidFile` 路径：在文件最后添加 `PidFile "/var/run/httpd.pid"`。
    6.  按 `Esc` 键退出编辑模式，输入 `:wq` 保存并关闭 httpd.conf 文件。
7.  依次执行以下命令启动Apache服务并验证。

    ```
    cd /usr/local/apache/bin/
    ./apachectl start
    netstat -tnlp                             #查看服务是否开启
    ```

    如果返回以下结果，说明Apache服务已经成功启动。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/154105670412351_zh-CN.png)

    在本地机器的浏览器中输入ECS实例公网IP地址，如果出现如图所示信息，说明Apache服务安装成功。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/154105670412353_zh-CN.png)

8.  设置开机自启动。
    1.  运行 `vim /etc/rc.d/rc.local` 打开rc.local文件，按 `i` 进入编辑模式。
    2.  添加 `/usr/local/apache/bin/apachectl start`。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/154105670412354_zh-CN.png)

    3.  按 `Esc` 键退出编辑模式，输入 `:wq` 保存并关闭rc.local文件。
9.  设置环境变量。
    1.  运行 `vi /root/.bash_profile` 打开文件，按 `i` 进入编辑模式。
    2.  将 `PATH=$PATH:$HOME/bin` 修改为 `PATH=$PATH:$HOME/bin:/usr/local/apache/bin`。
    3.  按 `Esc` 键退出编辑模式，输入 `:wq` 保存并关闭文件。
    4.  运行 `source /root/.bash_profile` 重新执行文件。

**步骤2：编译安装MySQL**

1.  依次执行以下命令检查系统中是否存在使用rpm安装的MySQL或者MariaDB。

    ```
    rpm -qa | grep mysql
    rpm -qa | grep mariadb
    ```

    如果已经安装，则运行下面第一个命令卸载。若第一个命令卸载不成功，则运行下面第二个命令强制卸载。

    ```
    rpm -e 软件名    #注意：这里的软件名必须包含软件的版本信息，如rpm -e mariadb-libs-5.5.52-1.el7.x86_64。一般使用此命令即可卸载成功。
    rpm -e --nodeps 软件名   #注意：这里的软件名必须包含软件的版本信息，如rpm -e --nodeps mariadb-libs-5.5.52-1.el7.x86_64。
    ```

    卸载后，再用 `rpm -qa|grep mariadb` 和 `rpm -qa|grep mysql` 查看结果。如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/154105670421379_zh-CN.png)

2.  依次运行以下命令安装 MySQL。

    ```
    yum install -y libaio-*                         #安装依赖
    mkdir -p /usr/local/mysql
    cd /usr/local/src
    wget http://zy-res.oss-cn-hangzhou.aliyuncs.com/mysql/mysql-5.7.17-linux-glibc2.5-x86_64.tar.gz 
    tar -xzvf mysql-5.7.17-linux-glibc2.5-x86_64.tar.gz
    mv mysql-5.7.17-linux-glibc2.5-x86_64/* /usr/local/mysql/
    ```

3.  依次运行以下命令建立mysql组和用户，并将mysql用户添加到mysql组。

    ```
    groupadd mysql
    useradd -g mysql -s /sbin/nologin mysql
    ```

4.  运行命令初始化MySQL数据库。

    ```
    /usr/local/mysql/bin/mysqld --initialize-insecure --datadir=/usr/local/mysql/data/ --user=mysql
    ```

5.  更改MySQL安装目录的属性：`chown -R mysql:mysql /usr/local/mysql`。
6.  依次运行以下命令设置开机自启动。

    ```
    cd /usr/local/mysql/support-files/
    cp mysql.server  /etc/init.d/mysqld
    chmod +x /etc/init.d/mysqld             # 添加执行权限
    vim /etc/rc.d/rc.local
    ```

    在 rc.local 文件中添加 `/etc/init.d/mysqld start`。

7.  设置环境变量。
    1.  运行 `vi /root/.bash_profile` 打开文件，按 `i` 进入编辑模式。
    2.  将 `PATH=$PATH:$HOME/bin:/usr/local/apache/bin` 修改为 `PATH=$PATH:$HOME/bin:/usr/local/apache/bin:/usr/local/mysql/bin:/usr/local/mysql/bin`。

        **说明：** 此处是在编译安装 Apache的环境变量的基础上再进行修改。

    3.  按 `Esc` 键退出编辑模式，输入 `:wq` 保存并关闭文件。
    4.  运行 `source /root/.bash_profile` 重新执行文件。
8.  启动 MySQL 数据库。

    ```
    /etc/init.d/mysqld start
    ```

    出现如下截图所示信息，表示MySQL启动成功。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/154105670412355_zh-CN.png)

9.  修改MySQL的root用户密码：初始化后MySQL为空密码可直接登录，为了保证安全性需要修改MySQL的root用户密码。运行以下命令，并按界面提示设置密码。

    ```
    mysqladmin -u root password
    ```

10. 测试登录MySQL数据库。

    ```
    mysql -uroot -p #-p和密码之间无空格
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/154105670412356_zh-CN.png)

11. 运行 `\q` 退出MySQL。

**步骤3. 编译安装 PHP**

1.  依次运行以下命令安装依赖。

    ```
    yum install epel-release php-mcrypt libmcrypt libmcrypt-devel  libxml2-devel  openssl-devel  libcurl-devel libjpeg.x86_64 libpng.x86_64 freetype.x86_64 libjpeg-devel.x86_64 libpng-devel.x86_64 freetype-devel.x86_64  libjpeg-turbo-devel   libmcrypt-devel   mysql-devel  -y
     wget http://zy-res.oss-cn-hangzhou.aliyuncs.com/php/php-7.0.12.tar.gz
     tar zxvf php-7.0.12.tar.gz
     cd php-7.0.12
     ./configure \
     --prefix=/usr/local/php \
     --enable-mysqlnd \
     --with-mysqli=mysqlnd --with-openssl \
     --with-pdo-mysql=mysqlnd \
     --enable-mbstring \
     --with-freetype-dir \
     --with-jpeg-dir \
     --with-png-dir \
     --with-zlib --with-libxml-dir=/usr \
     --enable-xml  --enable-sockets \
     --with-apxs2=/usr/local/apache/bin/apxs \
     --with-mcrypt  --with-config-file-path=/etc \
     --with-config-file-scan-dir=/etc/php.d \
     --enable-maintainer-zts \
     --disable-fileinfo
     make && make install
    ```

2.  运行命令复制配置文件。

    ```
    cp php.ini-production /etc/php.ini
    ```

3.  编辑Apache配置文件 httpd.conf，以Apache支持PHP。
    1.  运行 `vim /etc/httpd/httpd.conf` 打开文件，按 `i` 进入编辑模式。
    2.  在配置文件最后添加如下二行代码。

        ```
        AddType application/x-httpd-php  .php 
        AddType application/x-httpd-php-source  .phps
        ```

    3.  定位到 `DirectoryIndex index.html`，修改为 `DirectoryIndex index.php index.html`。

        **说明：** 如果文件中没有 `DirectoryIndex index.html`，则添加上述代码。

    4.  按 `Esc` 键退出编辑模式，输入 `:wq` 保存并关闭文件。
4.  重启Apache服务：

    ```
    /usr/local/apache/bin/apachectl restart
    ```

5.  测试是否能够正常解析PHP。
    1.  依次运行以下命令，找开index.php文件。

        ```
        cd  /usr/local/apache/htdocs/
        vim index.php
        ```

    2.  按 `i` 键进入编辑模式，并添加以下内容。

        ```
        <?php
        phpinfo();
        ?>
        ```

    3.  按 `Esc` 键退出编辑模式，并输入 `:wq` 保存并关闭文件。
    4.  重启Apache服务：

        ```
        /usr/local/apache/bin/apachectl restart
        ```

    5.  在本地机器的浏览器里输入 `http://实例公网 IP/index.php`。

        如果出现以下页面表示PHP解析成功。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/154105670412357_zh-CN.png)


**步骤4. 安装phpMyAdmin**

依次运行以下命令安装phpMyAdmin。

```
mkdir -p /usr/local/apache/htdocs/phpmyadmin
cd /usr/local/src/
wget http://oss.aliyuncs.com/aliyunecs/onekey/phpMyAdmin-4.1.8-all-languages.zip
unzip phpMyAdmin-4.1.8-all-languages.zip
mv phpMyAdmin-4.1.8-all-languages/*  /usr/local/apache/htdocs/phpmyadmin
```

在本地机器浏览器输入 `http://实例公网 IP/phpmyadmin` 访问phpMyAdmin登录页面。如果出现以下页面，说明phpMyAdmin安装成功。输入MySQL的用户名和密码即可登录。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/154105670412358_zh-CN.png)

## 相关链接 {#section_gm2_r5t_2fb .section}

您可通过 [云中沙箱平台](https://edu.cloudcare.cn/courses/e1f762aba275487e9bc2667dc3fe36aa/detail) 上体验本文档描述的操作。

更多开源软件尽在 [云市场](https://market.aliyun.com/software)。

