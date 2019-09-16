# Deploy access to SVN by using svnserve {#task_1597495 .task}

This topic describes how to deploy access to Apache Subversion \(SVN\) by using svnserve.

You must have an Alibaba Cloud account before you follow the instructions provided in the tutorial. To create an Alibaba Cloud account, click [Create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).

In this topic, the following software versions are used to manually deploy SVN. The versions may be different in your actual running environment.

-   Operating system: public image 64-bit CentOS 7.2
-   Subversion: version 1.7.14
-   Apache HTTP Server: version 2.4.6

## Procedure {#section_fxi_ocf_52q .section}

To deploy access to SVN by using svnserve, follow these steps:

1.  [Step 1: Install SVN](#section_h54_dqf_pyz)
2.  [Step 2: Configure SVN](#section_qui_xbb_dke)
3.  [Step 3: Configure the security group rules](#section_9qx_vu2_6zo)
4.  [Step 4: Use a Windows client to test the SVN service](#section_frq_nei_7ay)

## Step 1: Install SVN {#section_h54_dqf_pyz .section}

You can install SVN in any of the following ways:

-   Use an SVN image from Alibaba Cloud Marketplace
    1.  Click [here](https://market.aliyun.com/products/55530001/jxsc000061.html) to purchase an SVN image in Alibaba Cloud Marketplace.
    2.  Click **Choose Your Plan**.
    3.  Enter the account and password to log on to the ECS console.
    4.  In the Image section, the Selected Image field shows the specified SVN image. Continue with other settings and activate the ECS instance. For more information, see [Create an instance by using the wizard](../intl.en-US/Instances/Create an instance/Create an instance by using the wizard.md#).
-   Install SVN manually
    1.  [Connect to a Linux instance by using a password](../intl.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using a password.md#).
    2.  Run the following command to install SVN.

        ``` {#codeblock_90i_lm5_qzi}
        yum install subversion
        ```

    3.  Run the following command to check the SVN version.

        ``` {#codeblock_6ml_3bk_pyo}
        svnserve --version
        ```

        ![Check the SVN version](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/156862701112528_en-US.png)


## Step 2: Configure SVN {#section_qui_xbb_dke .section}

To configure SVN, follow these steps:

1.  Run the following command to create a root directory for an SVN repository. 

    ``` {#codeblock_mvg_f02_stx}
    mkdir /var/svn
    ```

2.  Run the following commands in sequence to create an SVN repository. 

    ``` {#codeblock_xbm_t6r_2y3}
    # cd /var/svn
    # svnadmin create /var/svn/svnrepos
    ```

3.  Run the following commands in sequence to check files in the SVN repository. 

    ``` {#codeblock_0z1_5zd_n4s}
    # cd svnrepos
    # ls
    ```

    ![Check files in the SVN repository](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/156862701112529_en-US.png)

    The SVN directories are described as follows:

    |Directory|Description|
    |---------|-----------|
    |db|Stores all version control data files.|
    |hooks|Stores hook scripts.|
    |locks|The client used to track access to the SVN repository.|
    |format|A text file that contains only one integer, indicating the version number of the current SVN repository.|
    |conf|The configuration file of the SVN repository, including the username and permissions for accessing the repository.|

4.  Set the username and password of the SVN repository. 
    1.  Run the `cd conf/` command.
    2.  Run the `vi passwd` command to open the configuration file.
    3.  Press the `i` key to enter the edit mode.
    4.  Move the pointer to the `[users]` field, and add the username and password. 

        **Note:** You can add the username and password in the following format: username = password. For example, suzhan \(username\) = redhat \(password\), as shown in the following figure. There must be a space on both ends of the equal sign \(=\).

        ![Add the username and password](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/156862701112530_en-US.png)

    5.  Press the `Esc` key to exit the edit mode, and type `:wq` to save and close the file.
5.  Set the read and write permissions for the username. 
    1.  Run the `vi authz` command to open the permission control file.
    2.  Press the `i` key to enter the edit mode.
    3.  Move the pointer to the end of the file, and add the following code. In the code, suzhan specifies the username, r specifies the read permission, and w specifies the write permission. 

        ``` {#codeblock_5cv_jpj_877}
        [/]
        suzhan=rw
        ```

    4.  Press the `Esc` key to exit the edit mode, and type `:wq` to save and close the file. 

        ![Set the read and write permissions for the username](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/156862701112531_en-US.png)

6.  Modify the configurations of the SVN service. 
    1.  Run the command `vi svnserve.conf` to open the configuration file of the SVN service.
    2.  Press the `i` key to enter the edit mode.
    3.  Move the pointer to the following lines, and delete the number sign \(\#\) and space at the beginning of each line: 

        ``` {#codeblock_lif_rae_bf5}
        anon-access = read #Assigns read permissions to anonymous users. You can also specify anon-access = none to disable access by anonymous users. If you set anon-access to none, the revision history of the SVN service shows dates.
        auth-access = write #Authorizes the write permission.
        password-db = passwd #Specifies the password database file.
        authz-db = authz #Specifies the file that stores the authorization rules for path-based access control.
        realm = /var/svn/svnrepos #Specifies the authorization realm of the repository.
        ```

        **Note:** Each line cannot start with a space and there must be a space on both ends of the equal sign \(=\).

        ![Modify the configurations of the SVN service](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/156862701112532_en-US.png)

    4.  Press the `Esc` key to exit the edit mode, and type `:wq` to save and close the file.
7.  Run the following command to start the SVN repository. 

    ``` {#codeblock_2wb_bxm_m7c}
    svnserve -d -r /var/svn/
    ```

8.  Run the command `ps -ef |grep svn` to check whether the SVN service has been started. 

    The following response indicates that the SVN service has been started.

    ![Check the SVN service status](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/156862701112533_en-US.png)

    **Note:** Run the command `killall svnserve` to stop the SVN service.


## Step 3: Configure the security group rules {#section_9qx_vu2_6zo .section}

The SVN server listens on TCP Port 3690 by default. You must log on to the [ECS console](https://ecs.console.aliyun.com/#/home) to add TCP Port 3690 to the security group. For more information, see [Add security group rules](../intl.en-US/Security/Security groups/Add security group rules.md#).

## Step 4: Use a Windows client to test the SVN service {#section_frq_nei_7ay .section}

To test the SVN service by using a Windows client, follow these steps:

1.  Download and install a [TortoiseSVN client](http://tortoisesvn.net/downloads.html) on your local computer.
2.  Right-click the local project folder. In this example, the project folder is C:\\KDR.
3.  On the menu that appears, select **SVN Checkout**.
4.  Apply the following settings, and click **OK**. 

    -   Set the **URL of repository** field in this format: svn://Public IP address of the ECS instance/SVN repository name. In this example, the SVN repository name is svnrepos.
    -   Set the **Checkout directory** field. In this example, the directory is C:\\KDR.
    ![Checkout settings](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/156862701112535_en-US.png)

    **Note:** During the logon for the first time, you must provide the username and password that you have configured in the passwd file.


