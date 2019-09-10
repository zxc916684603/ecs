# 搭建Moodle课程管理系统 {#concept_htd_qfb_ffb .task}

Moodle是一个课程管理系统，采用PHP加MySQL方式运行的自由开源软件。使用Moodle为学生建立网上动态网站，可以根据需要随时调整界面、增减内容。本教程介绍如何使用云市场镜像快速搭建Moodle课程管理系统。

-   使用本教程进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm?)。
-   如需用户通过域名访问您的站点，请确保您已备案域名。如果域名没有备案，购买ECS实例后，请到[阿里云备案中心](https://beian.aliyun.com/)备案 。
-   已在安全组中添加下列安全组规则。具体操作，请参见[添加安全组规则](../cn.zh-CN/安全/安全组/添加安全组规则.md#)。

    |配置项|使用SSH远程连接ECS实例|使用HTTP访问Web服务器|使用FTP上传或下载文件|使用MySQL|
    |---|--------------|--------------|------------|-------|
    |网卡类型|公网|公网|公网|公网|
    |规则方向|入方向|入方向|入方向|入方向|
    |授权策略|允许|允许|允许|允许|
    |协议类型|SSH（22）|HTTP（80）|自定义 TCP|自定义 TCP|
    |端口范围|22/22|80/80|21/21|3306/3306|
    |授权类型|地址段访问|地址段访问|地址段访问|地址段访问|
    |授权对象|0.0.0.0/0|0.0.0.0/0|0.0.0.0/0|0.0.0.0/0|
    |优先级|1|1|1|1|


1.  使用云市场镜像创建ECS实例。 
    1.  单击[moodle 网络教学平台（Centos 7.0 64位）](https://market.aliyun.com/products/56014009/cmjj012770.html)进入镜像详情页。
    2.  单击**立即购买**。
    3.  在自定义购买页面，**镜像**区域已自动设置为您购买的镜像。按页面提示，完成其他配置项并购买ECS实例。 需注意以下配置：
        -   **计费方式**：如果您的站点需要备案，应选择**包年包月**。
        -   **公网带宽**：选中**分配公网IPv4地址**。
        -   **安全组**：选择前提条件中配置的安全组。
        -   其他配置您可以按需选择。配置详情，请参见[使用向导创建实例](../cn.zh-CN/实例/创建实例/使用向导创建实例.md#)。
2.  获取ECS实例的公网IP地址。 
    1.  登录[ECS管理控制台](https://ecs.console.aliyun.com)。
    2.  在左侧导航栏，单击**实例与镜像** \> **实例**。
    3.  在顶部状态栏处，选择目标ECS实例所在地域。
    4.  找到目标ECS实例，在**IP 地址**列获取该实例的公网IP地址。
3.  获取随机生成的MySQL数据库权限及FTP权限。 
    1.  连接已购ECS实例。具体操作，请参见[使用用户名密码验证连接Linux实例](../cn.zh-CN/实例/连接实例/连接Linux实例/使用用户名密码验证连接Linux实例.md#)。
    2.  运行命令`cat default.pass`查看并记录随机生成的MySQL数据库权限及FTP权限。 

        **说明：** 请妥善记录MySQL数据库权限及FTP权限，以便后续步骤使用。

        ![get_db_user](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9785/156809221512544_zh-CN.png)

4.  在浏览器地址栏里，输入`http://ECS实例公网IP地址/install.php`并回车。
5.  选择您想要的语言，单击**向后**。本示例中，选择**简体中文**。 

    ![moodle_1](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9785/156809221512545_zh-CN.png)

6.  在确认路径页面，所有默认目录保持不变。单击**向后**。 

    ![moodle_2](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9785/156809221512546_zh-CN.png)

7.  在选择数据库驱动页面，**类型**使用默认值。单击**向后**。 

    ![moodle_3](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9785/156809221512547_zh-CN.png)

8.  配置数据库信息，单击**向后**。 
    -   **数据库主机**：只能输入127.0.0.1。
    -   **数据库名**、**数据用户名**和**数据库密码**：输入第3步中记录的MySQL数据库权限信息。
    -   **数据库服务端口**：输入3306。

        ![configure_db](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9785/156809221512548_zh-CN.png)

9.  阅读并确认了解版权声明。单击**继续**。
10. 下图中显示的是安装Moodle需要的一些组件，都已经部署完成。单击**继续**。 

    ![moodle_dependent_components](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9785/156809221512549_zh-CN.png)

11. 当安装页面底部出现**继续**时，说明已经完成安装。单击**继续**。 

    ![installation_completed](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9785/156809221612550_zh-CN.png)

12. 按要求设置Moodle系统的登录信息后，单击**保存更改**。 

    ![configure_login1](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9785/156809221612551_zh-CN.png)

    ![configure_login2](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9785/156809221612552_zh-CN.png)

    安装完成，自动进入管理后台首页。

    ![user_management](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9785/156809221612553_zh-CN.png)

    **说明：** 数据库的管理地址为`http://ECS实例公网IP地址/phpmyadmin/`。

13. 用户可以使用公网IP地址访问您的站点。如果您希望用户使用域名访问您的站点，应先将域名解析到公网IP地址。您可以按以下步骤在服务器里绑定域名。 
    1.  远程连接ECS实例。连接方式请参见[连接方式导航](../cn.zh-CN/实例/连接实例/连接方式导航.md#)。
    2.  运行`vim /etc/httpd/conf/httpd.conf`命令打开配置文件。
    3.  按i键进入编辑模式。
    4.  添加Servername命令。 将`localhost`改为`www.yourdomain.com`即可。其中，`www.yourdomain.com`必须替换为您自己的域名。

        ![moodle_servername](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9785/156809221612554_zh-CN.png)

    5.  按Esc键退出编辑模式，然后输入:wq并回车以保存并关闭文件。

