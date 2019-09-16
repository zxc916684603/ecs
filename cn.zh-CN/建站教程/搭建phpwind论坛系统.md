# 搭建phpwind论坛系统 {#concept_53855_zh .task}

phpwind是采用PHP和MySQL方式运行的开源社区程序。phpwind先进版（v9.0.1）注重轻社区、高效、易开发。本篇教程介绍如何使用phpwind先进版快速搭建phpwind论坛系统。

-   使用本教程进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm?)。
-   对中国大陆提供服务的网站必须拥有已经备案的域名。如果没有备案，购买ECS实例后，请到[阿里云备案中心](https://beian.aliyun.com./)备案。

## 操作步骤 {#section_577_4bt_uj4 .section}

完成以下步骤，使用云市场镜像快速搭建phpwind论坛系统：

1.  购买**PHPWind论坛系统（含智慧云虚机面板）**镜像和ECS实例。 
    1.  单击[PHPWind论坛系统（含智慧云虚机面板）](https://market.aliyun.com/products/53616009/cmjj017608.html) 进入镜像详情页。
    2.  单击**立即购买**。
    3.  在自定义购买页面，**镜像**区域已自动设置为您购买的镜像。根据页面提示，完成其他配置项并购买ECS实例。其中，**网络类型**选择**专有网络**。更多配置详情，请参见[使用向导创建实例](../cn.zh-CN/实例/创建实例/使用向导创建实例.md#)。
2.  登录phpwind论坛。 

    1.  登录[ECS管理控制台](https://ecs.console.aliyun.com/#/home)。
    2.  在左侧导航栏，单击**实例与镜像** \> **实例**，进入ECS实例列表页面。
    3.  选择已购ECS实例所在的地域。
    4.  找到已购ECS实例，在**IP地址**列获取该实例的公网IP地址。
    5.  在浏览器地址栏中，输入公网IP地址。
    6.  在提示页面上，单击**获取权限**，下载权限文档zhcloud-readme.doc。 

        ![下载权限文档](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9786/156862653612205_zh-CN.png)

        权限文档中包含了智慧云虚机面板权限（host）、FTP 权限（PHPWind ftp）、 MySQL数据库权限（PHPWind database）和phpwind后台管理权限（PHPWind admin）。

        ![权限](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9786/156862653612206_zh-CN.png)

    7.  在浏览器地址栏中，输入`http://实例公网IP地址/admin.php`，进入phpwind的登录页面。
    8.  输入权限文档zhcloud-readme.doc中获取的phpwind后台管理用户名和密码，单击**登录**。 

        ![phpwind](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9786/156862653612207_zh-CN.png)

    登录phpwind后台，您就可以管理phpwind论坛了。

    ![登录phpwind后台](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9786/156862653612208_zh-CN.png)

3.  绑定域名。 
    1.  登录[智慧云虚机面板](http://zhy.yjcom.com/) 。登录信息，请参见权限文档zhcloud-readme.doc。 host相关登录信息表示的含义如下：

        -   `host url`：智慧云虚机面板的登录地址。
        -   `host account` ：智慧云虚机面板的登录账号。
        -   `host password` ：智慧云虚机面板的登录密码。
        ![登录](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9786/156862653612209_zh-CN.png)

        登录成功后，如下图所示。

        ![登录成功](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9786/156862653612210_zh-CN.png)

    2.  单击**域名绑定**，输入您的域名即可绑定。如需禁止IP访问，删除含有IP地址的这条记录即可。 

        ![域名绑定](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9786/156862653612211_zh-CN.png)

4.  获取phpwind商业授权。获取授权后，您可以合理合法地使用phpwind论坛程序。

## 常见问题 {#section_nhr_1rk_752 .section}

-   问题一：如何解决301重定向问题？

    解决方法：

    1.  登录[智慧云虚机面板](http://zhy.yjcom.com/)。
    2.  找到**自定义伪静态** \> **自定义**，写入301重定向的Nginx规则，单击**保存**。

        ![自定义伪静态](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9786/156862653612232_zh-CN.png)

        下面以域名`yjcom.com`为例，介绍如何写入301重定向Nginx规则。

        -   方法A：不使用`www.yjcom.com`域名访问网站时，都301重定向到`www.yjcom.com`。

            ``` {#codeblock_loo_byy_0zg}
            if ($host != ‘www.yjcom.com’ ) {
            rewrite ^/(.*)$ http://www.yjcom.com/$1 permanent;
            }
            ```

        -   方法B：使用`yjcom.com`域名访问网站时，才301重定向到`www.yjcom.com`。

            ``` {#codeblock_319_kym_lh6}
            if ($host = ‘yjcom.com’ ) {
            rewrite ^/(.*)$ http://www.yjcom.com/$1 permanent;
            }
            ```

            **说明：** 实际使用时，将以上代码中的域名替换为您自己的域名。

-   问题二：使用智慧云虚机面板需要对公网开放哪些端口？

    解决方法：在ECS实例安全组入方向添加规则并放行端口21/21、80/80、3306/3306、30000/30010、8081/8081和1777/1777。具体操作，请参见[添加安全组规则](../cn.zh-CN/安全/安全组/添加安全组规则.md#)。

    更多开源软件尽在云市场：[https://market.aliyun.com/software](https://market.aliyun.com/software)。


