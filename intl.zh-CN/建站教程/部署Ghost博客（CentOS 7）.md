# 部署Ghost博客（CentOS 7） {#concept_npp_vh1_ffb .task}

Ghost是一个基于Node.js开发的免费开源博客平台，用于简化个人博客和在线出版物的在线发布过程。本文介绍了部署Ghost博客的详细步骤。

使用本教程进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.alibabacloud.com/register/intl_register.htm)。

随着业务的扩展，您可以使用阿里云强大的产品平台，平滑地横向和纵向扩展服务容量，例如：

-   扩展单个ECS实例的CPU和内存规格，增强服务器的处理能力。
-   增加多台ECS实例，并利用负载均衡，在多个实例中进行负载的均衡分配。
-   利用弹性伸缩（Auto Scaling），根据业务量自动增加或减少ECS实例的数量。
-   利用对象存储OSS（Object Storage Service），存储静态网页和海量图片、视频等。

本文档介绍如何使用一台基本配置的云服务器ECS实例搭建Ghost。适用于初次使用阿里云进行建站的个人用户。

## 操作步骤 {#section_uei_jeb_jyf .section}

使用云服务器ECS搭建Ghost网站的操作步骤如下：

1.  [创建Linux实例](#section_lll_v4o_d8l)
2.  [部署Web环境](#section_3as_stl_g30)
3.  [安装Ghost](#section_ab9_fr6_oj6)
4.  [购买域名](#section_vhr_y2k_pga)
5.  [备案](#section_6ph_sb6_rb4)
6.  [配置域名解析](#section_b35_s43_byu)

## 步骤一：创建Linux实例 {#section_lll_v4o_d8l .section}

对于个人使用的小型网站，一台ECS实例可以满足基本需求。

本节介绍如何创建全新实例。如果您有镜像，也可以使用自定义镜像创建实例。具体操作，请参见[使用自定义镜像创建实例](../intl.zh-CN/实例/创建实例/使用自定义镜像创建实例.md#)。

创建一台Linux实例。具体步骤，请参见[使用向导创建实例](../intl.zh-CN/实例/创建实例/使用向导创建实例.md#)。

在配置参数时，您需要注意以下几点：

-   **实例**：对于个人网站，实例规格为**1vCPU 2GiB**或**2vCPU 4GiB**就能满足基本需求。关于实例规格的详细介绍，请参见[实例规格族](../intl.zh-CN/实例/实例规格族.md#)。
-   **网络**：选择**专有网络**。
-   **公网带宽**：如果不选中**分配公网IPv4地址**，则不为实例分配公网IP地址。ECS实例如需访问公网，需要配置并绑定弹性公网IP地址。请根据实际需求进行选择。
-   **镜像**：如果用于建站，可以选择公共镜像中的Linux操作系统，例如：CentOS 7.2 64位。

实例创建完成后，您会收到短信和邮件通知，告知您的实例名称、公网IP地址、内网IP地址等信息。您可以使用这些信息登录并管理实例。

很多重要信息都是通过绑定手机的短信接收，并且重要的操作（例如重启、停止等）都需要手机接收验证码，因此请务必保持绑定手机通信畅通。

## 步骤二：部署Web环境 {#section_3as_stl_g30 .section}

本节以安装Nginx为例介绍如何部署Web环境。

软件包中包含的软件及版本为：nginx/1.10.2

**说明：** 这是写文档时参见的软件版本。您下载的版本可能与此不同。

部署Web环境之前，请确认以下信息：

-   您的实例可以连接公网。
-   已安装用于连接Linux实例的工具，例如：SecureCRT。本节将以这个工具为例介绍操作步骤。

完成以下操作，部署Web环境：

1.  打开SecureCRT ，设置登录实例所需的信息。 

    1.  设置连接名称。
    2.  协议选择**SSH**。
    3.  输入主机IP地址和用户。
    4.  单击**确定**保存。
    ![设置登录信息](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156750542912471_zh-CN.png)

2.  输入用户名root和登录密码。 

    ![输入用户名密码](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156750543012472_zh-CN.png)

3.  添加Nginx软件库。 

    ``` {#codeblock_aqb_qow_fzu}
    [root@localhost ~]#rpm -Uvh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
    ```

4.  安装Nginx。 

    ``` {#codeblock_a2n_woi_jqe}
    [root@localhost ~]#yum -y install nginx
    ```

5.  设置Nginx服务器自动启动。 

    ``` {#codeblock_ovp_cuv_qpc}
    [root@localhost ~]# systemctl enable nginx.service
    ```

6.  启动Nginx并查看Nginx服务状态。 

    ``` {#codeblock_dd9_1iv_c5d}
    [root@localhost ~]#systemctl start nginx.service
    [root@localhost ~]#systemctl status nginx.service
    ```

7.  在浏览器中输入IP地址，可以看到默认的Nginx网页。 

    ![nginx网页](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156750543012474_zh-CN.png)


至此，Nginx搭建完成。

## 步骤三：安装Ghost {#section_ab9_fr6_oj6 .section}

完成以下操作，安装Ghost：

1.  更新系统。确保您的服务器系统处于最新状态。 

    ``` {#codeblock_16z_981_r0u}
    [root@localhost ~]# yum -y update
    ```

2.  安装Node.js。 
    1.  安装EPEL。 

        ``` {#codeblock_2zk_25s_dtc}
        [root@localhost ~]# yum install epel-release -y
        ```

    2.  安装Node.js和npm。 

        ``` {#codeblock_6kf_whh_vdf}
        [root@localhost ~]# yum install nodejs npm --enablerepo=epel
        ```

    3.  安装进程管理器以便控制Node.js应用程序。这个进程管理器可以保持应用程序一直处于运行状态。 

        ``` {#codeblock_rbo_756_1yq}
        [root@localhost ~]# npm install pm2 -g
        ```

    4.  安装后运行`node -v`和`npm -v`命令检查Node.js的版本。
3.  安装Ghost。 
    1.  创建Ghost安装目录。 

        ``` {#codeblock_l08_nn2_uau}
        [root@localhost ~]# mkdir -p /var/www/ghost
        ```

    2.  进入Ghost安装目录，下载最新版本的Ghost安装包。 

        ``` {#codeblock_yhi_jgk_vvk}
        [root@localhost ~]# cd /var/www/ghost
        [root@localhost ghost]# curl -L https://ghost.org/zip/ghost-latest.zip -o ghost.zip
        ```

    3.  解压Ghost安装包。 

        ``` {#codeblock_21c_odl_b35}
        [root@localhost ghost]# yum install unzip -y
        [root@localhost ghost]# unzip ghost.zip
        ```

    4.  使用npm安装Ghost。 

        ``` {#codeblock_erl_30h_bsm}
        [root@localhost ghost]# npm install -production
        ```

    5.  安装完成后运行`npm start`命令启动Ghost，检查是否安装成功。
    6.  从示例配置文件config.example.js复制并新建Ghost配置文件config.js。 

        ``` {#codeblock_htr_xmc_07z}
        [root@localhost ghost]# cp config.example.js config.js
        ```

    7.  配置config.js文件中的URL为Ghost博客的域名。 

        ``` {#codeblock_0c7_5un_klg}
        [root@localhost ghost]# vim config.js
        ```

        ![修改域名](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156750543012477_zh-CN.png)

    8.  使用进程管理器配置Ghost处于永久运行状态。 

        ``` {#codeblock_yih_off_8hr}
        [root@localhost ghost]# NODE_ENV=production pm2 start index.js --name "ghost"
        ```

    9.  开启、停止、重启ghost。 

        ``` {#codeblock_1un_5x2_4cc}
        [root@localhost ghost]# pm2 start ghost
        [root@localhost ghost]# pm2 stop ghost
        [root@localhost ghost]# pm2 restart ghost
        ```

4.  安装Nginx。 
    1.  添加Nginx软件库。 

        ``` {#codeblock_qiz_i1x_gtn}
        [root@localhost ~]# rpm -Uvh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
        ```

    2.  安装Nginx。 

        ``` {#codeblock_hq9_6rg_iav}
        [root@localhost ~]# yum -y install nginx
        ```

    3.  设置Nginx服务器自动启动。 

        ``` {#codeblock_rxh_fim_8sz}
        [root@localhost ~]# systemctl enable nginx.service
        ```

    4.  启动Nginx并查看Nginx服务状态。 

        ``` {#codeblock_5i4_clv_le2}
        [root@localhost ~]#systemctl start nginx.service
        [root@localhost ~]#systemctl status nginx.service
        ```

    5.  在浏览器中输入IP地址，可以看到默认的Nginx的网页。 

        ![nginx网页](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156750543012478_zh-CN.png)

5.  配置Nginx作为Ghost的反向代理。 
    1.  进入Nginx配置目录，新建Ghost博客的Nginx配置文件。 

        ``` {#codeblock_kpf_idi_dc8}
        [root@localhost ~]#vim /etc/nginx/conf.d/ghost.conf
        ```

    2.  将以下内容输入到ghost.conf中，把server\_name改成实际的域名。 

        ![修改域名](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156750543012479_zh-CN.png)

    3.  修改默认的配置文件default.conf为default.conf.bak，使Nginx只应用于ghost.conf。 

        ``` {#codeblock_mp4_zec_nhr}
        [root@localhost ~]#mv default.conf default.conf.bak
        ```

    4.  重启Nginx服务。 

        ``` {#codeblock_ydk_fsi_p74}
        [root@localhost conf.d]# systemctl restart nginx.service
        ```

6.  访问Ghost博客。 
    1.  在浏览器输入http://IP或http://域名即可访问Ghost。 

        ![Ghost网页](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156750543012480_zh-CN.png)

        **说明：** 如果访问出现502，请检查是否是防火墙的问题，可以关闭防火墙。

    2.  如果需要对博客进行编辑修改，在浏览器输入http://IP/ghost即可。 

        ![修改博客](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9768/156750543012481_zh-CN.png)


## 步骤四：购买域名 {#section_vhr_y2k_pga .section}

您可以给自己的网站设定一个单独的域名。这样您的用户可以使用易记的域名访问您的网站，而不需要使用复杂的IP地址。

建议登录[阿里云](https://wanwang.aliyun.com/)购买域名。

1.  在[购买域名](https://wanwang.aliyun.com/)页面，搜索您需要的域名，如尚未被注册，则可以购买。选择要购买的域名及期限，然后结算。 
2.  在确认订单的时候，需要选择**您的域名的所有者**。 为方便操作，建议暂时先选择**个人**，以后可以在会员中心进行修改。本文以个人用户为例。
3.  如果这是您首次购买域名，需要创建消息模板。具体操作，请参见[创建消息模板](https://domain.console.aliyun.com/#/infotemplate)。 
4.  填写注册信息。请务必填写真实信息。 
5.  填写完成后需要进行实名认证。上传个人身份证正面扫描件。审核一般需要3~5个工作日。

## 步骤五：备案 {#section_6ph_sb6_rb4 .section}

对于域名指向中国境内服务器的网站，必须进行网站备案。在域名获得备案号之前，网站是无法开通使用的。

阿里云有代备案系统，方便您进行备案。备案免费，审核时间一般为20天左右，请您耐心等待。

1.  登录[备案管理控制台](https://bsn.console.aliyun.com/#/bsnApply/ecs)。
2.  在左侧导航栏，单击**备案管理** \> **备案服务号申请**，然后单击**申请**，为购买的ECS实例申请备案服务号，此服务号在备案时会用到。 
3.  在弹出的提示信息对话框中，单击**确定**。
4.  申请成功后，页面自动跳转到备案服务号管理页面，显示与ECS实例绑定的备案号。然后单击**备案专区**，了解备案相关信息。 
5.  首次备案的用户，需要在[ICP代备案管理系统](https://beian.gein.cn/account/login.htm)注册一个备案账号。 

    **说明：** 该备案账号不是阿里云账号，而是申请备案专用的账号。


## 步骤六：配置域名解析 {#section_b35_s43_byu .section}

您需要在阿里云万网上配置域名解析之后，用户才能通过域名访问您的网站。

1.  登录[域名管理控制台](https://netcn.console.aliyun.com/core/domain/list)。
2.  在左侧导航栏，单击**域名** \> **域名列表**。在域名列表中找到要解析的域名，在**操作**列 ，单击**解析**。 
3.  单击**新手引导设置**。
4.  在文本框内输入您的Linux实例的公网IP地址，单击**提交**。 

