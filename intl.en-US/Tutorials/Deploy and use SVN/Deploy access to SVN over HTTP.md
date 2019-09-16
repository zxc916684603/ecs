# Deploy access to SVN over HTTP {#task_1597497 .task}

This topic describes how to deploy access to Apache Subversion \(SVN\) over HTTP.

You must have an Alibaba Cloud account before you follow the instructions provided in the tutorial. To create an Alibaba Cloud account, click [Create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).

In this topic, the following software versions are used to manually deploy SVN. The versions may be different in your actual running environment.

-   Operating system: public image 64-bit CentOS 7.2
-   Subversion: version 1.7.14
-   Apache HTTP Server: version 2.4.6

## Procedure {#section_qiv_j37_8qr .section}

To deploy access to SVN over HTTP, follow these steps:

1.  [Install SVN](#section_gyu_lbx_856)
2.  [Install Apache](#section_ily_okj_kbz)
3.  [Install mod\_dav\_svn](#section_gbn_l1r_5yj)
4.  [Configure SVN](#section_ed8_meq_o0d)
5.  [Configure Apache](#section_dk7_05x_t3w)
6.  [Configure the security group rules](#section_ggx_hu5_701)
7.  [Use a browser to test access to SVN](#section_svb_rm4_e81)

## Step 1: Install SVN {#section_gyu_lbx_856 .section}

To install SVN, follow these steps:

1.  [Connect to a Linux instance by using a password](../intl.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using a password.md#).
2.  Run the following command to install SVN. 

    ``` {#codeblock_6lv_c0n_jrc}
    yum install subversion
    ```

3.  Run the following command to check the SVN version. 

    ``` {#codeblock_8as_yc3_nxy}
    svnserve --version
    ```


## Step 2: Install Apache {#section_ily_okj_kbz .section}

To install Apache, follow these steps:

1.  Run the following command to install the Hypertext Transfer Protocol daemon \(HTTPd\). 

    ``` {#codeblock_pmq_rpw_jkz}
    yum install httpd
    ```

2.  Run the following command to check the HTTPd version. 

    ``` {#codeblock_bu4_pih_aey}
    httpd -version
    ```


## Step 3: Install mod\_dav\_svn {#section_gbn_l1r_5yj .section}

Run the following command to install mod\_dav\_svn.

``` {#codeblock_mu2_eil_swx}
yum install mod_dav_svn
```

## Step 4: Configure SVN {#section_ed8_meq_o0d .section}

To configure SVN, follow these steps:

1.  Run the following command to create a root directory for an SVN repository. 

    ``` {#codeblock_h70_mqa_qxs}
    mkdir /var/svn
    ```

2.  Run the following command to create an SVN repository. 

    ``` {#codeblock_qtv_rb0_9pa}
    svnadmin create /var/svn/svnrepo
    ```

3.  Run the following command to specify apache as the user group of the SVN repository. 

    ``` {#codeblock_8zo_suk_q8j}
    chown -R apache:apache /var/svn/svnrepo
    ```

4.  Run the following command to create a configuration file named passwd. 

    ``` {#codeblock_26i_osj_w9x}
    touch /var/svn/passwd 
    ```

5.  Run the following command to create the admin user and set the password. In this example, set the password to admin123. 

    ``` {#codeblock_qcv_gqo_rjv}
    htpasswd /var/svn/passwd admin
    ```

6.  Run the following command to create an access permission file. 

    ``` {#codeblock_3md_sng_zq2}
    cp /var/svn/svnrepo/conf/authz /var/svn/authz
    ```


## Step 5: Configure Apache {#section_dk7_05x_t3w .section}

To configure Apache, follow these steps:

1.  Run the command `vim /etc/httpd/conf.d/subversion.conf` to open the HTTPd configuration file.
2.  Press the `i` key to enter the edit mode.
3.  Enter the following configuration information: 

    ``` {#codeblock_dna_p1u_ag7}
    <Location /svn>
    DAV svn
    SVNParentPath /var/svn
    AuthType Basic
    AuthName "Authorization SVN"
    AuthzSVNAccessFile /var/svn/authz
    AuthUserFile /var/svn/passwd
    Require valid-user
    </Location>
    ```

4.  Press the `Esc` key, and type `:wq` to save and close the file.
5.  Run the following command to start the Apache HTTP Server. 

    ``` {#codeblock_1fn_ela_x1s}
    systemctl start httpd.service
    ```


## Step 6: Configure the security group rules {#section_ggx_hu5_701 .section}

The SVN server listens on TCP Port 3690 by default. You must log on to the ECS console to add TCP Port 3690 to the security group. For more information, see [Add security group rules](../intl.en-US/Security/Security groups/Add security group rules.md#).

## Step 7: Use a browser to test access to SVN {#section_svb_rm4_e81 .section}

To test access to SVN in a browser, follow these steps:

1.  Open your browser.
2.  In the address bar, enter the URL `http://<Public IP address of the ECS instance>/svn/<SVN repository name>`, and press the Enter key. In this example, the SVN repository name is svnrepo.
3.  Enter your username and password that you have configured in the passwd file. In this example, the username is admin and the password is admin123. 

    The following response indicates that you have accessed the SVN repository that you have created.

    ![Access result](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/156862703344304_en-US.png)


