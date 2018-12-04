# 搭建LNMP环境（CentOS 7） {#concept_fnh_v3x_5fb .concept}

本文档介绍如何手动在ECS实例上搭建LNMP环境（CentOS 7），其中LNMP分别代表Linux、Nginx、MySQL和PHP。

## 项目配置 {#section_mrn_4dv_vfb .section}

本篇教程在示例步骤中使用了以下版本的软件。操作时，请您以实际软件版本为准。

-   操作系统：CentOS 7.2 64位
-   Nginx版本：Nginx 1.10.2
-   MySQL版本：MySQL 5.6.24
-   PHP版本：PHP 5.6.38

## 适用对象 {#section_pmz_2x2_2fb .section}

适用于熟悉Linux操作系统，刚开始使用阿里云进行建站的个人用户。

## 基本流程 {#section_ghz_hx2_2fb .section}

使用云服务器ECS搭建LNMP平台的操作步骤如下：

1.  准备编译环境。
2.  安装Nginx。
3.  安装MySQL。
4.  安装PHP-FPM。
5.  测试访问。

**步骤一：准备编译环境。**

本文主要说明手动安装LNMP平台的操作步骤，您也可以在 [云市场](https://market.aliyun.com/software) 购买LNMP镜像直接启动ECS，以便快速建站。

1.  [使用向导创建实例](../cn.zh-CN/用户指南/实例/创建实例/使用向导创建实例.md#)。

    **说明：** 本篇教程创建的ECS实例选用了CentOS 7.2 64位的操作系统，专有网络和公网IP。

2.  [使用管理终端连接ECS实例](../cn.zh-CN/用户指南/连接实例/使用管理终端连接ECS实例.md#)。
3.  输入命令`cat /etc/redhat-release`查看系统版本。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64105/154391310132170_zh-CN.png)

4.  关闭防火墙。

    输入`systemctl status firewalld`命令查看当前防火墙的状态。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64105/154391310132172_zh-CN.png)

    如果防火墙的状态参数是active，则防火墙为开启状态。如果防火墙的状态参数是inactive，则防火墙为关闭状态。如上图所示，此处防火墙为开启状态，需要运行如下命令关闭防火墙：

    -   如果您想临时关闭防火墙，输入命令`systemctl stop firewalld`。

        **说明：** 这只是暂时关闭防火墙，下次重启Linux后，防火墙还会开启。

    -   如果您想永久关闭防火墙，输入命令`systemctl disable firewalld`。

        **说明：** 您可参考[firewalld官网](https://firewalld.org/)信息来决定何时开启防火墙。

5.  关闭SELinux。
    1.  输入getenforce命令查看当前SELinux的状态。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9763/154391310121065_zh-CN.png)

    2.  如果SELinux状态参数是Enforcing，则SELinux为开启状态。如果SELinux状态参数是Disabled， 则SELinux为关闭状态。如上图所示，此处SELinux为开启状态，需要运行如下命令关闭SELinux：
        -   如果您想临时关闭SELinux，输入命令`setenforce 0`。

            **说明：** 这只是暂时关闭SELinux，下次重启Linux后，SELinux还会开启。

        -   如果您想永久关闭SELinux，输入命令`vi /etc/selinux/config`编辑SELinux配置文件。回车后，把光标移动到`SELINUX=enforcing`这一行，按下`i`键进入编辑模式，修改为`SELINUX=disabled`， 按下`Esc`键，然后输入`:wq`并回车以保存并关闭SELinux配置文件。

            **说明：** 您可参考redhat关于[SELinux的官方文档](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/ch-selinux#s1-SELinux-resources)来决定何时开启SELinux。

    3.  重启系统使设置生效。
6.  参考[添加安全组规则](../cn.zh-CN/用户指南/安全组/添加安全组规则.md#)，放行所需端口入方向规则。

**步骤二：安装Nginx。**

1.  安装依赖包。

    ```
    yum groupinstall "Development tools" -y
    yum install zlib-devel pcre-devel openssl-devel -y
    yum install epel-release -y
    yum install perl perl-devel perl-ExtUtils-Embed libxslt libxslt-devel libxml2 libxml2-devel gd gd-devel GeoIP GeoIP-devel -y
    ```

2.  下载源码包解压编译。

    ```
    wget http://nginx.org/download/nginx-1.10.2.tar.gz
    tar xvf nginx-1.10.2.tar.gz -C /usr/local/src
    cd /usr/local/src/nginx-1.10.2
    ./configure --prefix=/etc/nginx \
    --sbin-path=/usr/sbin/nginx \
    --conf-path=/etc/nginx/nginx.conf \
    --error-log-path=/var/log/nginx/error.log \
    --http-log-path=/var/log/nginx/access.log \
    --pid-path=/var/run/nginx.pid \
    --lock-path=/var/run/nginx.lock \
    --http-client-body-temp-path=/var/tmp/nginx/client \
    --http-proxy-temp-path=/var/tmp/nginx/proxy \
    --http-fastcgi-temp-path=/var/tmp/nginx/fcgi \
    --http-uwsgi-temp-path=/var/tmp/nginx/uwsgi \
    --http-scgi-temp-path=/var/tmp/nginx/scgi \
    --user=nginx --group=nginx \
    --with-pcre --with-http_v2_module \
    --with-http_ssl_module \
    --with-http_realip_module \
    --with-http_addition_module \
    --with-http_sub_module \
    --with-http_dav_module \
    --with-http_flv_module \
    --with-http_mp4_module \
    --with-http_gunzip_module \
    --with-http_gzip_static_module \
    --with-http_random_index_module \
    --with-http_secure_link_module \
    --with-http_stub_status_module \
    --with-http_auth_request_module \
    --with-mail --with-mail_ssl_module \
    --with-file-aio \
    --with-ipv6 \
    --with-http_v2_module \
    --with-threads \
    --with-stream \
    --with-stream_ssl_module
    make && make install
    mkdir -p /var/tmp/nginx/client
    
    ```

3.  输入命令`nginx -v`可查看Nginx的版本号。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64105/154391310132179_zh-CN.png)

4.  添加运行Nginx服务进程的用户。

    ```
    useradd nginx
    chown -R nginx:nginx /etc/nginx/
    ```

5.  添加nginx.service启动配置文件。

    输入命令`vi /usr/lib/systemd/system/nginx.service`打开Nginx的启动配置文件，按下`i`键，然后在配置文件中写下如下内容：

    ```
    [Unit]
    Description=nginx - high performance web server
    Documentation=https://nginx.org/en/docs/
    After=network-online.target remote-fs.target nss-lookup.target
    Wants=network-online.target 
    
    [Service]
    Type=forking
    PIDFile=/var/run/nginx.pid
    ExecStartPre=/usr/sbin/nginx -t -c /etc/nginx/nginx.conf
    ExecStart=/usr/sbin/nginx -c /etc/nginx/nginx.conf
    ExecReload=/bin/kill -s HUP $MAINPID
    ExecStop=/bin/kill -s TERM $MAINPID 
    
    [Install] 
    WantedBy=multi-user.target
    ```

    按下`Esc`键，然后输入`:wq`并回车以保存并关闭Nginx启动配置文件。

6.  启动Nginx服务并设置开机自动启动。

    ```
    systemctl start nginx
    systemctl enable nginx
    ```

7.  登录[ECS管理控制台](https://ecs.console.aliyun.com/)，单击左侧导航栏中的**实例**，在**实例列表**中找到正在部署环境的实例，从这个实例的**IP地址**项中复制它的公网IP，用浏览器访问这个IP地址可看到默认欢迎页面。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9763/154391310121168_zh-CN.png)


**步骤三：安装MySQL。**

1.  准备编译环境。

    ```
    yum install ncurses-devel bison gnutls-devel –y
    yum install cmake -y
    ```

2.  准备MySQL数据存放目录。

    ```
    mkdir /mnt/data
    groupadd -r mysql
    useradd -r -g mysql -s /sbin/nologin mysql
    id mysql
    ```

3.  更改数据目录属主和属组。

    ```
    chown -R mysql:mysql /mnt/data
    ```

4.  下载稳定版源码包解压编译。

    ```
    wget https://downloads.mysql.com/archives/get/file/mysql-5.6.24.tar.gz
    tar xvf mysql-5.6.24.tar.gz -C  /usr/local/src
    cd /usr/local/src/mysql-5.6.24
    cmake . -DCMAKE_INSTALL_PREFIX=/usr/local/mysql \
    > -DMYSQL_DATADIR=/mnt/data \
    > -DSYSCONFDIR=/etc \
    > -DWITH_INNOBASE_STORAGE_ENGINE=1 \
    > -DWITH_ARCHIVE_STORAGE_ENGINE=1 \
    > -DWITH_BLACKHOLE_STORAGE_ENGINE=1 \
    > -DWITH_READLINE=1 \
    > -DWITH_SSL=system \
    > -DWITH_ZLIB=system \
    > -DWITH_LIBWRAP=0 \
    > -DMYSQL_TCP_PORT=3306 \
    > -DDEFAULT_CHARSET=utf8 \
    > -DDEFAULT_COLLATION=utf8_general_ci \
    > -DMYSQL_UNIX_ADDR=/usr/local/mysql/mysql.sock \
    > -DWITH_SYSTEMD=1 \
    > -DINSTALL_SYSTEMD_UNITDIR=/usr/lib/systemd/system \
    make && make install
    ```

5.  修改安装目录的属组为mysql。

    ```
    chown -R mysql:mysql /usr/local/mysql/
    ```

6.  初始化数据库并复制配置文件。

    ```
    cd /usr/local/mysql
    /usr/local/mysql/scripts/mysql_install_db --user=mysql --datadir=/mnt/data/
    mv /etc/my.cnf /etc/my.cnf.bak
    cp /usr/local/mysql/support-files/my-default.cnf /etc/my.cnf
    ```

7.  修改配置文件中的安装路径及数据目录存放路径。

    ```
    echo -e "basedir = /usr/local/mysql\ndatadir = /mnt/data\n" >> /etc/my.cnf
    ```

8.  添加mysql.service启动配置文件。

    输入命令`vi /usr/lib/systemd/system/mysql.service`打开MySQL的启动配置文件，按下`i`键，然后在配置文件中写下如下内容：

    ```
    [Unit]
    Description=MySQL Community Server
    After=network.target
    After=syslog.target
    
    [Install]
    WantedBy=multi-user.target
    Alias=mysql.service
    
    [Service]
    User=mysql
    Group=mysql
    PermissionsStartOnly=true
    ExecStart=/usr/local/mysql/bin/mysqld
    TimeoutSec=600
    Restart=always
    PrivateTmp=false
    ```

    按下`Esc`键，然后输入`:wq`并回车以保存并关闭MySQL启动配置文件。

9.  设置PATH环境变量。

    ```
    echo "export PATH=$PATH:/usr/local/mysql/bin" > /etc/profile.d/mysql.sh
    source /etc/profile.d/mysql.sh
    ```

10. 设置开机启动MySQL。

    ```
    systemctl enable mysql
    ```

11. 启动MySQL服务。

    ```
    systemctl start mysql
    mysql –h 127.0.0.1
    ```


**步骤四：安装PHP-FPM。**

Nginx作为web服务器，当它接收到请求后，不支持对外部程序的直接调用或者解析，必须通过FastCGI进行调用。如果是PHP请求，则交给PHP解释器处理，并把结果返回给客户端。PHP-FPM是支持解析PHP的一个FastCGI进程管理器。提供了更好管理PHP进程的方式，可以有效控制内存和进程、可以平滑重载PHP配置。

1.  安装依赖包。

    ```
    yum install libmcrypt libmcrypt-devel mhash mhash-devel libxml2 libxml2-devel bzip2 bzip2-devel
    ```

2.  下载稳定版源码包解压编译。

    ```
    wget http://cn2.php.net/get/php-5.6.38.tar.bz2/from/this/mirror
    cp mirror php-5.6.38.tar.bz2
    tar xvf php-5.6.38.tar.bz2 -C /usr/local/src
    cd /usr/local/src/php-5.6.38
    ./configure --prefix=/usr/local/php \
    --with-config-file-scan-dir=/etc/php.d \
    --with-config-file-path=/etc \
    --with-mysql=/usr/local/mysql \
    --with-mysqli=/usr/local/mysql/bin/mysql_config \
    --enable-mbstring \
    --with-freetype-dir \
    --with-jpeg-dir \
    --with-png-dir \
    --with-zlib \
    --with-libxml-dir=/usr \
    --with-openssl \
    --enable-xml \
    --enable-sockets \
    --enable-fpm \
    --with-mcrypt \
    --with-bz2
    make && make install
    ```

3.  添加PHP和PHP-FPM配置文件。

    ```
    cp /usr/local/src/php-5.6.38/php.ini-production /etc/php.ini
    cd /usr/local/php/etc/
    cp php-fpm.conf.default php-fpm.conf
    sed -i 's@;pid = run/php-fpm.pid@pid = /usr/local/php/var/run/php-fpm.pid@' php-fpm.conf
    ```

4.  添加php-fpm.service启动配置文件。

    输入命令`vi /usr/lib/systemd/system/php-fpm.service`打开PHP-FPM的启动配置文件，按下`i`键，然后在配置文件中写下如下内容：

    ```
    [Unit]
    Description=The PHP FastCGI Process Manager
    After=network.target
    
    [Service]
    Type=simple
    PIDFile=/usr/local/php/var/run/php-fpm.pid ExecStart=/usr/local/php/sbin/php-fpm --nodaemonize --fpm-config /usr/local/php/etc/php-fpm.conf
    ExecReload=/bin/kill -USR2 $MAINPID
    PrivateTmp=true
    
    [Install]
    WantedBy=multi-user.target
    
    ```

    按下`Esc`键，然后输入`:wq`并回车以保存并关闭PHP-FPM启动配置文件。

5.  启动PHP-FPM服务并设置开机自动启动。

    ```
    systemctl start php-fpm
    systemctl enable php-fpm
    ```

6.  启动服务。

    ```
    service php-fpm start
    ```

7.  添加Nginx对FastCGI的支持。
    1.  备份默认的Nginx配置文件。

        ```
        cp /etc/nginx/nginx.conf /etc/nginx/nginx.confbak
        cp nginx.conf.default nginx.conf.default.bak
        cp /etc/nginx/nginx.conf.default /etc/nginx/nginx.conf
        ```

    2.  输入命令`vi /etc/nginx/nginx.conf`打开Nginx的配置文件，按下`i`键，在所支持的主页面格式中添加PHP格式的主页，类似如下：

        ```
        location / {
          root   /etc/nginx/html;
          index  index.php index.html index.htm;
        }
        ```

    3.  取消以下内容前面的注释：

        ```
        location ~ \.php$ {
         root html;
         fastcgi_pass 127.0.0.1:9000;
         fastcgi_index index.php;
         fastcgi_param SCRIPT_FILENAME /scripts$fastcgi_script_name;
         include fastcgi_params;
        }
        ```

    4.  将`root html;`改成`root /etc/nginx/html;`。
    5.  将`fastcgi_param SCRIPT_FILENAME /scripts$fastcgi_script_name;`改成`fastcgi_param SCRIPT_FILENAME /etc/nginx/html/$fastcgi_script_name;`。
    6.  按下`Esc`键，然后输入`:wq`并回车以保存并关闭Nginx配置文件。
8.  输入命令`systemctl restart nginx`重新载入Nginx的配置文件。
9.  输入命令`vi /etc/nginx/html/index.php`打开index.php文件，按下`i`键，然后在文件中写入如下内容：

    ```
    <?php
    $conn=mysql_connect('127.0.0.1','root','');
    if ($conn){
    echo "LNMP platform connect to mysql is successful!";
    }else{
    echo "LNMP platform connect to mysql is failed!";
    }
    phpinfo();
    ?>
    ```

10. 按下`Esc`键，然后输入`:wq`并回车以保存并关闭index.php文件。

**步骤五：测试访问**

登录 [ECS管理控制台](https://ecs.console.aliyun.com/)，单击左侧导航栏中的**实例**，在**实例列表**中复制正在部署环境的实例的公网IP地址。用浏览器访问这个公网IP地址，如您看见如下图所示页面，则表示LNMP平台构建完成。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64105/154391310132205_zh-CN.png)

