# Windows Server 2012 R2/2016/2019无法安装.NET Framework 3.5.1或语言包的解决方法 {#concept_38203_zh .concept}

本文通过将更新源从WSUS切换为Windows Update解决无法安装.NET Framework 3.5.1或语言包的问题。

## 问题现象 {#section_lx0_oqu_q9s .section}

-   问题现象一：.NET Framework报错找不到源文件

    在Windows Server 2012 R2、Windows Server 2016或Windows Server 2019系统中安装.NET Framework 3.5.1时报如下图所示的错误：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10530/155729921245359_zh-CN.png)

-   问题现象二：无法安装语言包

    在控制面板切换语言或者Windows Update中查询语言选项时，无法选择或者安装语言包。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10530/155729921245360_zh-CN.png)


## 原因分析 { .section}

由于Windows实例默认采用WSUS（Windows Server Update Services）获取更新源，导致.NET Framework和语言包安装文件缺失。遂报错**找不到源文件**或者无法安装语言包。

## 解决方法 { .section}

1.  从**开始**菜单中找到PowerShell，右键单击选择**以管理员身份运行**。
2.  运行以下命令修改注册表将更新源设置为Windows Update。

    ```
    Set-ItemProperty -Path 'HKLM:\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU' -Name UseWUServer -Value 0
    Restart-Service -Name wuauserv
    ```

3.  运行以下命令通过PowerShell安装.NET Framework。

    ```
    Install-WindowsFeature Net-Framework-Core
    ```

    **说明：** 您也可以继续在Server Manager中安装.NET Framework，或者在控制面板中安装语言包。

4.  （可选）运行以下命令将更新源重新设置为WSUS。

    ```
    Set-ItemProperty -Path 'HKLM:\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU' -Name UseWUServer -Value 1
    Restart-Service -Name wuauserv
    ```


## 补充说明 { .section}

-   Windows Server 2012与Windows Server 2016内存占用较高，安装其他应用程序使内存消耗更高，可能会导致内存不足引起安装.NET Framework失败，因此建议增加物理内存，如果是I/O优化实例，可以酌情[开启系统虚拟内存](https://help.aliyun.com/knowledge_detail/40995.html)。
-   如果安装.NET Framework报错`0x800f081f`，请检查公网网络是否正常。如果正常，可能是连接Windows Update服务器链路不稳定导致更新失败，建议更换时间段重试。

