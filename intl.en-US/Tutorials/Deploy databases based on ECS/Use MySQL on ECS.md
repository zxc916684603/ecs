# Use MySQL on ECS {#concept_221087 .concept}

MySQL is a relational database management system. It provides tools to build Web applications, such as applications based on the Linux, Apache, MySQL, PHP \(LAMP\) or Linux, NGINX, MySQL, PHP \(LNMP\) stack. This topic describes how to install, configure, and remotely access the MySQL database on an ECS instance.

## Related configuration {#section_ued_1q1_g4z .section}

This topic is based on the following software:

-   Operating system: public image for CentOS 7.2 64-bit
-   MySQL: 5.7.26

This topic is based on an Elastic Compute Service \(ECS\) instance with the following specification:

-   CPU: 2 vCPUs
-   Memory: 4 GiB
-   Network type: VPC
-   IP address: public IP address

## Prerequisites {#section_xxs_qhu_cic .section}

You have added inbound rules to the security group associated with the ECS instance. Port 3306 is open for inbound traffic. For more information, see [Add security group rules](../../../../intl.en-US/Security/Security groups/Add security group rules.md#).

## Procedure {#section_pwk_j0q_cjw .section}

1.  Prepare the environment.
2.  Install MySQL.
3.  Configure MySQL.
4.  Remotely access MySQL.

## Step 1: Prepare the environment {#section_ijl_88h_31z .section}

1.  Log on to the ECS instance. For more information, see [Connect to a Linux instance by using an SSH key pair](../../../../intl.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using an SSH key pair.md#) or [Connect to a Linux instance by using a password](../../../../intl.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using a password.md#).

## Step 2: Install MySQL {#section_52j_x9u_c07 .section}

1.  Run the following command to update the YUM repository.

    ``` {#codeblock_rhk_dmt_8r0}
    rpm -Uvh  http://dev.mysql.com/get/mysql57-community-release-el7-9.noarch.rpm
    ```

2.  Run the following command to install MySQL.

    ``` {#codeblock_m4a_csr_dlx}
    yum -y install mysql-community-server
    ```

3.  Run the following command to view the version of MySQL.

    ``` {#codeblock_hm0_w2n_num}
    mysql -V
    ```

    MySQL is successfully installed if the following is returned.

    ``` {#codeblock_bsc_9ng_303}
    mysql  Ver 14.14 Distrib 5.7.26, for Linux (x86_64) using  EditLine wrapper
    ```


## Step 3: Configure MySQL {#section_d1c_rd3_n3i .section}

1.  Run the following command to launch MySQL.

    ``` {#codeblock_3z9_og5_4v1}
    systemctl start mysqld
    ```

2.  Run the following command to enable MySQL to run at boot time.

    ``` {#codeblock_o4i_hpp_nks}
    systemctl enable mysqld
    ```

3.  Run the following command to view the /var/log/mysqld.log file and record the temporary password of the root user.

    ``` {#codeblock_1bm_ah3_7av}
    # grep 'temporary password' /var/log/mysqld.log
    2019-04-28T06:50:56.674085Z 1 [Note] A temporary password is generated for root@localhost: 3w)WqGlM7-o,
    ```

    **Note:** You need the temporary password when you reset the password for the root user.

4.  Run the following command to configure the security settings of MySQL.

    ``` {#codeblock_jwj_i8z_hi8}
    mysql_secure_installation
    ```

    The security settings of MySQL involve the following steps.

    1.  Reset the password for the root user.

        ``` {#codeblock_s9i_fjo_9wx}
        Enter password for user root: # Enter the temporary password for the root user that you previously obtained.
        The 'validate_password' plugin is installed on the server.
        The subsequent steps will run with the existing configuration of the plugin.
        Using existing password for root.
        Estimated strength of the password: 100 
        Change the password for root? (Press y|Y for Yes, any other key for No) : Y
        New password: # Enter a new password, that is 8 to 30 characters in length. It must contain uppercase and lowercase letters, digits, and special characters. The following special characters are allowed: ( ) ` ~ ! @ # $ % ^ & * - + = | { } [ ] : ; ' < > , . ? /
        Re-enter new password: # Re-enter the new password for confirmation.
        Estimated strength of the password: 100 
        Do you wish to continue with the provided password?( Press y|Y for Yes, any other key for No) : Y
        ```

    2.  Enter `Y` to disable the anonymous user account.

        ``` {#codeblock_2q8_vhy_pd1}
        By default, a MySQL installation has an anonymous user, allowing anyone to log into MySQL without having to have a user account created for them. This is intended only for testing, and to make the installation go a bit smoother. You should remove them before moving into a production environment.
        Remove anonymous users? (Press y|Y for Yes, any other key for No): Y
        Success.
        ```

    3.  Enter `Y` to deny remote access by the root user.

        ``` {#codeblock_335_a89_7dq}
        Disallow root login remotely? (Press y|Y for Yes, any other key for No): Y
        Success.
        ```

    4.  Enter `Y` to remove the test database and access permissions to this database.

        ``` {#codeblock_nk7_gl2_x3v}
        Remove test database and access to it? (Press y|Y for Yes, any other key for No): Y
        - Dropping test database...
        Success.
        ```

    5.  Enter `Y` to reload privilege tables.

        ``` {#codeblock_40a_ufp_hkq}
        Reload privilege tables now? (Press y|Y for Yes, any other key for No): Y
        Success.
        All done!
        ```

    For more information about security settings of MySQL, see [MySQL Documentation](https://dev.mysql.com/doc/refman/5.7/en/mysql-secure-installation.html).


## Step 4: Remotely access the MySQL database {#section_kpq_gxb_a3n .section}

You can use a database client or Data Management Service \(DMS\) provided by Alibaba Cloud to remotely access the MySQL database. In this topic, we take DMS as an example to describe how to remotely access the MySQL database.

1.  On the ECS instance, create an account for remote access to MySQL.
    1.  Run the following command and enter the password for the root user to log on to MySQL.

        ``` {#codeblock_ht0_jrd_ua4}
         mysql -uroot -p
        ```

    2.  Run the following commands in the order described here to create an account for remote logon to MySQL. In this example, we use `dms` as the account name and `123456` as the password.

        ``` {#codeblock_32p_bu9_qjx}
        mysql> grant all on *.* to 'dms'@'%'IDENTIFIED BY '123456'; # Replace dms with root to enable remote logon with the root account.
        mysql> flush privileges;
        ```

        **Note:** 

        -   We recommend that you use a non-root account to remotely log on to the MySQL database instead of using the root account.
        -   When you create an account, you need to replace the password `123456` with a password that meets the security strength requirements. It must be 8 to 30 characters in length and contain uppercase and lowercase letters, digits, and special characters. The following special characters are allowed: `( ) ` ~ ! @ # $ % ^ & * - + = | { } [ ] : ; ' < > , . ? /`.
2.  Log on to the [Data Management Service console](https://dms.console.aliyun.com/).
3.  In the left-side navigation pane, select User-created databases \(ECS, Internet\).
4.  Click **Add Database**.
5.  Configure the database that you have created. For more information, see [Configure user-created databases](../../../../intl.en-US/Migration Service/Databases in ECS instances/Manage user-created databases hosted on an ECS instance.md#table_lb1_hwg_chb).
6.  Click **Log On**.

    After logging on, you can use the menu bar of DMS to create databases, tables, functions, and other objects. For more information, see [Manage user-created databases that are hosted on ECS](../../../../intl.en-US/Migration Service/Databases in ECS instances/Manage user-created databases hosted on an ECS instance.md#postreq_bsc_mq1_dhb).


