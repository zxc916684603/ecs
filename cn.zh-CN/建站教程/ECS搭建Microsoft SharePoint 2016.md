# ECS搭建Microsoft SharePoint 2016 {#concept_pmz_5gt_2fb .concept}

Microsoft SharePoint是Microsoft SharePoint Portal Server的简称。SharePoint Portal Server是一个门户站点，使得企业能够开发出智能的门户站点，这个站点能够无缝连接到用户、团队和知识，因此人们能够更好地利用业务流程中的相关信息，更有效地开展工作。SharePoint Portal Server 提供了一个企业的业务解决方案，它利用了企业应用程序集成功能，以及灵活的部署选项和管理工具，将来自不同系统的信息集成到一个解决方案中。本文主要说明如何在阿里云ECS上搭建Microsoft SharePoint 2016。使用的操作系统为Windows Server 2012 R2 DataCenter。

## 适用对象 {#section_wqw_wgt_2fb .section}

适用于熟悉ECS，熟悉Windows Server系统的用户。

## 基本流程 {#section_rh5_xgt_2fb .section}

1.  添加AD、DHCP、DNS、IIS服务
2.  安装数据库SQL Server 2014
3.  安装SharePoint 2016
4.  配置SharePoint 2016

**步骤一：添加AD、DHCP、DNS、IIS服务**

1.  采购一台4核8G的云服务器，本实验环境操作系统版本为 Windows Server 2012 R2 数据中心版64位。
2.  关闭IE增强的安全设置。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566312311_zh-CN.png)

3.  添加新的角色和功能（包括DNS、DHCP、IIS、Net Framework3.5），单击 **Add roles and features**，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566312312_zh-CN.png)

    添加AD、DHCP、DNS服务，在这里勾选就可以，然后单击 **下一步**，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566312313_zh-CN.png)

    同时勾选IIS（Web Server IIS）服务，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566312314_zh-CN.png)

4.  在Features选项卡中，勾选 **Net Framework 3.5** 功能，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566312316_zh-CN.png)

5.  单击 **下一步**，直至完成。
6.  安装完成，配置一下AD服务，点击红框里面的链接，因为没有已经存在的域环境，填写 **Root domain name**，创建一个新的forest如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566312317_zh-CN.png)

7.  填写密码，完成后单击 **下一步** 直至完成。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566412318_zh-CN.png)

8.  配置DHCP功能，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566412321_zh-CN.png)

    查看DHCP配置的描述，单击 **下一步**，选择默认配置，单击 **Commit** 即可完成安装，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566412322_zh-CN.png)


**步骤二：安装SQL Server**

1.  安装SQL Server 2014 with sp1，进入安装选项卡，单击第一个选项，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566412323_zh-CN.png)

2.  输入产品秘钥，单击 **下一步**。
3.  接受License，单击 **下一步**。
4.  完成安装检查，单击 **下一步**。
5.  选择默认选项，单击 **下一步**，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566412324_zh-CN.png)

6.  勾选全部功能，单击 **下一步**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566412325_zh-CN.png)

7.  配置数据实例，选择默认，在SharePoint配置的时候，连接配置实例即可。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566412326_zh-CN.png)

8.  配置SQL Server Database Engine服务和SQL Server Analysis Services服务账号和密码。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566412328_zh-CN.png)

9.  添加管理员账号，单击 **下一步**，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566512329_zh-CN.png)

10. 继续添加当前账号，单击 **下一步**，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566512330_zh-CN.png)

    接着单击 **下一步**，直至安装完成。


**步骤三：安装SharePoint 2016**

1.  安装SharePoint 2016 准备工具，打开镜像文件，打开准备工具的可执行文件，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566512331_zh-CN.png)

2.  准备工具的向导，需要安装以下一系列软件：

    -   应用程序服务器角色、Web 服务器\(IIS\)角色
    -   Microsoft SQL Server 2012 Native Client
    -   Microsoft ODBC Driver 11 for SQL Server
    -   Microsoft Sync Framework Runtime v1.0 SP1 \(x64\)
    -   Windows Server AppFabric
    -   Microsoft Identity Extensions
    -   Microsoft Information Protection and Control Client 2.1
    -   Microsoft WCF Data Services 5.6
    -   Microsoft .NET Framework 4.6
    -   Microsoft AppFabric 1.1 for Windows Server 累积更新包 1 \(KB2671763\)
    -   Visual Studio 2012 Visual C++ 的可再发行组件包
    -   Visual C++ Visual Studio 2015 的可再发行程序包
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566512332_zh-CN.png)

3.  接受License，准备安装必备组件，直至安装完毕准备工具，可以安装SharePoint server 2016，（打开目录下的Setup.exe）如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566512333_zh-CN.png)

4.  180天试用版Key：NQGJR-63HC8-XCRQH-MYVCH-3J3QR4、接受许可条款，选择安转目录（此处是默认设置，您可以根据实际情况选择相应数据盘），然后单击 **立即安装** 即可，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566512334_zh-CN.png)

5.  安装完成，提示我们关闭安装向导的同时，勾选立即运行SharePoint产品配置向导。

**步骤四：配置SharePoint 2016**

1.  创建一个新的服务器场，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566512335_zh-CN.png)

2.  配置数据库设置，由于数据库在本机，所以数据库服务器直接填写本机。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566512336_zh-CN.png)

3.  填写服务器场的密码，完成后选择服务器的角色，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566512337_zh-CN.png)

4.  修改管理中心默认的端口号4466为10000，您可以根据实际情况修改。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566512338_zh-CN.png)

5.  查看配置，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566512339_zh-CN.png)

6.  配置成功后，可以打开SharePoint的管理中心，如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/154817566612340_zh-CN.png)


