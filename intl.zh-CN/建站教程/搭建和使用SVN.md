# 搭建和使用SVN {#concept_pqr_4bb_ffb .concept}

Subversion\(SVN\) 是一个开源的版本控制系統, 也就是说 Subversion 管理着随时间改变的数据。

这些数据放置在一个中央资料档案库\(repository\) 中。这个档案库很像一个普通的文件服务器, 不过它会记住每一次文件的变动。这样您就可以把档案恢复到旧的版本, 或是浏览文件的变动历史。

## SVN 的一些概念 {#section_esy_dcb_ffb .section}

-   repository（源代码库）：源代码统一存放的地方
-   Checkout（提取）：当您手上没有源代码时，您需要从repository checkout一份源代码
-   Commit（提交）：如果您已经修改了代码，您需要Commit到repository
-   Update（更新）：当您已经Checkout了一份源代码，Update一下，您就可以与Repository上的源代码同步，您手上的代码就会有最新的变更

日常开发过程其实就是这样的（假设您已经Checkout并且已经工作了几天）：Update（获得最新的代码）—\> 作出自己的修改并调试成功 —\> Commit（大家就可以看到您的修改了）。

如果您与同事同时修改了同一个文件，SVN可以合并你们的改动，实际上SVN管理源代码是以行为单位的，就是说你们只要不是修改了同一行程序，SVN都会自动合并两种修改。如果是同一行，SVN会提示文件Confict（冲突），需要手动确认。

## 安装SVN { .section}

您可以采用以下任一种方法安装SVN。

**使用SVN版本控制镜像**

您可以在云市场购买使用 [SVN版本控制镜像](https://market.aliyun.com/products/55530001/jxsc000061.html) 的ECS实例。

创建了实例后，按以下步骤操作：

1.  登录 [ECS管理控制台](https://ecs.console.aliyun.com/#/home)。
2.  在左侧导航栏里，单击 **实例**。
3.  选择地域。
4.  找到新创建的ECS实例，在 **IP地址** 列获取实例的公网IP地址。

**手动安装SVN**

本文以CentOS 7.2 64位系统为例，说明如何在CentOS 7.2上安装SVN。

1.  [远程连接Linux实例](../../../../intl.zh-CN/用户指南/连接实例/使用用户名密码验证连接Linux实例.md#)。
2.  运行以下命令安装SVN。

    ```
    yum install subversion
    ```

3.  运行以下命令查看SVN版本。

    ```
    svnserve --version
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/154441191912528_zh-CN.png)

4.  按以下步骤创建版本库：
    1.  运行以下命令创建目录。

        ```
        mkdir /var/svn
        ```

    2.  依次运行以下命令创建版本库。

        ```
        cd /var/svn
        svnadmin create /var/svn/svnrepos
        ```

    3.  依次运行以下命令查看自动生成的版本库文件。

        ```
        cd svnrepos
        ls
        ```

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/154441191912529_zh-CN.png)

        Subversion目录说明：

        -   db目录：所有版本控制的数据存放文件。
        -   hooks目录：放置hook脚本文件的目录。
        -   locks目录：用来追踪存取文件库的客户端。
        -   format文件：是一个文本文件，里面只放了一个整数，表示当前文件库配置的版本号。
        -   conf目录：是这个仓库的配置文件（仓库的用户访问账号、权限等）。
    4.  运行命令 `cd conf/` 进入conf目录（该SVN版本库配置文件）。返回结果如下：
        -   authz：是权限控制文件。
        -   passwd：是账号密码文件。
        -   svnserve.conf：SVN服务配置文件。
    5.  按以下步骤设置账号密码：
        1.  运行 `vi passwd`。
        2.  按 `i` 键进入编辑模式。
        3.  在 `[users]` 块中添加用户账号和密码，格式：账号=密码，比如示例中的suzhan = redhat（注意等号两端要有一个空格）。
        4.  按 `Esc` 键退出编辑模式，并输入 `:wq` 保存并退出。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/154441191912530_zh-CN.png)

    6.  按以下步骤设置权限：
        1.  运行 `vi authz`。
        2.  按 `i` 键进入编辑模式。
        3.  在末尾添加如下代码（其中，r表示读，w表示写）：

            ```
            [/]
            suzhan=rw
            ```

        4.  按 `Esc` 键退出编辑模式，并输入 `:wq` 保存并退出。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/154441191912531_zh-CN.png)

    7.  按以下步骤修改svnserve.conf文件。
        1.  运行命令 `vi svnserve.conf`。
        2.  按 `i` 键进入编辑模式。
        3.  打开以下几个注释（注意每行不能以空格开始，等号两端要有一个空格）：

            ```
            anon-access = read #匿名用户可读，您也可以设置 anon-access = none，不允许匿名用户访问。设置为 none，可以使日志日期正常显示
            auth-access = write #授权用户可写
            password-db = passwd #使用哪个文件作为账号文件
            authz-db = authz #使用哪个文件作为权限文件
            realm = /var/svn/svnrepos #认证空间名，版本库所在目录
            ```

        4.  按 `Esc` 键退出编辑模式，并输入 `:wq` 保存并退出。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/154441191912532_zh-CN.png)

    8.  运行以下命令启动SVN版本库。

        ```
        svnserve -d -r /var/svn/svnrepos
        ```

    9.  运行命令 `ps -ef |grep svn` 查看SVN服务是否开启。

        如果返回结果如下图所示，表示SVN服务已经开启。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/154441191912533_zh-CN.png)


**说明：** 运行以下命令停止SVN命令。

```
killall svnserve
```

## 添加安全组规则 {#section_crh_12b_ffb .section}

SVN服务的默认端口为TCP 3690。您需要登录 [ECS管理控制台](https://ecs.console.aliyun.com/#/home)，[添加安全组规则](../../../../intl.zh-CN/用户指南/安全组/添加安全组规则.md#) 放行TCP 3690端口。

## 在Windows上测试 {#section_wm5_b2b_ffb .section}

这部分说明如何从本地（Windows操作系统）访问ECS实例上安装的SVN服务。

1.  在本地机器上安装 [TortoiseSVN客户端](http://tortoisesvn.net/downloads.html)。
2.  在您的本地项目文件夹（如示例中的C:\\KDR），右键空白处弹出菜单，选择 **SVN检出**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/154441191912534_zh-CN.png)

3.  指定资源库URL，格式为 `svn://实例公网IP地址/资源库名`；指定 **检出至目录**（如本示例中的C:\\KDR）；再单击 **确定**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/154441191912535_zh-CN.png)

    如果出现以图所示信息，表示检出成功。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/154441191912536_zh-CN.png)


**说明：** 第一次登录需要输入密码，一切以passwd文件里面的账户密码为主。

## 修改并提交项目 {#section_bxy_32b_ffb .section}

将项目下载到本地机器后，您可以在添加文件、修改文件、删除文件等。

**提交修改**

按以下步骤提交修改：

1.  在项目文件空白处单击右键，选择 **SVN提交**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/154441191912537_zh-CN.png)

2.  输入本次提交的版本更新信息（所作修改的注释）、勾选要提交的操作内容，单击 **确定**，即可把本机项目提交到SVN服务器资源库，覆盖掉资源库项目从而实现更新。

    **说明：** 

    -   如果发生提交冲突，即两人都提交修改，后提交者由于版本落后会提交失败。这时可以先备份自己的项目，从服务端下载最新的项目后，再将自己的项目覆盖到本地项目文件夹，最后SVN提交即可成功提交。
    -   假设您刚刚删掉了一个文件，这里就会显示如下截图所示信息。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/154441191912538_zh-CN.png)


**获取更新**

如果别人修改了SVN服务端资源库上的项目，您想下载最新的项目，则在本机项目文件空白处单击右键，选择 **SVN更新**，即可自动完成下载，并会提示所作的更新有哪些。

**说明：** 在原项目文件夹内选择SVN更新，会自动覆盖原有内容。我们建议您先备份，再更新，防止自己本来的项目内容丢失。

**SVN还原**

1.  打开一个文件夹，右键检出数据。
2.  删掉数据。
3.  根据您是否已经提交修改采取不同的操作：
    -   未提交时，右键单击空白处，选择 **TortoiseSVN** \> **SVN 还原**。
    -   已提交时，系统库里的数据也会得到同步，系统也会把它存的数据删掉。此时，您需要采取以下方法还原数据：
        1.  查看日志，确认删除了哪些文件。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/154441191912539_zh-CN.png)

        2.  将删掉的文件保存版本到删掉的位置。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9780/154441191912540_zh-CN.png)

4.  打开原文件夹，选择 **SVN提交**，系统库里的数据就和这个文件同步了。

## 相关链接 {#section_qrq_w2b_ffb .section}

更多开源软件尽在云市场：[https://market.aliyun.com/software](https://market.aliyun.com/software)

