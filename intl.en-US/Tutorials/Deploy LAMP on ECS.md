# Deploy LAMP on ECS {#concept_vm4_crt_2fb .task}

This topic describes how to build a LAMP stack on an ECS instance. LAMP is an acronym of the names of its four open-source components: the Linux operating system, Apache HTTP Server, MySQL relational database management system, and PHP programming language.

You must have an Alibaba Cloud account before you follow the instructions provided in the tutorial. To create an Alibaba Cloud account, click [Create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).

This example uses an ECS instance with the following configuration:

-   Uses the 64-bit CentOS 7.2 operating system
-   Uses a VPC network
-   Uses the public IP address of the ECS instance

This example chooses the following software versions. When you build a LAMP stack, choose software versions as needed.

-   Apache 2.4.37
-   MySQL 5.6.24
-   PHP 7.0.32
-   phpMyAdmin 4.0.10.20

This topic is intended for individual users who are familiar with the Linux operating system, but new to using Alibaba Cloud ECS to build websites.

This topic describes how to manually build a LAMP stack. You can also purchase a LAMP image on [Alibaba Cloud Marketplace](https://marketplace.alibabacloud.com/) and start the ECS instance to quickly build a website.

## Procedure {#section_j60_t9v_xgu .section}

Follow these steps to build a LAMP stack on an ECS instance:

1.  [Prepare the compilation environment](#section_g52_3gn_gq0)
2.  [Install Apache HTTP Server](#section_quq_rne_jnu)
3.  [Install the MySQL database management system](#section_11v_i8e_gi0)
4.  [Install PHP](#section_mi4_v1k_psh)
5.  [Install phpMyAdmin](#section_sae_6lj_aa5)

## Step 1. Prepare the compilation environment {#section_g52_3gn_gq0 .section}

Follow these steps to prepare the compilation environment:

1.  [Create an instance by using the wizard](../intl.en-US/Instances/Create an instance/Create an instance by using the wizard.md#).
2.  [Connect to a Linux instance by using the Management Terminal](../intl.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using the Management Terminal.md#).
3.  Run the `cat /etc/redhat-release` command to view the system version. 

    ![View the system version](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64105/156750496432170_en-US.png)

4.  Disable the firewall. 
    1.  Run the systemctl status firewalld command to check the firewall status. 

        ![Check the firewall status](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64105/156750496432172_en-US.png)

        -   If the firewall status is inactive, the firewall is disabled.
        -   If the firewall status is active, the firewall is enabled. In this example, the firewall is enabled. Therefore, you must disable the firewall.
    2.  The firewall must be disabled. If the firewall has already been disabled, skip this step. 
        -   If you want to temporarily disable the firewall, run the systemctl stop firewalld command.

            **Note:** This command temporarily disables the firewall. After you restart the Linux operating system, the firewall is enabled.

        -   If you want to permanently disable the firewall, run the systemctl disable firewalld command.

            **Note:** You can enable the firewall again. For more information, see the [firewall site](https://firewalld.org/).

5.  Disable SELinux. 
    1.  Run the getenforce command to check the SELinux status. 

        ![Check the SELinux status](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9763/156750496421065_en-US.png)

        -   If the SELinux status is Disabled, SELinux is disabled.
        -   If the SELinux status is Enforcing, SELinux is enabled. In this example, SELinux is enabled. Therefore, you must disable SELinux.
    2.  Disable SELinux. If SELinux has already been disabled, skip this step. 
        -   If you want to temporarily disable SELinux, run the setenforce 0 command.

            **Note:** This command temporarily disables SELinux. After you restart the Linux operating system, SELinux is enabled.

        -   If you want to permanently disable SELinux, run the vi /etc/selinux/config command to edit the configuration file of SELinux. Press Enter to run the command, move the cursor to the `SELINUX=enforcing` row, and press `I` to edit the configuration file. Change SELINUX=enforcing to `SELINUX=disabled`, press `Esc`, enter `:wq`, and then press `Enter` to save and close the configuration file.

            **Note:** You can enable SELinux again. For more information, see the [SELinux documentation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/ch-selinux#s1-SELinux-resources).

    3.  Restart the system to apply the settings.
6.  Add an inbound rule to the security group of the ECS instance to open the required port. For more information, see [Add security group rules](../intl.en-US/Security/Security groups/Add security group rules.md#).

## Step 2. Install Apache HTTP Server {#section_quq_rne_jnu .section}

Follow these steps to install Apache HTTP Server.

1.  Run the following commands to install the dependency package: 
    1.  ``` {#codeblock_o1x_fg7_cjc}
yum groupinstall "Development Tools" -y
```

    2.  ``` {#codeblock_q6g_eav_yze}
yum install libtool -y
```

    3.  ``` {#codeblock_7zm_5y8_r5t}
yum install expat-devel pcre pcre-devel openssl-devel -y
```

2.  Run the following commands to download and decompress the Apache, APR, and APR-util source code packages: 

    1.  ``` {#codeblock_jb5_bew_ub7}
wget https://mirrors.aliyun.com/apache/httpd/httpd-2.4.37.tar.gz
```

    2.  ``` {#codeblock_bom_dvo_r4f}
wget https://mirrors.aliyun.com/apache/apr/apr-1.6.5.tar.gz
```

    3.  ``` {#codeblock_7xb_c1h_c4d}
wget https://mirrors.aliyun.com/apache/apr/apr-util-1.6.1.tar.gz
```

    4.  ``` {#codeblock_q0b_izq_pqj}
tar xvf httpd-2.4.37.tar.gz -C /usr/local/src
```

    5.  ``` {#codeblock_xmg_4su_n7b}
tar xvf apr-1.6.5.tar.gz -C /usr/local/src
```

    6.  ``` {#codeblock_1a8_8c7_6r1}
tar xvf apr-util-1.6.1.tar.gz -C /usr/local/src
```

    **Note:** The source code version is continuously upgraded. You can obtain the installation package path in the [httpd source code installation package](https://mirrors.aliyun.com/apache/httpd/) or the [APR source code installation package](https://mirrors.aliyun.com/apache/apr/).

3.  Run the following commands to move the APR and APR-until folders to the Apache srclib folder: 
    1.  ``` {#codeblock_rpf_6sh_306}
cd /usr/local/src
```

    2.  ``` {#codeblock_ara_5z4_wzw}
mv apr-1.6.5 httpd-2.4.37/srclib/apr
```

    3.  ``` {#codeblock_ghn_mpb_877}
mv apr-util-1.6.1 httpd-2.4.37/srclib/apr-util
```

4.  Run the following commands to compile the source code: 
    1.  ``` {#codeblock_45a_td3_idb}
cd /usr/local/src/httpd-2.4.37
```

    2.  ``` {#codeblock_9p5_oqw_224}
./buildconf
```

    3.  ``` {#codeblock_jnw_gmb_r5b}
./configure --prefix=/usr/local/apache2 \
--enable-ssl \
--enable-so \
--with-mpm=event \
--with-included-apr \
--enable-cgi \
--enable-rewrite \
--enable-mods-shared=most \
--enable-mpms-shared=all
```

    4.  ``` {#codeblock_dcu_y16_0vy}
make && make install
```

5.  Run the following commands to set the PATH environment variable: 
    1.  ``` {#codeblock_6c1_37v_f08}
echo "export PATH=$PATH:/usr/local/apache2/bin" > /etc/profile.d/httpd.sh
```

    2.  ``` {#codeblock_toc_gz5_zac}
source /etc/profile.d/httpd.sh
```

6.  You can run the httpd -v command to view the Apache version number. 

    ![View the Apache version number](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/156750496433483_en-US.png)

7.  Add the Apache configuration file. 
    1.  Run the `vi /usr/lib/systemd/system/httpd.service` command to open the configuration file.
    2.  Press `I` and add the following content to the configuration file: 

        ``` {#codeblock_pil_cyu_qvf}
        [Unit] 
        Description=The Apache HTTP Server 
        After=network.target 
        
        [Service] 
        Type=forking 
        ExecStart=/usr/local/apache2/bin/apachectl -k start 
        ExecReload=/usr/local/apache2/bin/apachectl -k graceful 
        ExecStop=/usr/local/apache2/bin/apachectl -k graceful-stop 
        PIDFile=/usr/local/apache2/logs/httpd.pid 
        PrivateTmp=false
        
        [Install] 
        WantedBy=multi-user.target
        ```

    3.  Press `Esc`, enter `:wq`, and then press Enter to save and close the Apache configuration file.
8.  Run the following commands to start Apache HTTP Server and enable Apache HTTP Server to automatically start when the operating system is started. 
    1.  ``` {#codeblock_xoi_hx2_54m}
systemctl start httpd
```

    2.  ``` {#codeblock_gp8_5ct_alt}
systemctl enable httpd
```

9.  Check the installation status. 
    1.  Log on to the [ECS console](https://ecs.console.aliyun.com).
    2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.
    3.  On the **Instances** page, find the target instance and copy its **public IP address**.
    4.  Enter `http:// The public IP address of the ECS instance` into the address bar of your browser, and then press `Enter`. If the following page is displayed, it indicates that Apache HTTP Server has been started.

        ![The default welcome page](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/156750496412353_en-US.png)


## Step 3. Install the MySQL database management system {#section_11v_i8e_gi0 .section}

Follow these steps to install the MySQL database management system:

1.  Run the following commands to prepare the compiling environment: 
    1.  ``` {#codeblock_xhk_nr8_5dq}
yum install ncurses-devel bison gnutls-devel -y
```

    2.  ``` {#codeblock_naq_2sz_tq3}
yum install cmake -y
```

2.  Run the following commands to prepare a directory to store MySQL data. 
    1.  ``` {#codeblock_pl4_xuc_29u}
cd
```

    2.  ``` {#codeblock_hbu_qof_i6n}
mkdir /mnt/data
```

    3.  ``` {#codeblock_ywi_hvv_soe}
groupadd -r mysql
```

    4.  ``` {#codeblock_hs6_tbj_643}
useradd -r -g mysql -s /sbin/nologin mysql
```

    5.  ``` {#codeblock_rq1_h94_oza}
id mysql
```

3.  Run the following command to change the owner and group of the data directory. 

    ``` {#codeblock_9sc_0bh_avc}
    chown -R mysql:mysql /mnt/data
    ```

4.  Run the following commands to download, decompress, and compile the GA version of the source code: 
    1.  ``` {#codeblock_ib0_cql_9q8}
wget https://downloads.mysql.com/archives/get/file/mysql-5.6.24.tar.gz
```

    2.  ``` {#codeblock_xyx_x9v_kst}
tar xvf mysql-5.6.24.tar.gz -C  /usr/local/src
```

    3.  ``` {#codeblock_454_km3_2nu}
cd /usr/local/src/mysql-5.6.24
```

    4.  ``` {#codeblock_581_ngr_b6q}
cmake . -DCMAKE_INSTALL_PREFIX=/usr/local/mysql \
-DMYSQL_DATADIR=/mnt/data \
-DSYSCONFDIR=/etc \
-DWITH_INNOBASE_STORAGE_ENGINE=1 \
-DWITH_ARCHIVE_STORAGE_ENGINE=1 \
-DWITH_BLACKHOLE_STORAGE_ENGINE=1 \
-DWITH_READLINE=1 \
-DWITH_SSL=system \
-DWITH_ZLIB=system \
-DWITH_LIBWRAP=0 \
-DMYSQL_TCP_PORT=3306 \
-DDEFAULT_CHARSET=utf8 \
-DMYSQL_UNIX_ADDR=/usr/local/mysql/mysql.sock \
-DDEFAULT_COLLATION=utf8_general_ci \
-DWITH_SYSTEMD=1 \
-DINSTALL_SYSTEMD_UNITDIR=/usr/lib/systemd/system 
```

    5.  ``` {#codeblock_n8i_684_40w}
make && make install
```

5.  Run the following command to change the group of the installation directory to mysql: 

    ``` {#codeblock_13o_sv2_pci}
    chown -R mysql:mysql /usr/local/mysql/
    ```

6.  Run the following commands to initialize the database and copy the configuration file: 
    1.  ``` {#codeblock_abf_jzn_2rg}
cd /usr/local/mysql
```

    2.  ``` {#codeblock_m1i_2ph_a1y}
/usr/local/mysql/scripts/mysql_install_db --user=mysql --datadir=/mnt/data/
```

    3.  ``` {#codeblock_6nu_4j7_07k}
mv /etc/my.cnf /etc/my.cnf.bak
```

    4.  ``` {#codeblock_0df_uiu_3j3}
cp /usr/local/mysql/support-files/my-default.cnf /etc/my.cnf
```

7.  Run the following command to change the installation and data storage paths: 

    ``` {#codeblock_g58_sa3_wj4}
    echo -e "basedir = /usr/local/mysql\ndatadir = /mnt/data\n" >> /etc/my.cnf
    ```

8.  Modify the MySQL configuration file. 
    1.  Run the `vi /usr/lib/systemd/system/mysql.service` command to open the MySQL configuration file.
    2.  Press `I` and enter the following content: 

        ``` {#codeblock_qqq_zmq_q7n}
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

    3.  Press `Esc`, enter `:wq`, and then press Enter to save and close the MySQL configuration file.
9.  Run the following commands to set the PATH environment variable: 
    1.  ``` {#codeblock_hw2_tjt_pyi}
echo "export PATH=$PATH:/usr/local/mysql/bin" > /etc/profile.d/mysql.sh
```

    2.  ``` {#codeblock_ncf_wl2_fiy}
source /etc/profile.d/mysql.sh
```

10. Run the following commands to start MySQL and enable it to automatically start when the operating system is started: 
    1.  ``` {#codeblock_d2f_7wm_k2d}
systemctl start mysql
```

    2.  ``` {#codeblock_od9_xey_rf6}
systemctl enable mysql
```

11. Change the MySQL root password. Run the following command and set the password by following the instructions: 

    ``` {#codeblock_630_t3q_dax}
    mysqladmin -u root password
    ```

12. Run the following command to log on to the MySQL database: 

    ``` {#codeblock_1hl_yco_i5z}
    mysql -uroot -p
    ```

    ![Test the database](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/156750496433592_en-US.png)

13. Run the `\q` command to log out of MySQL.

## Step 4. Install PHP {#section_mi4_v1k_psh .section}

Follow these steps to install PHP:

1.  Run the following command to install the dependency package: 

    ``` {#codeblock_ayh_jjy_2m0}
    yum install libmcrypt libmcrypt-devel mhash mhash-devel libxml2 libxml2-devel bzip2 bzip2-devel -y
    ```

2.  Run the following commands to download, decompress, and compile the GA version of the source code package: 

    1.  ``` {#codeblock_o62_j2j_5ry}
cd
```

    2.  ``` {#codeblock_8sc_e1d_wiq}
wget http://cn2.php.net/get/php-7.0.32.tar.bz2/from/this/mirror
```

    3.  ``` {#codeblock_1w5_7ni_clh}
cp mirror php-7.0.32.tar.bz2
```

    4.  ``` {#codeblock_mqy_c9x_cfb}
tar xvf php-7.0.32.tar.bz2 -C /usr/local/src
```

    5.  ``` {#codeblock_dbv_jmb_2iz}
cd /usr/local/src/php-7.0.32
```

    6.  ``` {#codeblock_wb6_cxk_v58}
./configure --prefix=/usr/local/php \
--with-config-file-scan-dir=/etc/php.d \
--with-apxs2=/usr/local/apache2/bin/apxs \
--with-config-file-path=/etc \
--with-pdo-mysql=mysqlnd \
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
--with-bz2
```

    7.  ``` {#codeblock_29h_rvz_3sj}
make && make install
```

    **Note:** If the ECS instance does not have sufficient memory space, terminate PHP extensions that you do not need when you configure PHP to save memory space. For example, you can add --disable-fileinfo to the ./configure command to terminate the fileinfo extension.

3.  Run the following command to copy the PHP configuration file: 

    ``` {#codeblock_197_yoq_mar}
    cp php.ini-production /etc/php.ini
    ```

4.  Run the `vi /usr/local/apache2/conf/httpd.conf` command to open the Apache configuration file, and then press `I` to edit the configuration file. 
    1.  Find the ServerName parameter and add `ServerName localhost:80` to the parameter. 

        ![Add parameter content](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/156750496412350_en-US.png)

    2.  Find the Directory parameter. Add a number sign \(`#`\) before `Require all denied`, start a new line, and then add `Require all granted`. 

        ![Add parameter content](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/156750496512349_en-US.png)

    3.  Find `DirectoryIndex index.html` and replace it with `DirectoryIndex index.php index.html`. 

        ![Replace the content](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/156750496533711_en-US.png)

    4.  Find the following content: 

        ![Find the following content](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/156750496533713_en-US.png)

        Add the following content:

        ``` {#codeblock_iep_395_lo8}
        AddType application/x-httpd-php .php
        AddType application/x-httpd-php-source .phps
        ```

        After you add the content, the configuration is as follows.

        ![The content is added](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/156750496533714_en-US.png)

    5.  Press `Esc`, enter `:wq`, and then press Enter to save and close the Apache configuration file.
5.  Add Apache support for PHP parsing. 
    1.  Run the following command to open the index.php file: 

        ``` {#codeblock_4e0_l3z_02l}
        vi /usr/local/apache2/htdocs/index.php
        ```

    2.  Press `I` to edit the file. Add the following content to the file: 

        ``` {#codeblock_ig4_jcc_ksq}
        <? php
        phpinfo();
        ? >
        ```

    3.  Press `Esc` to exit the edit mode. Enter `:wq` to save and close the index.php file.
    4.  Run the following command to restart Apache HTTP Server. 

        ``` {#codeblock_jn3_3rd_2q8}
        systemctl restart httpd
        ```

6.  Enter `http:// The public IP address of the ECS instance` into the address bar of your browser and press `Enter`. If the following page is displayed, it indicates that PHP parsing is working properly.

    ![PHP parsing is working properly](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/156750496533715_en-US.png)


## Step 5. Install phpMyAdmin {#section_sae_6lj_aa5 .section}

Follow these steps to install phpMyAdmin:

1.  Run the following commands to prepare a directory to store phpMyAdmin data: 
    1.  ``` {#codeblock_iyv_ohz_gnb}
cd
```

    2.  ``` {#codeblock_b4t_pej_8fe}
mkdir -p /usr/local/apache2/htdocs/phpmyadmin
```

2.  Run the following command to download and decompress the phpMyAdmin package: 
    1.  ``` {#codeblock_krx_ugy_8mk}
wget https://files.phpmyadmin.net/phpMyAdmin/4.0.10.20/phpMyAdmin-4.0.10.20-all-languages.zip
```

    2.  ``` {#codeblock_kvm_xp8_yki}
unzip phpMyAdmin-4.0.10.20-all-languages.zip
```

3.  Run the following command to copy the phpMyAdmin file to the prepared storage directory: 

    ``` {#codeblock_vgo_f5l_5eg}
    mv phpMyAdmin-4.0.10.20-all-languages/*  /usr/local/apache2/htdocs/phpmyadmin
    ```

4.  Enter `http:// The public IP address of the ECS instance/phpmyadmin` into the address bar of your browser, and press `Enter` to go to the logon page of phpMyAdmin. If the following page is displayed, it indicates that phpMyAdmin has been installed.

    ![PhpMyAdmin is installed](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/156750496533718_en-US.png)

5.  Enter the MySQL username and password, and click **Go**. 

    ![Enter the MySQL username and password](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9778/156750496533716_en-US.png)


