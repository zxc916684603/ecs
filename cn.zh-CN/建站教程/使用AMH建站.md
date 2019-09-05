# 使用AMH建站 {#concept_qnl_rzs_2fb .concept}

AMH是一套通过Web控制和管理Linux服务器以及虚拟主机的管理系统。您可以使用云服务器ECS安装AMH来搭建PHP网站。本篇教程分别介绍如何部署AMH并快速搭建PHP网站。

## 前提条件 {#section_olp_2bt_2fb .section}

-   使用本教程进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm?)。

-   若使用手动方式部署AMH，请确保您已创建ECS实例。具体步骤，请参见[创建ECS实例](../cn.zh-CN/个人版快速入门/创建ECS实例.md#)。

## 基本流程 {#section_6pz_9tx_x0w .section}

使用AMH快速建站的基本流程如下：

1.  [使用镜像部署AMH（云市场镜像）](#section_ug5_fbt_2fb)或[手动部署AMH（公共镜像）](#section_g4n_cct_2fb)
2.  [使用AMH搭建PHP网站](#section_v3j_xct_2fb)

## 镜像部署AMH {#section_ug5_fbt_2fb .section}

镜像部署AMH适用于尚未购买ECS实例的用户，操作步骤如下：

1.  单击[PHP运行环境（AMH 4.2面板 CentOS 6.5）](https://market.aliyun.com/products/53398003/cmjj009429.html?spm=5176.730005.0.0.vdYTVv)进入镜像详情页。
2.  单击**立即购买**。

    ![AMH镜像](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314012278_zh-CN.png)

3.  在自定义购买页面，**镜像**区域已自动设置为您选购的镜像。根据页面提示，完成ECS实例的其他配置后，单击**确认订单**并完成支付。配置详情，请参见[使用向导创建实例](../cn.zh-CN/实例/创建实例/使用向导创建实例.md#)。

    ![购买ECS实例](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314055524_zh-CN.png)


## 手动部署AMH {#section_g4n_cct_2fb .section}

AMH 4.2为一套独立的LNMP/Nginx虚拟主机面板，请使用纯净系统安装。手动部署AMH的操作步骤如下：

1.  远程连接ECS实例。连接方式请参见[连接方式导航](../cn.zh-CN/实例/连接实例/连接方式导航.md#)。
2.  下载并运行AMH安装脚本。

    ``` {#codeblock_skv_12y_uru}
    wget http://amh.sh/file/AMH/4.2/amh.sh && chmod 775 amh.sh && ./amh.sh 2>&1 | tee amh.log
    ```

    ![AMH-WGET](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314055543_zh-CN.png)

3.  根据界面提示输入1~3选项（1代表安装AMH，2代表卸载AMH，3代表退出不做操作）。输入1并回车，接着输入MySQL和AMH的登录密码后进入安装流程。最后看到安装成功提示，说明系统已安装完成。

    ![安装AMH](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314012281_zh-CN.png)

    成功安装后，如有必要请删除日志文件amh.log。若安装失败需协助安装，请将错误日志反馈给我们。

    **说明：** 安装成功需花费1小时左右，请您耐心等待。


## 使用AMH搭建PHP网站 {#section_v3j_xct_2fb .section}

完成以下步骤，使用AMH搭建PHP网站：

1.  登录AMH管理页面。
    1.  在浏览器地址栏，输入`ECS实例公网IP地址:8888`并回车，进入AMH后台登录界面。

        ![登录界面](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314012283_zh-CN.png)

    2.  输入用户名和密码，单击**登录**。如果您使用了镜像部署AMH，则默认帐号为`admin`、密码为`cldera.com`。

        登录成功后，您可以看到很多功能，如下图所示。

        ![登录成功](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314012284_zh-CN.png)

2.  开始创建空间。
    1.  在顶部导航栏，单击**虚拟主机**。

        ![虚拟主机](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314012285_zh-CN.png)

    2.  设置**主标识域名**和**绑定域名**，其他配置使用默认值，单击**保存**。

        ![设置AMH](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314012286_zh-CN.png)

        创建的虚拟主机，如下图所示。

        ![虚拟主机列表](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314012287_zh-CN.png)

3.  创建PHP网站所需的MySQL数据库。
    1.  在顶部导航栏，选择**MySQL** \> **快速建库**。

        ![快速建库](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314012288_zh-CN.png)

    2.  按需选择以下任一方式创建MySQL数据库。
        -   方法一：按下图所示完成数据库的配置，并单击**创建**。其中数据库编码一般选择UTF8即可。

            ![创建数据库1](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314112289_zh-CN.png)

        -   方法二：将**localhost**更改为**%**，以便远程管理MySQL。

            ![创建数据库2](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314112290_zh-CN.png)

4.  AMH搭建网站的准备工作完成后，您可以通过dedecms系统安装默认网站。去官网下载dedecms系统并上传到空间根目录。
    1.  去官网下载dedecms系统。
    2.  新增FTP账号。
        1.  在顶部导航栏，选择**FTP**。

            **说明：** 该FTP需绑定到之前已创建的空间中。

        2.  配置参数后，单击**保存**。

            ![新增FTP账号](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314112291_zh-CN.png)

            新增的FTP账号，如下图所示。

            ![FTP账号列表](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314112292_zh-CN.png)

    3.  登录FTP，上传dedecms系统。
        1.  登录后，FTP中有2个默认主页文件，您可以直接删除。

            ![FTP根目录](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314112293_zh-CN.png)

        2.  将文件压缩成zip格式并上传，如下图所示。

            ![压缩dedecms](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314112294_zh-CN.png)

            ![上传dedecms](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314112295_zh-CN.png)

    4.  登录FTP，解压已上传的文件。
        1.  选择创建的FTP帐号，单击**管理**。

            ![管理FTP账号1](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314112296_zh-CN.png)

        2.  登录FTP。

            ![登录FTP](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314112297_zh-CN.png)

        3.  选中需要解压的文件， 单击**智能解压**。

            ![只能解压](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314112298_zh-CN.png)

        4.  解压完成后，开始安装网站。

            ![完成解压](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314112299_zh-CN.png)

5.  在浏览器中输入之前绑定的域名（该域名需要先解析到服务器），并完成以下操作。完成操作后，您可以快速使用AMH建站，与其它PHP系统的安装和使用相同。

    ![输入域名1](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314112300_zh-CN.png)

    ![输入域名2](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314112301_zh-CN.png)

    ![输入域名3](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314212302_zh-CN.png)

    ![输入域名4](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9782/156767314212303_zh-CN.png)


