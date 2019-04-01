# How do I install the .NET Framework 3.5 SP1 in a Windows instance? {#concept_pdc_llk_3gb .concept}

When you install the .NET Framework 3.5 SP1 through Server Manager or by other means, if the system prompts you that the source file cannot be found, you can install it through commands by following the instructions below .

## Symptom { .section}

When .NET Framework 3.5 is being installed in a Windows instance, the following error is displayed:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/87175/155410406336006_en-US.png)

## Cause {#section_kqr_hqk_3gb .section}

To use a Feature on Demand \(FOD\) in Windows Server 2012 and higher, you need to download the installation package from Windows Update. However, a Windows instance uses Windows Server Update Services \(WSUS \) to get the updates by default. This results in missing installation and language package files of the .NET Framework, and the system prompts you that **Source file cannot be found**.

**Note:** 

-   The PowerShell commands described in this topic can all be executed through the Cloud Assistant. For more information, see [Cloud Assistant](../../../../../reseller.en-US/Deployment & Maintenance/Cloud assistant/Cloud assistant.md#).
-   If you want to automatically install the .NET Framework 3.5 by running PowerShell commands during instance creation, we recommend that you do it with the help of instance user data. For more information, see [User data](../../../../../reseller.en-US/Instances/Configure instances/User-defined data/User data.md#).

## Windows Server 2008 {#section_xm5_wlk_3gb .section}

Open the CMD utility as an administrator and run the following command to enable .NET Framework 3.5 :

```
cmd /c start /w ocsetup NET-Framework-Core
```

## Windows Server 2008 R2 {#section_wsb_ymk_3gb .section}

1.  Open the CMD utility as an administrator and run powershell to switch to interactive mode.
2.  Run the following commands to enable .NET Framework 3.5:

    ```
    Import-Module Servermanager
    Add-WindowsFeature Net-Framework-Core
    ```


## Windows Server 2012 R2/2016/1709/1809 {#section_c4f_vnk_3gb .section}

1.  Open the CMD utility as an administrator and run powershell to switch to interactive mode.
2.  Run the following commands to modify the registry to set the update source to Windows Update:

    ```
    $ServicingPolicy = "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\Servicing"
    New-Item $ServicingPolicy -Force
    New-ItemProperty -Path $ServicingPolicy -Name RepairContentServerSource -PropertyType DWord -Value 2 -Force
    New-ItemProperty -Path $ServicingPolicy -Name LocalSourcePath -PropertyType ExpandString -Force
    ```

3.  Run the following commands to enable .NET Framework 3.5:

    ```
    Import-Module Servermanager
    Add-WindowsFeature Net-Framework-Core
    ```


## Windows Server 2019 {#section_lmd_lpk_3gb .section}

1.  Open the CMD utility as an administrator and run powershell to switch to interactive mode.
2.  Run the following command to enable .NET Framework 3.5:

    ```
    Add-WindowsCapability -Online -Name Net-Framework-Core
    ```


