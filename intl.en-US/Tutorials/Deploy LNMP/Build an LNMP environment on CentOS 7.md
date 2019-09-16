# Build an LNMP environment on CentOS 7 {#concept_fnh_v3x_5fb .task}

NGINX is a small and efficient Web server software for Linux. NGINX allows you to easily build an LNMP Web service environment. The LNMP environment is based on four major components required in this architecture: Linux, NGINX, MySQL, and PHP. This topic describes how to manually build the LNMP environment on an ECS instance.

-   You must have an Alibaba Cloud account before you follow the instructions provided in the tutorial. To create an Alibaba Cloud account, click [Create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).
-   You have added an inbound rule to the security group of the ECS instance to support Ports 80 and 3306. For more information, see [Add security group rules](../intl.en-US/Security/Security groups/Add security group rules.md#).

The procedure described in this topic is applicable to individual users that are familiar with Linux, but new to website construction by using Alibaba Cloud ECS instances.

The following software versions are used:

-   Operating system: public image 64-bit CentOS 7.2
-   NGINX: version 1.12.2
-   MySQL: version 5.7.25
-   PHP: version 7.0.33

The ECS instances described in this topic use the following configurations:

-   CPU: 2 vCPUs
-   Memory: 4 GiB
-   Network type: Virtual Private Cloud \(VPC\)
-   IP address: public IP address

You can also purchase an LNMP image in [Alibaba Cloud Marketplace](https://marketplace.alibabacloud.com/) and launch an ECS instance from the image to efficiently build a website.

## Procedure {#section_bi1_x2j_v96 .section}

To build an LNMP environment manually by using an ECS instance, follow these steps:

1.  [Step 1: Prepare the compiling environment](#section_swe_tkc_2ir)
2.  [Step 2: Install NGINX](#section_dri_f0r_ivi)
3.  [Step 3: Install MySQL](#section_sok_8r6_jr6)
4.  [Step 4: Install PHP](#section_5tw_l02_k4s)
5.  [Step 5: Configure NGINX](#section_e7d_ddt_6tc)
6.  [Step 6: Configure MySQL](#section_mp6_h2y_zkp)
7.  [Step 7: Configure PHP](#section_ual_v4d_k6e)
8.  [Step 8: Test the connection to the LNMP environment](#section_b0a_az5_erl)

## Step 1: Prepare the compiling environment {#section_swe_tkc_2ir .section}

To prepare the compiling environment, follow these steps:

1.  Connect to a Linux ECS instance. For more information, see [Connect to a Linux instance by using an SSH key pair](../intl.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using an SSH key pair.md#) or [Connect to a Linux instance by using a password](../intl.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using a password.md#).
2.  Disable the firewall. 
    1.  Run the command `systemctl status firewalld` to check the state of the firewall. 

        ![Check the state of the firewall](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64105/156862597732172_en-US.png)

        -   If the firewall stays in the inactive state, the firewall is disabled.
        -   If the firewall stays in the active state, the firewall is enabled. In this example, the firewall is in the active state, so you must disable the firewall.
    2.  Disable the firewall. Skip this step if the firewall is in the inactive state. 
        -   To temporarily disable the firewall, run the command `systemctl stop firewalld`.

            **Note:** Therefore, the firewall is temporarily disabled, and will remain in the active state when you restart Linux next time.

        -   To permanently disable the firewall, run the command `systemctl disable firewalld`.

            **Note:** You can enable the firewall again. For more information, see [Firewalld documentation](https://firewalld.org/).

3.  Disable Security-Enhanced Linux \(SELinux\). 
    1.  Run the `getenforce` command to check the state of SELinux. 

        ![Check the state of SELinux](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9763/156862597721065_en-US.png)

        -   If SELinux stays in the Disabled state, SELinux is disabled.
        -   If SELinux stays in the Enforcing state, SELinux is enabled. In this example, SELinux is in the Enforcing state, so you must disable SELinux.
    2.  Disable SELinux. Skip this step if SELinux is in the Disabled state. 
        -   To temporarily disable SELinux, run the command `setenforce 0`.

            **Note:** Therefore, SELinux is temporarily disabled, and will remain in the Enforcing state when you restart Linux next time.

        -   To permanently disable SELinux, follow these steps: Run the command `vi /etc/selinux/config`, and press the Enter key. Move the pointer to the line of `SELINUX=enforcing`, and press the `i` key to enter the edit mode. Edit the SELinux state in this way: `SELINUX=disabled`. Afterward, press the `Esc` key, type `:wq`, and then press the `Enter` key to save and close the SELinux configuration file.

            **Note:** You can enable SELinux again. For more information, see [SELinux documentation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/ch-selinux#s1-SELinux-resources).

    3.  Restart the system to make the changes take effect.

## Step 2: Install NGINX {#section_dri_f0r_ivi .section}

To install NGINX, follow these steps:

1.  Run the following command to install NGINX. 

    ``` {#codeblock_36h_rd3_sgn}
    yum -y install nginx
    ```

2.  Run the following command to check the NGINX version. 

    ``` {#codeblock_9zx_sze_j1d}
    nginx -v                            
    ```

    The following response indicates that NGINX has been installed.

    ``` {#codeblock_zt3_wnu_m8d}
    nginx version: nginx/1.12.2                            
    ```


## Step 3: Install MySQL {#section_sok_8r6_jr6 .section}

To install MySQL, follow these steps:

1.  Run the following command to update the YUM repository. 

    ``` {#codeblock_koo_tk1_8u4}
    rpm -Uvh  http://dev.mysql.com/get/mysql57-community-release-el7-9.noarch.rpm
    ```

2.  Run the following command to install MySQL. 

    ``` {#codeblock_ard_wdk_vl8}
    yum -y install mysql-community-server
    ```

3.  Run the following command to check the MySQL version. 

    ``` {#codeblock_dvm_6z1_wqe}
    mysql -V
    ```

    The following response indicates that MySQL has been installed.

    ``` {#codeblock_xll_r6f_g1u}
    mysql  Ver 14.14 Distrib 5.7.25, for Linux (x86_64) using  EditLine wrapper
    ```


## Step 4: Install PHP {#section_5tw_l02_k4s .section}

To install PHP, follow these steps:

1.  Run the following commands in sequence to update the YUM repository. 

    ``` {#codeblock_4w7_lig_c8h}
    # yum install -y http://dl.iuscommunity.org/pub/ius/stable/CentOS/7/x86_64/ius-release-1.0-15.ius.centos7.noarch.rpm
    # rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
    ```

    **Note:** The package `ius-release-1.0-15.ius.centos7.noarch.rpm` is used in this topic. In your actual running environment, use the latest ius-release package.

2.  Run the following command to install PHP. 

    ``` {#codeblock_oxs_0w8_qym}
    yum -y install php70w-devel php70w.x86_64 php70w-cli.x86_64 php70w-common.x86_64 php70w-gd.x86_64 php70w-ldap.x86_64 php70w-mbstring.x86_64 php70w-mcrypt.x86_64  php70w-pdo.x86_64   php70w-mysqlnd  php70w-fpm php70w-opcache php70w-pecl-redis php70w-pecl-mongo
    ```

3.  Run the following command to check the PHP version. 

    ``` {#codeblock_ae6_t4j_l6k}
    php -v
    ```

    The following response indicates that PHP has been installed.

    ``` {#codeblock_lug_03g_tbo}
    PHP 7.0.33 (cli) (built: Dec  6 2018 22:30:44) ( NTS )
    Copyright (c) 1997-2017 The PHP Group
    Zend Engine v3.0.0, Copyright (c) 1998-2017 Zend Technologies
        with Zend OPcache v7.0.33, Copyright (c) 1999-2017, by Zend Technologies                
    ```


## Step 5: Configure NGINX {#section_e7d_ddt_6tc .section}

To configure NGINX, follow these steps:

1.  Run the following command to back up the NGINX configuration file. 

    ``` {#codeblock_6td_viy_mfp}
    cp /etc/nginx/nginx.conf /etc/nginx/nginx.conf.bak
    ```

2.  Run the following command to open the NGINX configuration file. 

    ``` {#codeblock_9t2_ezx_mu0}
    vim /etc/nginx/nginx.conf
    ```

3.  Press the `i` key to enter the edit mode.
4.  Add the following configurations between the braces of the server field so that NGINX can support PHP requests. 

    ``` {#codeblock_vml_nfi_gfx}
            location / {
                index index.php index.html index.htm;
            }
            #Enables NGINX to process your PHP requests by using Fast Common Gateway Interface (FastCGI).
            location ~ .php$ {
                root /usr/share/php;
                fastcgi_pass 127.0.0.1:9000; #NGINX forwards PHP requests to PHP FastCGI Process Manager (PHP-FPM) through Port 9000 of the ECS instance.
                fastcgi_index index.php;
                fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
                include fastcgi_params;  #NGINX uses the FastCGI interface to process PHP requests.
            }                
    ```

    **Note:** If you do not add the configurations, NGINX cannot process your PHP requests. As a result, you will not open the requested PHP-enabled page.

5.  Run the following command to start the NGINX service. 

    ``` {#codeblock_4uv_qs6_hhz}
    systemctl start nginx
    ```

6.  Run the following command to enable the NGINX service to run at startup. 

    ``` {#codeblock_3fq_onj_ajg}
    systemctl enable nginx
    ```


## Step 6: Configure MySQL {#section_mp6_h2y_zkp .section}

To configure MySQL, follow these steps:

1.  Run the following command to start the MySQL service. 

    ``` {#codeblock_82d_of5_syh}
    systemctl start mysqld
    ```

2.  Run the following command to enable the MySQL service to run at startup. 

    ``` {#codeblock_my7_hw4_ei9}
    systemctl enable mysqld
    ```

3.  Run the following command to check the file /var/log/mysqld.log and obtain the initial password of the root user. 

    ``` {#codeblock_tuf_7m1_pde}
    # grep 'temporary password' /var/log/mysqld.log
    2016-12-13T14:57:47.535748Z 1 [Note] A temporary password is generated for root@localhost: p0/G28g>lsHD
    ```

    **Note:** You must use the initial password to reset the password as the root user.

4.  Run the following command to configure your MySQL databases and secure data. 

    ``` {#codeblock_99r_5w3_mav}
    mysql_secure_installation
    ```

    Continue with these steps for the security configuration:

    1.  Reset the password as the root user. 

        ``` {#codeblock_upx_vnv_o1t}
        Enter password for user root: #Specifies the initial password that you obtained in the previous step.
        The 'validate_password' plugin is installed on the server.
        The subsequent steps will run with the existing configuration of the plugin.
        Using existing password for root.
        Estimated strength of the password: 100 
        Change the password for root ? ((Press y|Y for Yes, any other key for No) : Y #Specifies whether to change the password of the root user. Press the Y key.
        New password: #Specifies a new password. The password must be 8 to 30 characters in length and must contain letters, digits, and special characters at the same time. The following special characters are allowed: parentheses (()), grave accents (`), tildes (~), exclamation points (!), at signs (@), number signs (#), dollar signs ($), percent signs (%), carets (^), ampersands (&), asterisks (*), hyphens (-), underscores (_), plus signs (+), equal signs (=), vertical bars (|), braces ({}), brackets ([]), colons (:), semicolons (;), apostrophes ('), angle brackets (<>), commas (,), periods (.), question marks (?), and forward slashes (/).
        Re-enter new password: #Confirms the new password.
        Estimated strength of the password: 100 
        Do you wish to continue with the password provided?( Press y|Y for Yes, any other key for No) : Y
        ```

    2.  Press the `Y` key to delete anonymous users. 

        ``` {#codeblock_lnt_dwr_1xk}
        By default, a MySQL installation has an anonymous user, allowing anyone to log into MySQL without having to have a user account created for them. This is intended only for testing, and to make the installation go a bit smoother. You should remove them before moving into a production environment.
        Remove anonymous users? (Press y|Y for Yes, any other key for No) : Y  #Specifies whether to delete anonymous users. Press the Y key.
        Success.
        ```

    3.  Press the `Y` key to disable remote logon as the root user. 

        ``` {#codeblock_rlv_w6z_zxh}
        Disallow root login remotely? (Press y|Y for Yes, any other key for No) : Y #Specifies whether to disable remote logon as a root user. Press the Y key.
        Success.
        ```

    4.  Press the `Y` key to delete the test database and the permission for accessing the test database. 

        ``` {#codeblock_xvi_g6d_8rg}
        Remove test database and access to it? (Press y|Y for Yes, any other key for No) : Y #Specifies whether to delete the test database and the permission for accessing the test database. Press the Y key.
        - Dropping test database...
        Success.
        ```

    5.  Press the `Y` key to reload the grant table. 

        ``` {#codeblock_eam_fo0_vtl}
        Reload privilege tables now? (Press y|Y for Yes, any other key for No) : Y #Specifies whether to reload the grant table. Press the Y key.
        Success.
        All done!
        ```


For more information, see [MySQL documentation](http://dev.mysql.com/doc/refman/5.7/en/mysql-secure-installation.html).

## Step 7: Configure PHP {#section_ual_v4d_k6e .section}

To configure PHP, follow these steps:

1.  In the /usr/share/php directory, create a phpinfo.php file to show PHP version information. Continue with these steps: 
    1.  Run the command `vim /usr/share/php/phpinfo.php` to open the file.
    2.  Press the `i` key to enter the edit mode.
    3.  Enter the following code: 

        ``` {#codeblock_6i5_2om_5un}
        <? php echo phpinfo(); ? >
        ```

    4.  Type `:wq` to save and close the file.
2.  Run the following command to start PHP-FPM. 

    ``` {#codeblock_rfz_eze_x0p}
    systemctl start php-fpm
    ```

3.  Run the following command to enable PHP-FPM to run at startup. 

    ``` {#codeblock_hz7_efe_fd5}
    systemctl enable php-fpm
    ```


## Step 8: Test the connection to the LNMP environment {#section_b0a_az5_erl .section}

To test the connection to the LNMP environment, follow these steps:

1.  Open your browser.
2.  In the address bar, enter the URL `http://<Public IP address of the ECS instance>/phpinfo.php`. 

    The following response indicates that the LNMP environment has been deployed.

    ![LNMP deployed](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64105/156862597744922_en-US.png)


Afterward, we recommend that you run the following command to delete /usr/share/php/phpinfo.php and secure your system.

``` {#codeblock_6zp_iaw_xzc}
rm -rf /usr/share/php/phpinfo.php
```

