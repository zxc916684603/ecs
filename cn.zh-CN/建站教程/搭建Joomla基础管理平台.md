# 搭建Joomla基础管理平台 {#concept_an2_t25_2fb .task}

Joomla是一套知名的内容管理系统。Joomla是使用PHP语言和MySQL数据库所开发的软件系统，最新版本3.x实现了许多技术上的优化，是目前的稳定版本。本教程主要介绍如何在阿里云服务器ECS上搭建Joomla基础管理平台。

使用本教程进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm?)。

本教程适用于熟悉ECS、熟悉Linux系统， 刚开始使用阿里云ECS实例进行建站的用户。

本教程示例步骤中使用的操作系统为CentOS 6.5 64位。

## 操作步骤 {#section_nay_1qv_7oa .section}

完成以下步骤，在阿里云服务器ECS上搭建Joomla基础管理平台：

1.  步骤一：使用Joomla镜像
    -   如果您是新购ECS实例，可以使用云市场镜像搭建Joomla平台。具体步骤请参见[步骤一：使用云市场镜像创建ECS实例](#section_q70_cxg_or8)。
    -   如果您已购买ECS实例，可以通过更换系统盘的方式，来更换所需要的镜像。具体步骤请参见[步骤一：更换已购实例的镜像](#section_ejm_w1b_goc)。
2.  [步骤二：安装Joomla](#section_jxt_daz_4vz)
3.  [步骤三：配置外网访问](#section_4rz_5pj_ina)
4.  [步骤四：配置Joomla](#section_01x_nlv_v3c)

相关操作如下：

-   [查看并修改MySQL以及FTP密码](#section_98v_wr7_0nv)
-   [卸载软件](#section_075_xkt_0yf)
-   [为Joomla安装中文语言包](#section_ru7_goc_oe2)

## 步骤一：使用云市场镜像创建ECS实例 {#section_q70_cxg_or8 .section}

购买ECS实例，如果需要备案网站，计费方式请选择**包年包月**。对于个人使用的小型网站，一台云服务器ECS实例可以满足需求。

如果您已有包含Joomla环境的自定义镜像，可以使用该镜像创建实例。本节只介绍在新购ECS实例上使用云市场镜像搭建Joomla平台的操作步骤。

**说明：** 本教程示例步骤中使用的云市场Joomla镜像，目前仅支持CentOS、Ubuntu和Aliyun Linux。

1.  登录[ECS管理控制台](https://ecs.console.aliyun.com)。
2.  在左侧导航栏，单击**实例与镜像** \> **实例**。
3.  在实例列表页面，单击**创建实例**。
4.  在自定义购买页面，完成以下配置。 
    1.  选择**计费方式**。如果您需要备案网站，请选择**包年包月**。 

        ![选择计费方式](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078412405_zh-CN.png)

    2.  选择**地域**。例如，如果您的网站访问者都分布在北京地区，则可以选择**华北 2（北京）**。 

        地域是指实例所在的地理位置。您可以根据所在的地理位置选择地域。地域与用户距离越近，延迟相对越少，下载速度相对越快。

        **说明：** 

        -   实例创建完成后，不支持更换地域。
        -   不同地域提供的可用区数量、实例系列、存储类型、实例价格等也会有所差异。请根据您的业务需求进行选择。
    3.  选择**实例**，根据您网站的访问量选择实例规格（vCPU、内存），设置**购买实例数量**。 对于个人网站，1vCPU 2GiB或2vCPU 4GiB一般能够满足需求。实例规格详情，请参见[实例规格族](../cn.zh-CN/实例/实例规格族.md#)。

        ![选择实例规格](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078412407_zh-CN.png)

    4.  选择**镜像**。单击**镜像市场**，然后单击**从镜像市场获取更多选择（含操作系统）**。 

        ![单击镜像市场](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078412410_zh-CN.png)

    5.  在镜像市场对话框，搜索[Joomla!建站系统](https://market.aliyun.com/products/53616009/jxsc000035.html?spm=5176.730005.0.0.AoD4Vi)，然后单击**使用**。 

        ![选择镜像](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078412411_zh-CN.png)

    6.  选择**系统盘**和**数据盘**。您可以创建全新的磁盘作为数据盘，也可以选择**用快照创建磁盘**，将快照的数据直接复制到磁盘中作为数据盘。 

        ![选择系统盘和数据盘](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078412412_zh-CN.png)

    7.  选择网络类型。对于建站的用户，选择**专有网络**，然后选择专有网络VPC、交换机。 

        ![选择专有网络](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078458090_zh-CN.png)

    8.  选择**公网带宽**。因为创建的实例需要访问公网，选中**分配公网IPv4地址**，否则不分配公网IP，您需要绑定弹性公网IP地址。 

        ![选择公网带宽](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078458094_zh-CN.png)

    9.  选择**安全组**。
    10. 设置实例的**登录凭证**。如果使用自定义密码，请务必牢记密码。您也可以在创建完成后再设置密码。 

        ![设置登录凭证](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078412413_zh-CN.png)

    11. 设置**购买时长**。
5.  单击**确认下单**。
6.  确认订单信息无误后，单击**确认支付**。

## 步骤一：更换已购实例的镜像 {#section_ejm_w1b_goc .section}

如果您已购买ECS实例，可以通过更换系统盘的方式，来更换所需要的镜像。具体操作，请参见[更换系统盘（非公共镜像）](../cn.zh-CN/块存储/云盘/更换系统盘/更换系统盘（非公共镜像）.md#)。本节选择PHP运行环境镜像（CentOS 64 位 | PHP 5.4|Nginx 1.4|Joomla）。镜像说明如下：

-   镜像版本说明操作系统：CentOS 6.5 64 位。

    镜像版本V1.0软件明细：Nginx1.4.7、PHP 5.4.27、MySQL5.5.37、FTP2.2.2、Joomla!3.3.3 1.2和镜像安装说明。

-   镜像环境里相应软件的安装，是基于阿里云Linux版的一键安装包源码1.3.0版本，在此基础上修改、优化了相应功能，编译安装完成。
-   在镜像环境中，/root/sh-1.3.0-centos-joomla.zip是安装镜像环境的脚本。您可以在CentOS 6.5系统中自行采用此脚本安装，安装后的环境跟镜像里初始化的环境一致。

    **说明：** 如果使用此脚本安装镜像环境，需要运行chmod 777 -R sh-1.3.0-centos-joomla命令为脚本赋予777安装权限。

-   在镜像环境中出于安全考虑，Joomla默认设置页面只容许127.0.0.1访问，/root/目录下提供一个joomla\_opennet.sh的脚本 。用户运行此脚本后，可以通过外网访问Joomla的默认设置页面。
-   在镜像环境中，/root/sh-1.3.0-centos-joomla是安装环境的主目录，镜像中的环境是在此目录下编译安装的。

## 步骤二：安装Joomla {#section_jxt_daz_4vz .section}

完成以下操作，在CentOS 6.5系统中，通过安装镜像环境的脚本/root/sh-1.3.0-centos-joomla.zip自行安装Joomla。

1.  解压缩安装脚本/root/sh-1.3.0-centos-joomla.zip。
2.  运行以下命令为脚本授予777安装权限。 

    ``` {#codeblock_led_jch_27h}
    chmod 777 -R sh-1.3.0-centos-joomla
    ```

3.  运行以下命令进入安装目录。 

    ``` {#codeblock_pnp_rpt_1d5}
    cd sh-1.3.0-centos-joomla
    ```

4.  运行以下命令开始安装。 

    ``` {#codeblock_0n7_lel_jnn}
    ./install
    ```

5.  根据界面提示，输入y。 

    ![输入y](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078412414_zh-CN.png)

    以下界面表示，持续安装中。

    ![安装中](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078512415_zh-CN.png)

    如果出现以下界面，表示安装结束。

    ![安装结束](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078512416_zh-CN.png)

6.  运行以下命令检查端口是否开启。 

    ``` {#codeblock_cnt_8ww_9wj}
    netstat -luntp
    ```

    如果出现以下界面，表示端口80、21、9000、3306等都已开启。

    ![端口已开启](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078512417_zh-CN.png)


## 步骤三：配置外网访问 {#section_4rz_5pj_ina .section}

在镜像环境中出于安全考虑，Joomla默认页面只允许127.0.0.1访问。如需通过外网访问Joomla的默认设置页面，执行以下命令运行/root/joomla\_opennet.sh脚本。

``` {#codeblock_6no_ylp_pna}
/root/joomla_opennet.sh
```

## 步骤四：配置Joomla {#section_01x_nlv_v3c .section}

完成以下步骤，配置Joomla。

1.  在浏览器地址栏中输入`http://ECS实例公网IP地址`，回车即可看到Joomla的初始化界面。
2.  选择**语言**，并填写相关内容，单击**下一步**。 

    ![选择语言](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078512418_zh-CN.png)

3.  选择**MySQL**，填写相关权限后，单击**下一步**。 

    ![选择mysql](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078512419_zh-CN.png)

4.  查看相关配置是否符合，确认完毕后，单击**安装**。 

    ![单击安装](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078512420_zh-CN.png)

    出现以下界面，表示安装完成。

    ![安装完成](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078512421_zh-CN.png)

5.  依次运行以下命令进入服务器/alidata/www/default目录下删除installation目录。 
    1.  ``` {#codeblock_z4g_fj2_hyq}
cd /alidata/www/default
```

    2.  ``` {#codeblock_zs0_iwn_fyh}
rm -rf installation/
```


至此，Joomla搭建完成。Joomla访问方式如下：

-   访问前端网站：`http://ECS实例公网IP地址`
-   访问后台管理：`http://ECS实例公网IP地址/administrator`

## 查看并修改MySQL以及FTP密码 {#section_98v_wr7_0nv .section}

密码存储在/alidata/account.log文件中。查看、修改密码的步骤如下：

1.  进入服务器的系统后，可以在任意目录下，运行以下命令查看密码。 

    ``` {#codeblock_sbf_qga_ty5}
    cat /alidata/account.log
    ```

2.  使用root用户登录系统后，运行以下命令修改密码。 
    -   修改FTP的密码

        ``` {#codeblock_a9q_8ld_xni}
        passwd www 
        ```

    -   修改MySQL的密码

        ``` {#codeblock_zzw_y4p_w35}
        mysqladmin -uroot -p旧密码 password 新密码
        ```

        **说明：** -p和旧密码之间没有空格，password和新密码之间有空格。


## 卸载软件 {#section_075_xkt_0yf .section}

卸载镜像环境中安装的软件，可以参见如下命令。

``` {#codeblock_zvd_r0x_epd}
cd /root/sh-1.3.0-centos-joomla
```

``` {#codeblock_dqf_kq8_vvq}
./uninstall.sh
```

**说明：** 

-   执行以上操作会清理环境的/alidata目录，卸载前请自行备份好相应数据。
-   如果不小心删除了/root/sh-1.3.0-centos-joomla，可以使用以下命令重新解压缩脚本文件/root/sh-1.3.0-centos-joomla.zip。

    ``` {#codeblock_shy_ssa_0wl}
    cd
    unzip sh-1.3.0-centos-joomla.zip
    chmod 777 -R sh-1.3.0-centos-joomla
    cd sh-1.3.0-centos-joomla
    ./uninstall
    ```


## 为Joomla安装中文语言包 {#section_ru7_goc_oe2 .section}

Joomla安装完成之后默认前台后台都是英文界面，中文语言需要手动安装。

1.  将中文语言包从服务器下载至本地。 中文语言包在服务器的/alidata/res目录中。

    ![下载语言包至本地](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078512422_zh-CN.png)

2.  登录Joomla之后单击**Extensions（扩展）** \> **Extension Manager（扩展管理）**，打开扩展配置页面后，上传简体中文语言包。 

    ![上传中文语言包](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078612423_zh-CN.png)

3.  单击**Update & Install**上传。 上传成功，如下图所示。

    ![上传成功](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078612424_zh-CN.png)

4.  单击**Extensions（扩展）** \> **Language Manager（语言管理）**，设置前端后台的默认语言，设置完后并单击右上角**Logout**重新登录。 

    ![设置默认语言](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078612425_zh-CN.png)

    登录后进入中文界面，如下所示。

    ![进入中文界面](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9784/156888078612426_zh-CN.png)


