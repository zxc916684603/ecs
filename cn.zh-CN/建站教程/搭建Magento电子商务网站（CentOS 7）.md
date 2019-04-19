# 搭建Magento电子商务网站（CentOS 7） {#concept_jny_5rl_2fb .concept}

Magento是一款开源电商网站框架，其丰富的模块化架构体系及拓展功能可为大中型站点提供解决方案。它使用PHP开发，支持版本范围从PHP 5.6到PHP 7.1，并使用MySQL存储数据。本教程主要介绍如何在阿里云ECS实例上搭建Magento电子商务网站。

## 适用对象 {#section_its_wrl_2fb .section}

适用于熟悉ECS、Linux系统、vim基本添加和删除命令，刚开始使用阿里云进行建站的用户。

## 项目配置 {#section_gxm_xrl_2fb .section}

本教程使用的软件版本信息如下：

-   操作系统：公共镜像CentOS 7.2 64位
-   Apache：2.4.6
-   MySQL：5.7
-   PHP：7.0
-   Composer：1.8.5
-   Magento：2.1

本教程使用的ECS实例硬件配置如下：

-   CPU：2 vCPU
-   内存：4 GiB
-   网络类型：VPC

**说明：** 搭建Magento 2服务器，所选实例规格内存不能小于2 GiB。

## 前提条件 {#section_nln_zrl_2fb .section}

ECS实例所在安全组的入方向已添加规则放行端口80和3306。详细操作，请参见[添加安全组规则](../../../../cn.zh-CN/安全/安全组/添加安全组规则.md#)。

## 基本流程 {#section_xf2_tja_cg5 .section}

1.  安装配置Apache
2.  安装配置MySQL
3.  安装配置PHP
4.  创建magento数据库
5.  安装配置Composer
6.  安装配置Magento
7.  配置Magento客户端
8.  添加cron作业

## 步骤一：安装配置Apache { .section}

1.  **安装Apache** 
    1.  运行以下命令更新包和存储库。

        ``` {#codeblock_kxq_eji_aip}
        yum update -y
        ```

    2.  运行以下命令安装Apache。

        ``` {#codeblock_85o_nbb_vsf}
        yum install httpd -y
        ```

    3.  运行以下命令查看Apache是否安装成功。

        ``` {#codeblock_nc1_knf_gy3}
        httpd -v
        ```

        返回结果如下图所示，表示安装成功。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9769/155564275244421_zh-CN.png)

2.  **配置Apache** 
    1.  运行以下命令打开Apache配置文件。

        ``` {#codeblock_612_tm5_5rn}
        vim /etc/httpd/conf/httpd.conf
        ```

    2.  在`Include conf.modules.d/*.conf`的下一行，添加`LoadModule rewrite_module modules/mod_rewrite.so`。具体步骤如下：
        1.  移动光标到`Include conf.modules.d/*.conf`下一行的行首。
        2.  按`i`键，进入编辑模式。
        3.  输入`LoadModule rewrite_module modules/mod_rewrite.so`。
        4.  按`:w`键保存修改。
    3.  将下列内容中的`AllowOverride None`更改为`AllowOverride All`。

        ```
        # AllowOverride controls what directives may be placed in .htaccess files.
        # It can be "All", "None", or any combination of the keywords:
        # Options FileInfo AuthConfig Limit
        #
        AllowOverride None
        ```

        具体步骤如下：

        1.  运行`/AllowOverride controls what`命令，找到要替换的内容。
        2.  移动光标至`AllowOverride None`。
        3.  按`R`进入替换模式。
        4.  输入`AllowOverride All`。
    4.  按`:wq`保存配置文件并退出。
3.  **启动Apache服务** 
    1.  运行以下命令启动Apache服务。

        ``` {#codeblock_s62_gt6_tn7}
        systemctl start httpd
        ```

    2.  运行以下命令添加Apache服务开机自启动。

        ``` {#codeblock_msf_n46_j1i}
        systemctl enable httpd
        ```


## 步骤二：安装配置MySQL {#section_yyy_uy3_t68 .section}

1.  **安装MySQL** 
    1.  运行以下命令添加MySQL YUM源。

        ```
        rpm -Uvh http://dev.mysql.com/get/mysql57-community-release-el7-8.noarch.rpm
        ```

    2.  运行以下命令安装MySQL。

        ``` {#codeblock_yap_emf_crj}
        yum -y install mysql-community-server
        ```

2.  **启动MySQL服务并设置开机自启动** 
    1.  运行以下命令启动MySQL服务。

        ```
        systemctl start mysqld
        ```

    2.  运行以下命令设置MySQL服务开机自启动。

        ``` {#codeblock_heu_bou_pdh}
        systemctl enable mysqld
        ```

3.  **配置MySQL** 
    1.  运行以下命令查看/var/log/mysqld.log文件，获取并记录root用户的初始密码。

        ```
        # grep 'temporary password' /var/log/mysqld.log
        2016-12-13T14:57:47.535748Z 1 [Note] A temporary password is generated for root@localhost: p0/G28g>lsHD
        ```

        **说明：** 下一步重置root用户密码时，会使用该初始密码。

    2.  运行下列命令配置MySQL的安全性。

        ``` {#codeblock_qeg_j4n_bpf}
        mysql_secure_installation
        ```

        安全性的配置包含以下五个方面：

        1.  设置root账号密码。

            ``` {#codeblock_qtp_0az_w8o}
            Enter password for user root: #输入上一步中获取的root用户密码
            The 'validate_password' plugin is installed on the server.
            The subsequent steps will run with the existing configuration of the plugin.
            Using existing password for root.
            Estimated strength of the password: 100 
            Change the password for root ? ((Press y|Y for Yes, any other key for No) : Y #是否更改root用户密码，输入Y
            New password: #输入密码，长度为8至30个字符，必须同时包含大小写英文字母、数字和特殊符号。特殊符号可以是()` ~!@#$%^&*-+=|{}[]:;‘<>,.?/
            Re-enter new password: #再次输入密码
            Estimated strength of the password: 100 
            Do you wish to continue with the password provided?(Press y|Y for Yes, any other key for No) : Y
            ```

        2.  输入`Y`删除匿名用户账号。

            ``` {#codeblock_2vn_a9k_k3b}
            By default, a MySQL installation has an anonymous user, allowing anyone to log into MySQL without having to have a user account created for them. This is intended only for testing, and to make the installation go a bit smoother. You should remove them before moving into a production environment.
            Remove anonymous users? (Press y|Y for Yes, any other key for No) : Y  #是否删除匿名用户，输入Y
            Success.
            ```

        3.  输入`Y`禁止root账号远程登录。

            ``` {#codeblock_pwo_d02_13f}
            Disallow root login remotely? (Press y|Y for Yes, any other key for No) : Y #禁止root远程登录，输入Y
            Success.
            ```

        4.  输入`Y`删除test库以及对test库的访问权限。

            ``` {#codeblock_3lr_65k_9lx}
            Remove test database and access to it? (Press y|Y for Yes, any other key for No) : Y #是否删除test库和对它的访问权限，输入Y
            - Dropping test database...
            Success.
            ```

        5.  输入`Y`重新加载授权表。

            ``` {#codeblock_g13_6su_xz9}
            Reload privilege tables now? (Press y|Y for Yes, any other key for No) : Y #是否重新加载授权表，输入Y
            Success.
            All done!
            ```

        更多详情，请参见[官方文档](http://dev.mysql.com/doc/refman/5.7/en/mysql-secure-installation.html)。


## 步骤三：安装配置PHP {#section_6r1_7kt_txz .section}

1.  **安装PHP** 
    1.  依次运行以下命令安装PHP YUM源。

        ``` {#codeblock_pv0_08w_s1i}
        # yum install -y http://dl.iuscommunity.org/pub/ius/stable/CentOS/7/x86_64/ius-release-1.0-14.ius.centos7.noarch.rpm
        # yum -y update
        # rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
        ```

    2.  运行以下命令安装PHP7及所需扩展。

        ``` {#codeblock_ibs_jc0_p7d}
        yum -y install php70w php70w-pdo php70w-mysqlnd php70w-opcache php70w-xml php70w-gd php70w-mcrypt php70w-devel php70w-intl php70w-mbstring php70w-bcmath php70w-json php70w-iconv
        ```

    3.  运行以下命令查看PHP版本。

        ```
        php -v
        ```

        返回结果如下，说明PHP安装成功。

        ``` {#codeblock_es5_vim_zur}
        PHP 7.0.33 (cli) (built: Dec  6 2018 22:30:44) ( NTS )
        Copyright (c) 1997-2017 The PHP Group
        Zend Engine v3.0.0, Copyright (c) 1998-2017 Zend Technologies
            with Zend OPcache v7.0.33, Copyright (c) 1999-2017, by Zend Technologies						
        ```

2.  **配置PHP** 
    1.  运行以下命令打开PHP配置文件。

        ``` {#codeblock_7mp_ckf_mcd}
        vim /etc/php.ini
        ```

    2.  移动光标至最后一行的行尾。具体操作步骤如下：
        1.  输入`:$`后，按回车键。光标将移动至文件最后一行。
        2.  按`$`移动光标至行尾。
    3.  按`i`进入编辑模式。
    4.  在文件最后添加以下配置：

        ```
        memory_limit = 1024M #您可根据实际情况增加或减少内存限制
        date.timezone = Asia/Shanghai #设置时区为上海。
        ```

        添加后如下图所示。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9769/155564275244781_zh-CN.png)

    5.  按`:wq`保存文件并退出。
    6.  重启Web服务进程。

        ```
        systemctl restart httpd
        ```


## 步骤四：创建Magento数据库 { .section}

1.  运行以下命令使用root用户和密码登录MySQL。

    ``` {#codeblock_x0q_p1g_ups}
    mysql -u root -p
    ```

2.  运行以下命令创建magento数据库。

    ``` {#codeblock_v9x_1bb_1qx}
    mysql> CREATE DATABASE magento; #根据实际情况将magento替换为您需要创建的数据库名称
    ```

3.  依次运行以下命令为magento数据库创建用户。

    ``` {#codeblock_rmr_x5y_bix}
    mysql> GRANT ALL ON magento.* TO YourUser@localhost IDENTIFIED BY 'YourPass'; #替换YourUser和YourPass为您需要创建的账号和密码
    mysql> FLUSH PRIVILEGES;
    ```

    例如，创建账号为magentoUser、密码为magentoUser1@3的用户，运行的命令为：

    ``` {#codeblock_x0y_nnr_kjv}
    mysql> GRANT ALL ON magento.* TO magentoUser@localhost IDENTIFIED BY 'magentoUser1@3';
    mysql> FLUSH PRIVILEGES;
    ```

4.  运行 `exit` 退出MySQL。
5.  （可选）验证新建的Magento数据库和用户是否可用。具体步骤如下：
    1.  运行以下命令使用新建账号和密码登录MySQL。

        ``` {#codeblock_cm4_x54_1k1}
        mysql -u YourUser -p   #替换YourUser为您创建的账号
        ```

    2.  运行以下命令查看新建的magento数据库。

        ``` {#codeblock_tpi_jib_477}
        mysql> show databases;
        +--------------------+
        | Database           |
        +--------------------+
        | information_schema |
        | magento            |
        +--------------------+
        2 rows in set (0.00 sec)
        ```

    3.  运行以下命令退出MySQL。

        ``` {#codeblock_0zp_gcq_5h1}
        mysql> exit
        ```


## 步骤五：安装配置Composer { .section}

Composer是一个PHP包管理和包依赖管理的工具。请按以下步骤安装配置Composer。

1.  运行以下命令安装Composer。

    ```
    curl -sS https://getcomposer.org/installer | php
    ```

2.  运行以下命令配置Composer全局使用。

    ```
    mv /root/composer.phar /usr/bin/composer
    ```

3.  运行`composer -v`命令查看Composer版本。返回结果如下，表示Composer安装成功。

    ```
      / ____/___  ____ ___  ____  ____  ________  _____
     / /   / __ \/ __ `__ \/ __ \/ __ \/ ___/ _ \/ ___/
    / /___/ /_/ / / / / / / /_/ / /_/ (__  )  __/ /
    \____/\____/_/ /_/ /_/ .___/\____/____/\___/_/
                        /_/
    Composer version 1.8.5 2019-04-09 17:46:47
    					
    ```


## 步骤六：安装配置Magento { .section}

您可以使用不同的方法安装Magento，可以选择是否安装示例数据。

-   如果安装Magento仅用于测试，您可以选择安装示例数据。
-   如果安装Magento用于生产环境，建议您安装全新的Magento，从头开始配置。

本教程介绍使用git下载Magento，并使用Composer安装Magento的操作步骤。

1.  依次运行以下命令下载Magento。

    ```
    # yum -y install git
    # cd /var/www/html/
    # git clone https://github.com/magento/magento2.git
    ```

2.  （可选）运行以下命令将Magento切换到稳定版本。

    ```
    # cd magento2 &&  git checkout tags/2.1.0 -b 2.1.0
    Switched to a new branch '2.1.0'
    ```

    **说明：** 默认情况下，git下载安装的Magento是最新的开发版本。如果您在生产环境中使用，建议切换到稳定版本，否则未来将无法升级安装。

3.  运行以下命令将安装文件移到Web服务器根目录下。

    ```
    # shopt -s dotglob nullglob && mv /var/www/html/magento2/* /var/www/html/ && cd ..
    ```

    **说明：** 如果不运行此命令，您只能通过`http://[ECS实例公网IP地址]/magento2`访问您的Magento站点。

4.  依次运行下列命令为Magento文件设置适当的权限。

    ```
    # chown -R :apache /var/www/html
    # find /var/www/html -type f -print0 | xargs -r0 chmod 640
    # find /var/www/html -type d -print0 | xargs -r0 chmod 750
    # chmod -R g+w /var/www/html/{pub,var}
    # chmod -R g+w /var/www/html/{app/etc,vendor}
    # chmod 750 /var/www/html/bin/magento
    ```

5.  运行`composer install`命令安装Magento。

## 步骤七：配置Magento客户端 {#section_s2n_ltk_g2d .section}

1.  打开浏览器。
2.  在浏览器中输入`http://[ECS实例公网IP地址]`。如果出现以下页面，说明Magento安装成功。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9769/155564275212145_zh-CN.png)

3.  单击**Agree and Setup Magento**开始配置Magento。具体步骤如下：

    1.  准备性检查。

        1.  单击**Start Readiness Check**。
        2.  检查完成后，单击**Next**。
        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9769/155564275244785_zh-CN.png)

    2.  添加数据库。

        1.  输入之前创建的数据库用户的账号和密码。本教程中创建的示例用户账号为magentoUser、密码为magentoUser1@3。
        2.  输入之前创建的数据库的名字。本教程中创建的示例数据库名字为magento。
        3.  单击**Next**。
        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9769/155564275244786_zh-CN.png)

    3.  填写Web访问设置后，单击**Next**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9769/155564275244787_zh-CN.png)

    4.  填写定制商店后，单击**Next**。
    5.  填写管理员账号信息后，单击**Next**。
    6.  单击**Install Now**进行安装。
    出现如下图所示的界面时，说明Magento配置完成。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9769/155564275212146_zh-CN.png)


## 步骤八：添加cron作业 { .section}

1.  运行`crontab -u apache -e`设置cron运行调度工作。
2.  按`i`进入编辑模式。
3.  输入下列配置信息。

    ```
    */10 * * * * php -c /etc /var/www/html/bin/magento cron:run
    */10 * * * * php -c /etc /var/www/html/update/cron.php
    */10 * * * * php -c /etc /var/www/html/bin/magento setup:cron:run
    ```

4.  按`:wq`保存并退出。

Magento上使用cron作业的更多信息，请参见[Magento官方文档](http://devdocs.magento.com/guides/v2.0/config-guide/cli/config-cli-subcommands-cron.html)。

## 后续操作 {#section_jh3_l5l_2fb .section}

访问`http://[ECS实例公网IP]`可以看到如下图所示的默认主页。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9769/155564275312147_zh-CN.png)

访问`http://[ECS实例公网IP]/admin`，输入您在安装过程中设置的用户名和密码，成功登录管理面板后可看到如下界面。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9769/155564275412148_zh-CN.png)

更多Magento配置信息，请参见[Magento官方文档](http://devdocs.magento.com/guides/v2.1/)。

