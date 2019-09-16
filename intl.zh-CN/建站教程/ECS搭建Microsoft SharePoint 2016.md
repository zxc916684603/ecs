# ECS搭建Microsoft SharePoint 2016 {#concept_pmz_5gt_2fb .task}

本教程介绍如何在阿里云ECS上搭建Microsoft SharePoint 2016。

使用本教程进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.alibabacloud.com/register/intl_register.htm)。

Microsoft SharePoint是Microsoft SharePoint Portal Server的简称。SharePoint Portal Server是一个门户站点，使得企业能够开发出智能的门户站点，这个站点能够无缝连接到用户、团队和知识，使人们能够更好地利用业务流程中的相关信息，更有效地开展工作。SharePoint Portal Server提供了一个企业的业务解决方案，它利用了企业应用程序集成功能，以及灵活的部署选项和管理工具，将来自不同系统的信息集成到一个解决方案中。

本教程适用于熟悉ECS、熟悉Windows Server系统的用户。

本教程在示例步骤中使用如下软件版本：

-   操作系统：Windows Server 2012 R2 DataCenter
-   数据库：SQL Server 2014 SP1

本教程示例步骤中使用的云服务器ECS硬件配置如下：

-   vCPU：4核
-   内存：8G

## 操作步骤 {#section_bi1_x2j_v96 .section}

在阿里云ECS上搭建Microsoft SharePoint 2016的操作步骤如下：

1.  [步骤一：添加AD、DHCP、DNS、IIS服务](#section_o8w_kwm_aao)
2.  [步骤二：安装数据库SQL Server 2014](#section_o9w_kwm_bho)
3.  [步骤三：安装SharePoint 2016](#section_o1w_kwm_xxo)
4.  [步骤四：配置SharePoint 2016](#section_o2w_kwm_cco)

## 步骤一：添加AD、DHCP、DNS、IIS服务 {#section_o8w_kwm_aao .section}

完成以下操作，添加AD、DHCP、DNS、IIS服务：

1.  购买一台云服务器ECS。具体操作，请参见[使用向导创建实例](../intl.zh-CN/实例/创建实例/使用向导创建实例.md#)。
2.  关闭IE增强的安全设置。 

    ![关闭IE安全设置](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658312311_zh-CN.png)

3.  添加新的角色和功能（包括DNS、DHCP、IIS和Net Framework3.5）。 
    1.  单击**Add roles and features**。 

        ![添加角色功能](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658312312_zh-CN.png)

    2.  添加AD、DHCP、DNS服务。选中**Active Directory Domain Services**、**DHCP Server**和**DNS Server**复选框，然后单击**Next**。 

        ![添加AD、DHCP和DNS](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658312313_zh-CN.png)

    3.  添加IIS服务。选中**Web Server IIS**复选框，然后单击**Next**。 

        ![添加IIS](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658412314_zh-CN.png)

    4.  在**Features**选项卡中，选中**.Net Framework 3.5 Features**。 

        ![添加.Net](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658412316_zh-CN.png)

    5.  单击**Next**，直至完成。
4.  安装完成后，配置AD服务。单击**Add a new forest**，然后在**Root domain name**文本框填写域名，创建一个新的域环境。 

    ![配置AD域名](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658412317_zh-CN.png)

5.  设置密码，然后单击**Next**直至完成。 

    ![输入密码](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658412318_zh-CN.png)

6.  单击**Complete DHCP configuration**，配置DHCP功能。 

    ![配置DHCP](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658412321_zh-CN.png)

    1.  查看DHCP配置的描述，然后单击**Next**。
    2.  保持默认配置，单击**Commit**即可完成安装。 

        ![保持默认配置](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658412322_zh-CN.png)


## 步骤二：安装数据库SQL Server 2014 {#section_o9w_kwm_bho .section}

完成以下步骤，安装数据库SQL Server 2014：

1.  安装SQL Server 2014 SP1，进入安装选项卡，单击第一个选项。 

    ![单击第一个选项卡](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658512323_zh-CN.png)

2.  输入产品秘钥，单击**Next**。
3.  接受License，单击**Next**。
4.  完成安装检查，单击**Next**。
5.  选择默认选项，单击**Next**。 

    ![保持默认配置](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658512324_zh-CN.png)

6.  单击**Select All**选中全部功能，然后单击**Next**。 

    ![select all](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658512325_zh-CN.png)

7.  配置数据实例，单击**Default instance**，使用默认实例ID。 

    ![配置数据实例](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658512326_zh-CN.png)

8.  配置**SQL Server Database Engine**服务和**SQL Server Analysis Services**服务的账号和密码。 

    ![配置服务账号和密码](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658512328_zh-CN.png)

9.  单击**Add Current User**添加当前账号，然后单击**Next**。 

    ![添加当前账号](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658512329_zh-CN.png)

10. 单击**Add Current User**继续添加当前账号，然后单击**Next**。 

    ![继续添加当前账号](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658612330_zh-CN.png)

11. 继续单击**Next**，直至安装完成。

## 步骤三：安装SharePoint 2016 {#section_o1w_kwm_xxo .section}

完成以下操作，安装SharePoint 2016：

1.  安装SharePoint 2016准备工具，打开镜像文件，打开准备工具的可执行文件。 

    ![打开安装工具](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862658612331_zh-CN.png)

2.  在准备工具的向导窗口，单击**Next**。 
3.  接受许可条款，准备安装必备组件，直至准备工具安装完成。
4.  打开目录下的Setup.exe，输入产品密钥，然后接受许可条款，单击**继续**。 
5.  选择安装目录（本示例中是保持默认设置，您可以根据实际情况选择相应安装目录），然后单击**立即安装**。 
6.  安装完成，选中**立即运行SharePoint产品配置向导**并关闭安装向导。

## 步骤四：配置SharePoint 2016 {#section_o2w_kwm_cco .section}

完成以下操作，配置SharePoint 2016：

1.  单击**创建新的服务器场**。 
2.  配置数据库设置和指定数据库访问账户信息。由于数据库安装在本机，所以数据库服务器直接填写本机IP。 
3.  选择服务器的角色。 
4.  选中**指定端口号**复选框并修改端口号为10000，您可以根据实际情况修改。 
5.  查看配置，并单击**下一步**。 配置成功后，可以打开SharePoint的管理中心。

