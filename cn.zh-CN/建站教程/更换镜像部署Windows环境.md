# 更换镜像部署Windows环境 {#concept_25427_zh .task}

使用集成了操作系统和应用程序的镜像，可以快速在ECS实例上部署Windows应用环境。本文介绍通过更换ECS实例的镜像来部署Windows环境的操作步骤。

使用本教程进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm?)。

您可以根据业务需要，手动部署或使用阿里云[云市场](http://market.aliyun.com/)镜像部署ECS实例的应用环境。云市场镜像集成了操作系统和应用程序，推荐您使用云市场镜像快速部署Windows应用环境。

您可以直接选择包含Windows应用环境的云市场镜像创建实例（具体步骤请参见[创建实例](../cn.zh-CN/个人版快速入门/创建ECS实例.md#)），也可以通过更换系统盘的方式，将已购ECS实例的操作系统更换为云市场镜像。本教程的操作步骤适用于已创建ECS实例，但希望通过更换云市场镜像来快速部署Windows应用环境的场景。教程中，仅介绍使用云市场镜像部署的通用操作步骤。镜像软件安装包中通常包含了操作指南，请参见镜像操作指南进行具体的安装和配置。

**说明：** 

-   云服务器ECS不支持虚拟化软件（如KVM、Xen、VMware等）的安装部署。
-   更换系统盘时，ECS实例数据盘的数据不会受到影响。因此建议您将系统盘的个人数据备份到数据盘中，或采用其他方式进行备份。
-   更换系统盘后，ECS实例系统盘的数据会全部被清空，服务器自动备份的快照也可能会被删除（快照是否被删除，取决于您的设置，请参见[自动快照随云盘释放](../cn.zh-CN/隐藏/Alibaba Cloud ECS/快照/设置自动快照随云盘释放.md#)）。请务必做好数据备份工作。
-   更换系统盘后，ECS实例的IP地址不会改变。

1.  登录[ECS管理控制台](https://ecs.console.aliyun.com)。
2.  在左侧导航栏，单击**实例与镜像** \> **实例**。
3.  在实例列表页面，选中目标实例，单击实例ID或**操作**列的**管理**。![找到实例](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9762/156862646221022_zh-CN.png)


4.  停止目标实例。 

    **说明：** 停止实例会影响您的业务，请谨慎操作。

    1.  在实例详情页面，单击**停止**。![停止实例](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9762/156862646214390_zh-CN.png)


    2.  在提醒对话框，单击**确定**。![提醒对话框](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9762/156862646214393_zh-CN.png)


    3.  在停止实例对话框，选择**停止方式**和**停止模式**，然后单击**确定**。 

        **说明：** 如果您停止实例是为了更换系统盘、重新初始化磁盘、更改实例规格、修改私网IP等操作，建议您选中**停止后仍旧保留实例并继续收费**选项，避免实例启动失败。

        ![停止实例](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9762/156862646214395_zh-CN.png)

5.  更换ECS实例系统盘。 
    1.  在实例详情页面的**配置信息**区域，单击**更多** \> **更换系统盘**。![更换系统盘](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9762/156862646214397_zh-CN.png)


    2.  在更换系统盘对话框，单击**确定，更换系统盘**。![更换系统盘须知](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9762/156862646214398_zh-CN.png)


    3.  **镜像类型**选择**镜像市场**，然后单击**从镜像市场选择（含操作系统）**。![选择镜像](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9762/156862646221021_zh-CN.png)


    4.  在左侧导航栏，选择镜像分类，或者在搜索栏中输入您想使用的镜像，然后单击**搜索**。选中目标镜像后，单击**使用**。![选择目标镜像](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9762/156862646221036_zh-CN.png)


    5.  设置ECS实例的登录密码。在**登录密码**文本框中输入密码，并在**确认密码**文本框中再次输入密码。![设置登录密码](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9762/156862646221042_zh-CN.png)


    6.  在更换系统盘页面右下角， 选中 *云服务器ECS服务条款* 和 *镜像商品使用条款* 并单击**确定更换**。![确定更换](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9762/156862646221043_zh-CN.png)



出现系统盘更换成功对话框时，表明您已成功使用镜像市场的镜像更换ECS实例的操作系统。单击**返回实例列表**返回实例列表页面。启动并登录ECS实例后，即可使用实例的应用环境。

![系统盘更换成功](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9762/156862646221046_zh-CN.png)

