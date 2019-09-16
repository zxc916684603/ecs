# Build a Drupal-based website on CentOS 7 {#concept_lqz_2p1_ffb .task}

This topic describes how to build a Drupal-based website on an ECS instance that runs CentOS 7.

You must have an Alibaba Cloud account before you follow the instructions provided in the tutorial. To create an Alibaba Cloud account, click [Create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).

Drupal is a free and open source content management framework \(CMF\) written in Hypertext Preprocessor \(PHP\). Drupal consists of a content management system \(CMS\) and a PHP development framework. You can use Drupal to build dynamic websites that provide various features and services, and to support website projects in different applications from personal blogs to large communities.

The procedure described in this topic is applicable to users that are familiar with Alibaba Cloud ECS instances and Linux, but new to website construction with ECS instances.

## Procedure {#section_z74_yzt_kll .section}

To build a Drupal-based website on an ECS instance, follow these steps:

1.  [Step 1: Activate an ECS instance](#section_i87_j52_9zo)
2.  [Step 2: Build the Web environment](#section_y3l_5ds_jz7)
3.  [Step 3: Install Drupal](#section_mdj_fvs_xov)

## Step 1: Activate an ECS instance {#section_i87_j52_9zo .section}

You can activate an ECS instance to build a personal website. In the follow-up management, you can upgrade the instance or optimize the architecture as needed.

## Step 2: Build the Web environment {#section_y3l_5ds_jz7 .section}

You can build the Web environment on the ECS instance in any of the following ways:

-   Image deployment
-   Easy deployment with an installation package
-   Manual deployment: Build the environment by using source code or Yellowdog Update, Modified \(YUM\).

We recommend that you use an image. This is an easy way to build the Web environment for the first time. If you have some basic knowledge of Linux operations and maintenance, you can use an installation package, the source code, or the YUM utility to customize the Web environment. This topic describes how to build the Drupal website by using an image.

1.  When you create an ECS instance, in the Image section, choose **Marketplace Image** \> **Select from image market including operating system**. For more information, see [Create an ECS instance](https://ecs.console.aliyun.com/#/create/prepay).
2.  Type **LAMP** in the search bar, click Search, and then select the first matched image in this example. 
3.  Click **Continue**.**** 

    You can also go to [Alibaba Cloud Marketplace](https://market.aliyun.com/software?spm=5176.8060583.401001.1.ReWWeQ), and search for and purchase the required images.

    In this topic, the software versions used in the environment include: `CentOS 7.2 | Apache 2.4.25 | MySQL 5.7.17 | PHP 7.1.1 |Drupal8.1.1`.

    **Note:** The versions that you download may be different in your actual running environment.


## Step 3: Install Drupal {#section_mdj_fvs_xov .section}

To install Drupal, follow these steps:

1.  Download the Drupal installation package. 

    ``` {#codeblock_eym_wte_4tz}
    # wget http://ftp.drupal.org/files/projects/drupal-8.1.1.zip
    ```

2.  Decompress the package to your website root directory. 

    ``` {#codeblock_dnw_tfi_yye}
    # unzip drupal-8.1.1.zip 
    # mv drupal-8.1.1/* /var/www/html/
    ```

3.  Download the Chinese translation package. 

    ``` {#codeblock_jb5_uss_5zb}
    # cd /var/www/html/
    # wget -P profiles/standard/translations http://ftp.drupal.org/files/translations/8.x/drupal/drupal-8.26.zh-hans.po
    ```

4.  Specify the owner and group of the sites directory. 

    ``` {#codeblock_dh0_o87_8d4}
    # chown -R apache:apache /var/www/html/sites
    ```

5.  Restart the Apache service. 

    ``` {#codeblock_cdb_vp2_n0e}
    # /etc/init.d/httpd restart
    ```

6.  Open your browser, and in the address bar, enter the URL "Public IP address of the ECS instance/index.php" to go to the Drupal installation page. Select the required language from the Choose Language drop-down list, and click **Save and continue**. 
7.  Select Standard, and click **Save and continue**. 
8.  Enter database information, and click **Save and continue**. 

    **Note:** After you log on to the MySQL database, you can run the following commands to customize the database information:

    -   DBNAME: database name
    -   UAERNAME: username
    -   IP: localhost or 127.0.0.1 for a local host
    -   YOURPASSWORD: database password
    ``` {#codeblock_mdp_tpg_qaz}
    mysql> CREATE DATABASE DBNAME;
    mysql> CREATE USER UAERNAME;
    mysql> GRANT ALL PRIVILEGES ON *. * TO 'UAERNAME'@'IP' IDENTIFIED BY 'YOURPASSWORD' WITH GRANT OPTION;  
    mysql> FLUSH PRIVILEGES;
    ```

9.  At the end of automatic installation, go to the website settings page, enter site information, and then click **Save and continue**. 

Afterward, you can customize your website pages.

