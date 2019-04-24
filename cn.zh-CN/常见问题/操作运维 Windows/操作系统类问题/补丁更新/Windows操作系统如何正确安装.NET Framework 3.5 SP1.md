# Windows操作系统如何正确安装.NET Framework 3.5 SP1 {#concept_pdc_llk_3gb .concept}

当您使用Server Manager等其他安装方法安装.NET Framework 3.5 SP1被提示找不到源文件时，可以参考本文描述通过命令安装.NET Framework 3.5 SP1。

## 现象描述 { .section}

在Windows实例中安装.NET Framework 3.5时报如下图所示的错误：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/87175/155612144036006_zh-CN.png)

## 原因分析 {#section_kqr_hqk_3gb .section}

Windows Server 2012以及更高的操作系统版本的FOD（Feature on Demand）功能时，需要从Windows Update下载安装源。由于Windows实例默认采用WSUS（Windows Server Update Services）获取更新源，导致.NET Framework和语言包安装文件缺失。遂报错**找不到源文件**。

**说明：** 

-   本文涉及的PowerShell命令均可以通过云助手完成部署。更多详情，请参阅[云助手](../../../../cn.zh-CN/部署与运维/云助手/云助手概述.md#)。
-   若您希望在创建实例期间通过PowerShell命令自动安装.NET Framework 3.5，建议您配合实例自定义数据实现。更多详情，请参阅[实例自定义数据](../../../../cn.zh-CN/实例/管理实例/使用实例自定义数据/生成实例自定义数据.md#)。

## Windows Server 2008操作步骤 {#section_xm5_wlk_3gb .section}

以管理员身份打开CMD，运行以下命令启用.NET Framework 3.5：

```
cmd /c start /w ocsetup NET-Framework-Core
```

## Windows Server 2008 R2操作步骤 {#section_wsb_ymk_3gb .section}

1.  以管理员身份打开CMD，并运行powershell切换到交互模式。
2.  运行以下命令启用.NET Framework 3.5：

    ```
    Import-Module Servermanager
    Add-WindowsFeature Net-Framework-Core
    ```


## Windows Server 2012 R2/2016/2019/1709/1809操作步骤 {#section_c4f_vnk_3gb .section}

1.  以管理员身份打开CMD，并运行powershell切换到交互模式。
2.  运行以下命令修改注册表将更新源设置为Windows Update：

    ```
    $ServicingPolicy = "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\Servicing"
    New-Item $ServicingPolicy -Force
    New-ItemProperty -Path $ServicingPolicy -Name RepairContentServerSource -PropertyType DWord -Value 2 -Force
    New-ItemProperty -Path $ServicingPolicy -Name LocalSourcePath -PropertyType ExpandString -Force
    ```

3.  运行以下命令启用.NET Framework 3.5：

    ```
    Import-Module Servermanager
    Add-WindowsFeature Net-Framework-Core
    ```


