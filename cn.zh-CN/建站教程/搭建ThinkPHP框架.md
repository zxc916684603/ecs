# 搭建ThinkPHP框架 {#concept_52954_zh .task}

ThinkPHP是一款免费、开源、快速、简单、面向对象的轻量级PHP开发框架，遵循Apache2开源协议发布，是为了敏捷Web应用开发和简化企业应用开发而诞生的。本篇教程介绍如何使用云市场镜像快速搭建ThinkPHP框架。

使用本教程进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm?)。

本教程适用于正在学习PHP或者已基于ThinkPHP框架进行研发的开发人员。

## 操作步骤 {#section_4sp_3lg_ngj .section}

使用云市场镜像快速搭建ThinkPHP框架的操作步骤如下：

1.  [步骤一：购买ThinkPHP框架镜像](#section_gno_olp_zdk)
2.  [步骤二：上传应用程序](#section_yyy_uy3_t68)
3.  [步骤三：切换PHP脚本适应程序](#section_6r1_7kt_txz)
4.  [步骤四：开启pathinfo](#section_l6p_2fu_5oi)
5.  [步骤五：绑定域名](#section_6ng_7ds_rcp)

## 步骤一：购买ThinkPHP框架镜像 {#section_gno_olp_zdk .section}

完成以下操作，购买ThinkPHP框架镜像：

1.  单击[ThinkPHP框架（含智慧云虚机面板）](https://market.aliyun.com/products/53616009/cmjj017339.html)进入镜像详情页。
2.  单击**立即购买**，按提示步骤根据您的实际业务需求购买ECS实例。
3.  登录[ECS管理控制台](https://ecs.console.aliyun.com)。
4.  在左侧导航栏，单击**实例与镜像** \> **实例**。
5.  在顶部状态栏处，选择地域。
6.  在实例列表页面，找到目标实例，在**IP 地址**列获取该实例的公网IP地址。
7.  在浏览器地址栏中输入公网IP地址，屏幕上会显示提示页面。
8.  在提示页面，单击**获取权限**，下载权限文档zhcloud-readme.doc。 

    ![安装thinkPHP框架](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9781/156862650712159_zh-CN.png)

    权限文档中包含了智慧云虚机面板权限（host）、FTP权限和MySQL数据库权限，请妥善保存。

    ![权限](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9781/156862650712160_zh-CN.png)


## 步骤二：上传应用程序 {#section_yyy_uy3_t68 .section}

如果您已经通过ThinkPHP框架完成了自己的应用程序，可以通过FTP上传您的程序。操作步骤如下：

1.  下载FTP工具。本篇教程以FileZilla FTP为例。下载地址为[https://www.filezilla.cn/download/client](https://www.filezilla.cn/download/client)。
2.  下载FileZilla后，双击filezilla.exe，开始按软件提示安装FileZilla FTP。
3.  启动FileZilla FTP，在**主机**、**用户名**和**密码**处分别输入FTP IP地址、FTP账号和FTP密码。相关信息，请参见权限文档zhcloud-readme.doc。 

    ![启动FileZilla](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9781/156862650712161_zh-CN.png)

4.  单击**快速连接**，开始连接FTP。
5.  将您已经写好的应用程序拉到右边区域即可实现上传。

## 步骤三：切换PHP脚本适应程序 {#section_6r1_7kt_txz .section}

由于PHP的版本不同所支持的PHP函数也不尽相同。若您的程序对PHP版本有严格要求，您可以通过**脚本切换**来切换到您需要的PHP版本。若没有严格要求，可跳过此步骤。

1.  登录[智慧云虚机面板](http://zhy.yjcom.com/) 。登录信息，请参见权限文档zhcloud-readme.doc。 

    -   `host url`：**智慧云虚机面板**的登录地址。
    -   `host account`：**智慧云虚机面板**的登录账号。
    -   `host password`：**智慧云虚机面板**的登录密码。
    ![智慧云虚机面板](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9781/156862650712162_zh-CN.png)

    登录成功后，如下图所示。

    ![登录成功](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9781/156862650712163_zh-CN.png)

2.  单击**脚本切换** ，选择您需要的PHP版本，单击**确定** 。 

    ![选择PHP版本](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9781/156862650712165_zh-CN.png)


## 步骤四：开启pathinfo {#section_l6p_2fu_5oi .section}

使用ThinkPHP框架写的程序一般会用到pathinfo。若您需要开启pathinfo，请按如下步骤操作：

1.  登录[智慧云虚机面板](http://zhy.yjcom.com/)。
2.  单击**PATH\_INFO**，选择您的站点，单击**开启**按钮。 

    ![开启pathinfo](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9781/156862650712166_zh-CN.png)


## 步骤五：绑定域名 {#section_6ng_7ds_rcp .section}

如果您的实例公网IP地址已经完成了域名备案，您可以在智慧云虚机面板上绑定您的域名。

1.  登录[智慧云虚机面板](http://zhy.yjcom.com/)。
2.  单击**域名绑定**，输入您的域名即可绑定。 

    若您想禁止IP访问，删除含有IP地址的这条记录即可。

    ![绑定域名](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9781/156862650712167_zh-CN.png)


## 常见问题：如何解决301重定向问题？ {#section_ugz_lyl_2fb .section}

完成以下操作，在智慧云虚机面板写入301重定向的Nginx规则：

1.  登录[智慧云虚机面板](http://zhy.yjcom.com/)。
2.  单击**自定义伪静态** \> **自定义**，写入301重定向的Nginx规则，单击**保存**。 

    ![自定义伪静态](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9781/156862650812168_zh-CN.png)

    下面以域名`yjcom.com`为例写入301重定向的Nginx规则。

    -   方法 A：不使用`www.yjcom.com`域名访问网站时都301重定向到`www.yjcom.com`。

        ``` {#codeblock_efe_280_gwa}
        if ($host != ‘www.yjcom.com’ ) {
        rewrite ^/(.*)$ http://www.yjcom.com/$1 permanent;
        }
        ```

    -   方法 B：使用`yjcom.com`域名访问网站时才301重定向到`www.yjcom.com`。

        ``` {#codeblock_9dv_qka_f5w}
        if ($host = ‘yjcom.com’ ) {
        rewrite ^/(.*)$ http://www.yjcom.com/$1 permanent;
        }
        ```

        **说明：** 实际使用时，将以上代码中的域名替换为您自己的域名。


