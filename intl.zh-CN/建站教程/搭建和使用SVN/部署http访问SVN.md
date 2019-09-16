# 部署http访问SVN {#task_1597497 .task}

本教程介绍如何通过http访问模式来部署SVN。

使用本教程进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.alibabacloud.com/register/intl_register.htm)。

本教程手动部署SVN的示例步骤中使用了以下版本软件。操作时，请您以实际软件版本为准。

-   操作系统：公共镜像CentOS 7.2 64位
-   SVN：1.7.14
-   Apache：2.4.6

## 操作步骤 {#section_qiv_j37_8qr .section}

通过http访问模式部署SVN的操作步骤如下：

1.  [步骤一：安装SVN](#section_gyu_lbx_856)
2.  [步骤二：安装Apache](#section_ily_okj_kbz)
3.  [步骤三：安装mod\_dav\_svn](#section_gbn_l1r_5yj)
4.  [步骤四：配置SVN](#section_ed8_meq_o0d)
5.  [步骤五：配置Apache](#section_dk7_05x_t3w)
6.  [步骤六：配置安全组规则](#section_ggx_hu5_701)
7.  [步骤七：浏览器测试访问](#section_svb_rm4_e81)

## 步骤一：安装SVN {#section_gyu_lbx_856 .section}

完成以下操作，安装SVN：

1.  [远程连接Linux实例](../intl.zh-CN/实例/连接实例/连接Linux实例/使用用户名密码验证连接Linux实例.md#)。
2.  运行以下命令安装SVN。 

    ``` {#codeblock_6lv_c0n_jrc}
    yum install subversion
    ```

3.  运行以下命令查看SVN版本。 

    ``` {#codeblock_8as_yc3_nxy}
    svnserve --version
    ```


## 步骤二：安装Apache {#section_ily_okj_kbz .section}

完成以下操作，安装Apache：

1.  运行以下命令安装httpd。 

    ``` {#codeblock_pmq_rpw_jkz}
    yum install httpd
    ```

2.  运行以下命令查看httpd版本。 

    ``` {#codeblock_bu4_pih_aey}
    httpd -version
    ```


## 步骤三：安装mod\_dav\_svn {#section_gbn_l1r_5yj .section}

运行以下命令安装mod\_dav\_svn。

``` {#codeblock_mu2_eil_swx}
yum install mod_dav_svn
```

## 步骤四：配置SVN {#section_ed8_meq_o0d .section}

完成以下操作，配置SVN：

1.  运行以下命令创建版本库根目录。 

    ``` {#codeblock_h70_mqa_qxs}
    mkdir /var/svn
    ```

2.  运行以下命令创建SVN仓库。 

    ``` {#codeblock_qtv_rb0_9pa}
    svnadmin create /var/svn/svnrepo
    ```

3.  运行以下命令修改SVN仓库的用户组为apache。 

    ``` {#codeblock_8zo_suk_q8j}
    chown -R apache:apache /var/svn/svnrepo
    ```

4.  运行以下命令创建用户配置文件passwd。 

    ``` {#codeblock_26i_osj_w9x}
    touch /var/svn/passwd 
    ```

5.  运行以下命令创建用户admin并设置密码。本示例中，密码设置为admin123。 

    ``` {#codeblock_qcv_gqo_rjv}
    htpasswd /var/svn/passwd admin
    ```

6.  运行以下命令创建用户访问权限文件。 

    ``` {#codeblock_3md_sng_zq2}
    cp /var/svn/svnrepo/conf/authz /var/svn/authz
    ```


## 步骤五：配置Apache {#section_dk7_05x_t3w .section}

完成以下操作，配置Apache：

1.  运行`vim /etc/httpd/conf.d/subversion.conf`命令打开httpd配置文件。
2.  按`i`键进入编辑模式。
3.  输入以下配置信息： 

    ``` {#codeblock_dna_p1u_ag7}
    <Location /svn>
    DAV svn
    SVNParentPath /var/svn
    AuthType Basic
    AuthName "Authorization SVN"
    AuthzSVNAccessFile /var/svn/authz
    AuthUserFile /var/svn/passwd
    Require valid-user
    </Location>
    ```

4.  按`Esc`键后，输入`:wq`保存并关闭文件。
5.  运行以下命令启动Apache服务。 

    ``` {#codeblock_1fn_ela_x1s}
    systemctl start httpd.service
    ```


## 步骤六：配置安全组规则 {#section_ggx_hu5_701 .section}

SVN服务的默认端口为TCP 3690。您需要登录ECS管理控制台，放行TCP 3690端口。具体操作，请参见[添加安全组规则](../intl.zh-CN/安全/安全组/添加安全组规则.md#)。

## 步骤七：浏览器测试访问 {#section_svb_rm4_e81 .section}

完成以下操作，浏览器测试访问：

1.  打开浏览器。
2.  输入网址`http://<ECS实例公网IP>/svn/<SVN仓库名>`并按回车键。本示例中，SVN仓库名为svnrepo。
3.  输入账号和密码，即您在passwd文件中设置的账号和密码。本示例中，账号为admin，密码为admin123。 

    返回结果如下图所示，表示成功访问之前新建的SVN仓库。

    ![访问结果](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/156862702944304_zh-CN.png)


