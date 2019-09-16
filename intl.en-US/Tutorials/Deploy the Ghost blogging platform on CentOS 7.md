# Deploy the Ghost blogging platform on CentOS 7 {#concept_npp_vh1_ffb .task}

Ghost is a free open source blogging platform developed on the basis of Node.js. The platform is used to simplify the online publishing process for individual blogs and online publications. This topic describes how to deploy the Ghost blogging platform.

You must have an Alibaba Cloud account before you follow the instructions provided in the tutorial. To create an Alibaba Cloud account, click [Create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).

As your business scope is increasingly enlarged, you can use comprehensive services of Alibaba Cloud to scale up and scale out your business capacity. For example, you can optimize your business in the following ways:

-   Scale up the vCPU and memory of a single ECS instance to enhance the processing performance.
-   Add multiple ECS instances and implement load balancing among these instances.
-   Use Auto Scaling to automatically increase or decrease the number of ECS instances based on business requirements.
-   Use Object Storage Service \(OSS\) to store a large amount of data such as static web pages, images, and videos.

This topic describes how to deploy the Ghost blogging platform on an ECS instance that has basic configurations. The procedure described in this topic is applicable to individual users that are new to website construction with ECS instances.

## Procedure {#section_uei_jeb_jyf .section}

To deploy the Ghost blogging platform on an ECS instance, follow these steps:

1.  [Step 1: Create a Linux-based ECS instance](#section_lll_v4o_d8l)
2.  [Step 2: Deploy the Web environment](#section_3as_stl_g30)
3.  [Step 3: Install Ghost](#section_ab9_fr6_oj6)
4.  [Step 4: Purchase a domain](#section_vhr_y2k_pga)
5.  [Step 5: Apply for an ICP filing](#section_6ph_sb6_rb4)
6.  [Step 6: Resolve the domain name to the IP address of the instance](#section_b35_s43_byu)

## Step 1: Create a Linux-based ECS instance {#section_lll_v4o_d8l .section}

To build an individual website, you need only one ECS instance.

This section describes how to create an ECS instance. If you have a custom image, you can create an instance from this image. For more information, see [Create an instance by using a custom image](../intl.en-US/Instances/Create an instance/Create an instance by using a custom image.md#).

Create a Linux-based ECS instance. For more information, see [Create an instance by using the wizard](../intl.en-US/Instances/Create an instance/Create an instance by using the wizard.md#).

To set parameters, follow these rules:

-   **Instance Type**: For an individual website, you can use an instance of **1 vCPU and 2 GiB** or **2 vCPUs and 4 GiB** to meet basic requirements. For more information about instance types, see [Instance families](../intl.en-US/Instances/Instance families.md#).
-   **Network Type**: Click **VPC** in the Network Type section.
-   **Network Billing Method**: To enable the ECS instance to connect to the Internet, you must configure an Elastic IP address \(EIP\) and attach the EIP to the ECS instance. If you do not select **Assign Public IP Address**, the ECS instance has no public IP address configured. The actual configurations depend on your requirements.
-   **Image**: To build a website, you can click Public Image, and select a Linux operating system such as **CentOS** from the drop-down list.

After you create an instance, the system sends you an SMS message and an email to notify you of the information about the instance, such as the instance name, public IP address, and internal IP address. You can use the information to log on to the ECS console and manage the instance.

The system notifies you of most important information by sending SMS messages. To authenticate some important operations such as restarting or stopping the instance, you must use your mobile phone to receive verification codes. Therefore, after you bind a mobile number to your Alibaba Cloud account, you must keep the corresponding mobile phone in the normal running status.

## Step 2: Deploy the Web environment {#section_3as_stl_g30 .section}

This section describes how to deploy the Web environment by installing NGINX.

The software package provides NGINX 1.10.2.

**Note:** This version is used in the following example. The version that you download may be different in your actual running environment.

Prerequisites:

-   Your instance can connect to the Internet.
-   You have installed a tool for connecting to the Linux-based ECS instance. SecureCRT is used as the tool in this section.

To deploy the Web environment, follow these steps:

1.  Open the SecureCRT client and specify the information of the instance that you want to log on to. 

    1.  Specify the name of the session for connecting to the ECS instance.
    2.  Select **SSH** from the Protocol drop-down list.
    3.  Enter the host IP address in the Hostname field and specify the username.
    4.  Click **Connect**.
    ![Set logon information](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156862687312471_en-US.png)

2.  Enter the root username and the password. 

    ![Enter the username and the password](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156862687312472_en-US.png)

3.  Add the NGINX repository. 

    ``` {#codeblock_aqb_qow_fzu}
    [root@localhost ~]#rpm -Uvh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
    ```

4.  Install NGINX. 

    ``` {#codeblock_a2n_woi_jqe}
    [root@localhost ~]#yum -y install nginx
    ```

5.  Enable NGINX to run at startup. 

    ``` {#codeblock_ovp_cuv_qpc}
    [root@localhost ~]# systemctl enable nginx.service
    ```

6.  Start NGINX and check the NGINX service status. 

    ``` {#codeblock_dd9_1iv_c5d}
    [root@localhost ~]#systemctl start nginx.service
    [root@localhost ~]#systemctl status nginx.service
    ```

7.  Open your browser, and in the address bar, enter the public IP address of the ECS instance to view the default NGINX web page. 

    ![NGINX web page](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156862687312474_en-US.png)


Then, the NGINX environment is ready to run.

## Step 3: Install Ghost {#section_ab9_fr6_oj6 .section}

To install Ghost, follow these steps:

1.  Run the following command to update system software to the latest versions. 

    ``` {#codeblock_16z_981_r0u}
    [root@localhost ~]# yum -y update
    ```

2.  Install Node.js. 
    1.  Install Extra Packages for Enterprise Linux \(EPEL\). 

        ``` {#codeblock_2zk_25s_dtc}
        [root@localhost ~]# yum install epel-release -y
        ```

    2.  Install Node.js and npm. 

        ``` {#codeblock_6kf_whh_vdf}
        [root@localhost ~]# yum install nodejs npm --enablerepo=epel
        ```

    3.  Install the process manager to control Node.js applications. This process manager keeps the applications in the running state. 

        ``` {#codeblock_rbo_756_1yq}
        [root@localhost ~]# npm install pm2 -g
        ```

    4.  Run the commands `node -v` and `npm -v` to check the Node.js version.
3.  Install Ghost. 
    1.  Create the Ghost installation directory. 

        ``` {#codeblock_l08_nn2_uau}
        [root@localhost ~]# mkdir -p /var/www/ghost
        ```

    2.  Enter the Ghost installation directory, and run the following command to download the latest Ghost version. 

        ``` {#codeblock_yhi_jgk_vvk}
        [root@localhost ~]# cd /var/www/ghost
        [root@localhost ghost]# curl -L https://ghost.org/zip/ghost-latest.zip -o ghost.zip
        ```

    3.  Decompress the Ghost package. 

        ``` {#codeblock_21c_odl_b35}
        [root@localhost ghost]# yum install unzip -y
        [root@localhost ghost]# unzip ghost.zip
        ```

    4.  Use npm to install Ghost. 

        ``` {#codeblock_erl_30h_bsm}
        [root@localhost ghost]# npm install -production
        ```

    5.  Run the `npm start` command to start Ghost and check whether Ghost has been installed.
    6.  Create a copy of the example configuration file config.example.js, and rename the file as config.js. 

        ``` {#codeblock_htr_xmc_07z}
        [root@localhost ghost]# cp config.example.js config.js
        ```

    7.  In the config.js file, specify the domain of the Ghost blogging platform as the URL. 

        ``` {#codeblock_0c7_5un_klg}
        [root@localhost ghost]# vim config.js
        ```

        ![Specify the domain](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156862687312477_en-US.png)

    8.  Use the process manager to enable Ghost to run permanently. 

        ``` {#codeblock_yih_off_8hr}
        [root@localhost ghost]# NODE_ENV=production pm2 start index.js --name "ghost"
        ```

    9.  Start, stop, and then restart Ghost. 

        ``` {#codeblock_1un_5x2_4cc}
        [root@localhost ghost]# pm2 start ghost
        [root@localhost ghost]# pm2 stop ghost
        [root@localhost ghost]# pm2 restart ghost
        ```

4.  Install NGINX. 
    1.  Add the NGINX repository. 

        ``` {#codeblock_qiz_i1x_gtn}
        [root@localhost ~]# rpm -Uvh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
        ```

    2.  Install NGINX. 

        ``` {#codeblock_hq9_6rg_iav}
        [root@localhost ~]# yum -y install nginx
        ```

    3.  Enable NGINX to run at startup. 

        ``` {#codeblock_rxh_fim_8sz}
        [root@localhost ~]# systemctl enable nginx.service
        ```

    4.  Start NGINX and check the NGINX service status. 

        ``` {#codeblock_5i4_clv_le2}
        [root@localhost ~]#systemctl start nginx.service
        [root@localhost ~]#systemctl status nginx.service
        ```

    5.  Open your browser, and in the address bar, enter the public IP address of the ECS instance to view the default NGINX web page. 

        ![NGINX web page](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156862687312478_en-US.png)

5.  Specify NGINX as the reverse proxy for Ghost. 
    1.  Enter the NGINX configuration directory, and create the NGINX configuration file for Ghost. 

        ``` {#codeblock_kpf_idi_dc8}
        [root@localhost ~]#vim /etc/nginx/conf.d/ghost.conf
        ```

    2.  Add the following content to the ghost.conf file, and set server\_name to the domain that is used in your actual running environment. 

        ![Specify the domain](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156862687312479_en-US.png)

    3.  Change the name of the default configuration file default.conf to default.conf.bak, so NGINX is only applicable to ghost.conf. 

        ``` {#codeblock_mp4_zec_nhr}
        [root@localhost ~]#mv default.conf default.conf.bak
        ```

    4.  Restart the NGINX service. 

        ``` {#codeblock_ydk_fsi_p74}
        [root@localhost conf.d]# systemctl restart nginx.service
        ```

6.  Connect to the Ghost blogging platform. 
    1.  Open your browser, and in the address bar, enter the URL http://IP address of the ECS instance or http://Domain of the Ghost blogging platform to connect to the Ghost blogging platform. 

        ![Ghost web page](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156862687312480_en-US.png)

        **Note:** If the system returns Error Code 502, check whether you have disabled the firewall.

    2.  To edit your Ghost blogging platform, open your browser, and in the address bar, enter the URL http://IP address of the ECS instance/ghost. 

        ![Edit the Ghost blogging platform](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156862687412481_en-US.png)


## Step 4: Purchase a domain {#section_vhr_y2k_pga .section}

You can specify a unique domain for your website. Therefore, users can visit your website by using a simple domain instead of a complex IP address.

We recommend that you visit [www.net.cn](https://wanwang.aliyun.com/) to purchase a domain.

1.  Go to the [Domains](https://wanwang.aliyun.com/) page, enter the domain that you want to use in the search bar, and then click Find A Domain. If the searched domain has not been registered, you can purchase the domain. Specify the domain that you want to purchase and the service duration for the domain, and click Buy Now. 
2.  When you confirm the order, you must specify **the owner of the domain**. To simplify the operation, we recommend that you select **Person** temporarily. You can change the owner in the follow-up management. In this example, a personal domain is specified.
3.  If you purchase the domain for the first time, you must create the registrant profile. For more information, see [Create the registrant profile](https://domain.console.aliyun.com/#/infotemplate). 
4.  Enter the authentic registrant profile. 
5.  To pass the real-name verification, upload the scanned image of your identity card. The profile verification takes one to five working days.

## Step 5: Apply for an ICP filing {#section_6ph_sb6_rb4 .section}

You must apply for an IPC filing for the domain that is associated with a website hosted on a server in Mainland China. Your website cannot provide services until you obtain the ICP license number for the domain.

The Alibaba Cloud ICP Filing system can help you simplify the ICP filing procedure. You can apply for an ICP filing free of charge. The review duration is approximately 20 days.

1.  Log on to the [ICP Filing Management console](https://bsn.console.aliyun.com/#/bsnApply/ecs).
2.  In the left-side navigation pane, choose **ICP Filing Management** \> **ICP No. Application**, and click **Apply** to apply for the service identification number for the ECS instance that you have purchased. You will use the service identification number when you register an ICP filing. 
3.  In the dialog box that appears, click **OK**.
4.  After the system issues the service identification number, the ICP No. Management tab appears and displays the service identification number that is associated with the ECS instance. For more information about ICP filing, click the **Filing Introduction** tab. 
5.  If you apply for an ICP filing for the first time, you must register an IPC filing account in the [Alibaba Cloud ICP Filing system](https://beian.gein.cn/account/login.htm). 

    **Note:** The IPC filing account is used only for ICP filing and different from an Alibaba Cloud account.


## Step 6: Resolve the domain name to the IP address of the instance {#section_b35_s43_byu .section}

You must resolve the domain name to the IP address of the ECS instance, so users can visit your website by using the domain name. Follow these steps:

1.  Log on to the [Domain console](https://netcn.console.aliyun.com/core/domain/list).
2.  In the left-side navigation pane, choose **Domain** \> **Domain Names**. Find the domain name that you want to resolve, and in the **Actions** column next to the domain name, click **Resolve**. 
3.  Click **Getting Started**.
4.  Enter the public IP address of your Linux-based instance in the dialog box that appears, and click **Submit**. 

Then, you can use the domain name to visit your website.

