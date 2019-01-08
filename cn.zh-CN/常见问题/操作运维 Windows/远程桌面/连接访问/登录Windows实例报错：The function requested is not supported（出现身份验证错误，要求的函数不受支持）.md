# 登录Windows实例报错：The function requested is not supported（出现身份验证错误，要求的函数不受支持） {#WindowsAuthenticationFailureAndCredSSPEdit .concept}

本文提供通过微软的RDP协议客户端远程连接Windows实例时报错：出现身份验证错误，要求的函数不受支持（The function requested is not supported）的解决方法。

![The function requested is not supported](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10592/154691592236309_zh-CN.png)

## 问题原因 { .section}

微软官方2018年5月更新了凭据安全支持提供程序协议（CredSSP）相关补丁和身份验证请求方式。当出现以下任一情景时会出现该连接错误：

-   **情景一**：客户端未更新该补丁，服务器端已更新该补丁且加密Oracle修正的策略为强制更新的客户端。
-   **情景二**：客户端已更新该补丁且加密Oracle修正的策略为强制更新的客户端，服务器端未更新该补丁。
-   **情景三**：客户端已更新该补丁且加密Oracle修正的策略为缓解，服务器端未更新该补丁。

    **说明：** 

    -   未更新该补丁指没有更新自2018年5月起至今的任意版本补丁（包括最新版本补丁）。
    -   已更新该补丁指更新过自2018年5月起至今的任意版本补丁或者所有版本补丁（包括最新版本补丁）。
    -   加密Oracle修正的策略路径为**计算机配置** \> **管理模板** \> **系统** \> **凭据分配** \> **加密 Oracle 修正**。更多信息请参考[相关文档](#Reference)。

## 解决方法一：服务器端允许任意版本的远程桌面连接 {#AllowAnyConnection .section}

**警告：** 此操作将允许较低安全级别的远程桌面连接。为了保证您的信息安全，建议您先使用方法一快速登录实例，再采用[方法二](#WindowsUpdate)，最后将方法一的配置做反向修改，关闭**允许运行任意版本远程桌面的计算机连接（较不安全）**特性。

**Windows Server 2008 R2**

1.  通过[远程连接功能](../../../../../cn.zh-CN/用户指南/连接实例/使用管理终端连接ECS实例.md#)登录Windows实例。
2.  打开**开始**，右键单击**计算机**，选择**属性**。

    ![The function requested is not supported](images/36446_zh-CN.jpeg)

3.  在系统控制面板中，单击**远程设置**，在弹出的**远程桌面**选项中选择**允许运行任意版本远程桌面的计算机连接（较不安全）**并单击**确定**。

    ![The function requested is not supported](images/36447_zh-CN.jpeg)


**Windows Server 2012 R2**

1.  通过[远程连接功能](../../../../../cn.zh-CN/用户指南/连接实例/使用管理终端连接ECS实例.md#)登录Windows实例。
2.  在开始界面，右键单击**这台电脑**，选择**属性**。

    ![The function requested is not supported](images/36448_zh-CN.jpeg)

3.  在系统控制面板中，单击**远程设置**，在弹出的**远程桌面**选项中取消选择**仅允许运行使用网络级别身份验证的远程桌面的计算机连接（建议）**并单击**确定**。

    ![The function requested is not supported](images/36449_zh-CN.jpeg)


**Windows Server 2016**

1.  通过[远程连接功能](../../../../../cn.zh-CN/用户指南/连接实例/使用管理终端连接ECS实例.md#)登录Windows实例。
2.  打开**开始** \> **Windows系统** \> **此电脑**，右键单击**此电脑**，选择**更多** \> **属性**。

    ![The function requested is not supported](images/36450_zh-CN.jpeg)

3.  在系统控制面板中，单击**远程设置**，在弹出的**远程桌面**选项中取消选择**仅允许运行使用网络级别身份验证的远程桌面的计算机连接（建议）** 并单击**确定**。

    ![The function requested is not supported](images/36451_zh-CN.jpeg)


## 解决方法二：下载Windows安全更新 {#WindowsUpdate .section}

1.  通过[远程连接功能](../../../../../cn.zh-CN/用户指南/连接实例/使用管理终端连接ECS实例.md#)登录Windows实例。

    **说明：** 如果您的客户端是Windows系统，请同样执行如下操作。

2.  搜索并打开Windows更新。
3.  单击**检查更新**下载积累的更新。

    ![The function requested is not supported](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10592/154691592236452_zh-CN.png)

4.  等待更新下载和安装。
5.  重启实例以完成安装更新。

您也可以根据自己的操作系统，在Windows实例和客户端上安装CredSSP对应的安全更新安装包：

-   [Windows Server 2008 32位下载](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/71931/cn_zh/1528889331663/windows6.0-kb4056564-v2-x86.msu?spm=a2c63.o282931.a3.18.43ed50f1Dm2XgE&file=windows6.0-kb4056564-v2-x86.msu)
-   [Windows Server 2008 R2 64位安全更新下载](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/71931/cn_zh/1528861821268/windows6.1-kb4103712-x64.msu?spm=a2c63.o282931.a3.19.43ed50f1Dm2XgE&file=windows6.1-kb4103712-x64.msu)
-   [Windows Server 2008 R2 64位质量和安全更新下载](https://windows-fix.oss-cn-beijing.aliyuncs.com/windows6.1-kb4103718-x64.msu?spm=a2c63.o282931.a3.20.43ed50f1Dm2XgE&file=windows6.1-kb4103718-x64.msu)
-   [Windows Server 2012 R2 64位安全更新下载](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/71931/cn_zh/1528861769725/windows8.1-kb4103715-x64.msu?spm=a2c63.o282931.a3.21.43ed50f1Dm2XgE&file=windows8.1-kb4103715-x64.msu)
-   [Windows Server 2012 R2 64位质量和安全更新下载](https://windows-fix.oss-cn-beijing.aliyuncs.com/windows8.1-kb4103725-x64.msu?spm=a2c63.o282931.a3.22.43ed50f1Dm2XgE&file=windows8.1-kb4103725-x64.msu)
-   [Windows Server 2016 64位下载](https://windows-fix.oss-cn-beijing.aliyuncs.com/windows10.0-kb4103723-x64.msu?spm=a2c63.o282931.a3.23.43ed50f1Dm2XgE&file=windows10.0-kb4103723-x64.msu)
-   [Windows Server 1709 64位下载](https://windows-fix.oss-cn-beijing.aliyuncs.com/windows10.0-kb4103727-x64.msu?spm=a2c63.o282931.a3.24.43ed50f1Dm2XgE&file=windows10.0-kb4103727-x64.msu)

## 解决方法三：修改注册表 {#RegEdit .section}

针对已经更新CredSSP相关补丁的客户端或者服务器端，您可以手动修改注册表，也可以运行我们为您准备的PowerShell脚本。

**警告：** 

-   使用注册表编辑器或其他方法修改注册表不当，可能会出现严重问题，您需要自行承担修改注册表风险。修改注册表之前，建议您先通过[创建快照](../../../../../cn.zh-CN/用户指南/快照/创建快照.md#)备份数据，以免数据丢失。
-   本方法会降低您本地计算机或实例的安全性，我们建议您使用[方法二](#WindowsUpdate)。

**手动修改**

1.  登录实例或者本地计算机。
2.  单击**开始** \> **运行**，输入**regedit**，单击**确定**。
3.  定位到HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Policies\\System\\CredSSP\\Parameters键，如果CredSSP或者Parameters键不存在，请新建CredSSP或者Parameters键。
4.  在Parameters键下新建DWORD值AllowEncryptionOracle，并设置数据为2。

    ![The function requested is not supported](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10592/154691592236453_zh-CN.png)

5.  重启实例或者本地计算机。

**脚本修改**

1.  登录实例或者本地计算机。
2.  以管理员身份运行Windows PowerShell。
3.  执行如下脚本。

    ```language-shell
    New-Item -Path HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System -Name CredSSP -Force
    New-Item -Path HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System\CredSSP -Name Parameters -Force
    Get-Item -Path HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System\CredSSP\Parameters | New-ItemProperty -Name AllowEncryptionOracle -Value 2 -PropertyType DWORD -Force
    
    ```

4.  重启实例或者本地计算机。

    **说明：** 若您优先使用本方法修改了注册表，随后又更新了客户端和ECS实例安全补丁，我们建议您将AllowEncryptionOracle的值设为0或者1以获得更高的安全性。


## 相关文档 {#Reference .section}

-   [CVE-2018-0886的CredSSP更新](https://support.microsoft.com/zh-cn/help/4093492/credssp-updates-for-cve-2018-0886-march-13-2018?spm=a2c63.o282931.a3.31.43ed50f1Dm2XgE)
-   [CVE-2018-0886 | CredSSP远程执行代码漏洞](https://portal.msrc.microsoft.com/zh-cn/security-guidance/advisory/CVE-2018-0886?spm=a2c63.o282931.a3.32.43ed50f1Dm2XgE)

