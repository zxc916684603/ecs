# 手动部署MySQL数据库（Linux） {#concept_221087 .task}

MySQL是一个关系型数据库管理系统，常用于搭建LAMP和LNMP等网站。本教程介绍如何在Linux系统ECS实例上安装、配置以及远程访问MySQL数据库。

使用本教程进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm?)。

您已在ECS实例所使用的安全组入方向添加规则并放行3306端口。具体步骤，请参见[添加安全组规则](../cn.zh-CN/安全/安全组/添加安全组规则.md#)。

本教程在示例步骤中使用了以下版本软件。实际操作时，请以您的软件版本为准。

-   操作系统：公共镜像CentOS 7.2 64位
-   MySQL：5.7.26

本教程在示例步骤中使用了以下配置的ECS实例。 实际操作时，请以您的实例配置为准。

-   CPU：2 vCPU
-   内存：4 GiB
-   网络类型：专有网络
-   IP地址：公网IP

在Linux实例上部署MySQL数据库的基本流程为：

-   [步骤一：准备环境](#section_fe0_pfu_e7r)
-   [步骤二：安装MySQL](#section_jg8_cz7_8pw)
-   [步骤三：配置MySQL](#section_gsn_kwf_xxy)
-   [步骤四：远程访问MySQL数据库](#section_jcj_rd6_yih)

## 步骤一：准备环境 {#section_fe0_pfu_e7r .section}

连接您的ECS实例。具体操作，请参见[使用SSH密钥对连接Linux实例](../cn.zh-CN/实例/连接实例/连接Linux实例/使用SSH密钥对连接Linux实例.md#)或[使用用户名密码验证连接Linux实例](../cn.zh-CN/实例/连接实例/连接Linux实例/使用用户名密码验证连接Linux实例.md#)。

## 步骤二：安装MySQL {#section_jg8_cz7_8pw .section}

完成以下操作，安装MySQL。

1.  运行以下命令更新YUM源。 

    ``` {#codeblock_diz_hdo_b6b}
    rpm -Uvh  http://dev.mysql.com/get/mysql57-community-release-el7-9.noarch.rpm
    ```

2.  运行以下命令安装MySQL。 

    ``` {#codeblock_dez_ib3_tns}
    yum -y install mysql-community-server
    ```

3.  运行以下命令查看MySQL版本号。 

    ``` {#codeblock_ps0_zws_2hr}
    mysql -V
    ```

    返回结果如下，表示MySQL安装成功。

    ``` {#codeblock_31s_pbf_jia}
    mysql  Ver 14.14 Distrib 5.7.26, for Linux (x86_64) using  EditLine wrapper
    ```


## 步骤三：配置MySQL {#section_gsn_kwf_xxy .section}

完成以下操作，配置MySQL。

1.  运行以下命令启动MySQL服务。 

    ``` {#codeblock_cfo_jw0_7bj}
    systemctl start mysqld
    ```

2.  运行以下命令设置MySQL服务开机自启动。 

    ``` {#codeblock_c05_kaa_waq}
    systemctl enable mysqld
    ```

3.  运行以下命令查看/var/log/mysqld.log文件，获取并记录root用户的初始密码。 

    ``` {#codeblock_0z8_hf1_ybq}
    # grep 'temporary password' /var/log/mysqld.log
    2019-04-28T06:50:56.674085Z 1 [Note] A temporary password is generated for root@localhost: 3w)WqGlM7-o,
    ```

    **说明：** 下一步重置root用户密码时，会使用该初始密码。

4.  运行下列命令对MySQL进行安全性配置。 

    ``` {#codeblock_isw_4eq_igx}
    mysql_secure_installation
    ```

    安全性的配置包含以下五个方面：

    1.  重置root用户的密码。 

        ``` {#codeblock_xh5_0h0_hqr}
        Enter password for user root: #输入上一步获取的root用户初始密码
        The 'validate_password' plugin is installed on the server.
        The subsequent steps will run with the existing configuration of the plugin.
        Using existing password for root.
        Estimated strength of the password: 100 
        Change the password for root ? ((Press y|Y for Yes, any other key for No) : Y #是否更改root用户密码，输入Y
        New password: #输入新密码，长度为8至30个字符，必须同时包含大小写英文字母、数字和特殊符号。特殊符号可以是()` ~!@#$%^&*-+=|{}[]:;‘<>,.?/
        Re-enter new password: #再次输入新密码
        Estimated strength of the password: 100 
        Do you wish to continue with the password provided?(Press y|Y for Yes, any other key for No) : Y
        ```

    2.  输入`Y`删除匿名用户账号。 

        ``` {#codeblock_1li_zcw_n3x}
        By default, a MySQL installation has an anonymous user, allowing anyone to log into MySQL without having to have a user account created for them. This is intended only for testing, and to make the installation go a bit smoother. You should remove them before moving into a production environment.
        Remove anonymous users? (Press y|Y for Yes, any other key for No) : Y  #是否删除匿名用户，输入Y
        Success.
        ```

    3.  输入`Y`禁止root账号远程登录。 

        ``` {#codeblock_hr8_kt7_wmp}
        Disallow root login remotely? (Press y|Y for Yes, any other key for No) : Y #禁止root远程登录，输入Y
        Success.
        ```

    4.  输入`Y`删除test库以及对test库的访问权限。 

        ``` {#codeblock_oqj_b0e_lc9}
        Remove test database and access to it? (Press y|Y for Yes, any other key for No) : Y #是否删除test库和对它的访问权限，输入Y
        - Dropping test database...
        Success.
        ```

    5.  输入`Y`重新加载授权表。 

        ``` {#codeblock_ly9_58r_o29}
        Reload privilege tables now? (Press y|Y for Yes, any other key for No) : Y #是否重新加载授权表，输入Y
        Success.
        All done!
        ```

    安全性配置的更多详情，请参见[MySQL官方文档](https://dev.mysql.com/doc/refman/5.7/en/mysql-secure-installation.html)。


## 步骤四：远程访问MySQL数据库 {#section_jcj_rd6_yih .section}

您可以使用数据库客户端或阿里云提供的数据管理服务DMS（Data Management Service）来远程访问MySQL数据库。本节以DMS为例，介绍远程访问MySQL数据库的操作步骤。

1.  在ECS实例上，创建远程登录MySQL的账号。 
    1.  运行以下命令后，输入root用户的密码登录MySQL。 

        ``` {#codeblock_w50_c08_wwd}
         mysql -uroot -p
        ```

    2.  依次运行以下命令创建远程登录MySQL的账号。示例账号为`dms`、密码为`123456`。 

        ``` {#codeblock_pge_auj_4g5}
        mysql> grant all on *.* to 'dms'@'%'IDENTIFIED BY '123456'; #使用root替换dms，可设置为允许root账号远程登录。
        mysql> flush privileges;
        ```

        **说明：** 

        -   建议您使用非root账号远程登录MySQL数据库。
        -   实际创建账号时，需将`123456`更换为符合要求的密码： 长度为8至30个字符，必须同时包含大小写英文字母、数字和特殊符号。特殊符号可以是`()` ~!@#$%^&*-+=|{}[]:;‘<>,.?/`。
2.  登录[数据管理控制台](https://dms.console.aliyun.com/)。
3.  在左侧导航栏中，选择自建库（ECS、公网）。
4.  单击**新建数据库**。
5.  配置自建数据库信息。 配置详情，请参见[配置自建数据库](../cn.zh-CN/迁移服务/ECS自建数据库/管理ECS实例自建数据库.md#table_lb1_hwg_chb)。
6.  单击**登录**。 成功登录后，您可以使用DMS提供的菜单栏功能，创建数据库、表、函数等，详情请参见[管理ECS自建数据库](../cn.zh-CN/迁移服务/ECS自建数据库/管理ECS实例自建数据库.md#postreq_bsc_mq1_dhb)。

