# What can I do if I am unable to install .NET Framework 3.5.1, or a language package, on Windows Server 2012 R2/2016/2019? {#concept_38203_zh .concept}

This topic describes how to change the update source from Windows Server Update Services \(WSUS\) to Windows Update so that you can install .NET Framework 3.5.1, or a language package, on Windows Server 2012 R2/2016/2019.

## Issues {#section_lx0_oqu_q9s .section}

-   .NET Framework reports that the source file cannot be found.

    When .NET Framework 3.5.1 is installed on Windows Server 2012 R2, Windows Server 2016, or Windows Server 2019, an error message is displayed, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10530/155869239845359_en-US.png)

-   No language package is available.

    No language package is available on the Control Panel or in Windows Update.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10530/155869239845360_en-US.png)


## Cause { .section}

By default, a Windows instance uses Windows Server Update Services \(WSUS\) to access the update source. As a result, installation files of .NET Framework or the language package cannot be found.

## Solution { .section}

1.  In the Start menu, right-click **PowerShell**, and then select **Run as Administrator**.
2.  Run the following command to modify the registry and change the update source to Windows Update:

    ```
    Set-ItemProperty -Path 'HKLM:\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU' -Name UseWUServer -Value 0
    Restart-Service -Name wuauserv
    ```

3.  Run the following command to use PowerShell to install .NET Framework:

    ```
    Install-WindowsFeature Net-Framework-Core
    ```

    **Note:** You can also install .NET Framework in Server Manager or install a language package through the Control Panel.

4.  Optional. Run the following command to change the update source back to WSUS:

    ```
    Set-ItemProperty -Path 'HKLM:\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU' -Name UseWUServer -Value 1
    Restart-Service -Name wuauserv
    ```

    **Note:** 

    -   Windows Server 2012 and Windows Server 2016 feature high CPU usage, especially when they are installed with multiple applications. Therefore, .NET Framework may fail to be installed due to insufficient memory. To resolve this issue, we recommend that you increase the amount of memory. For example, if you use an I/O-optimized instance, you can enable the virtual memory as needed. For more information, see [How to configure the virtual memory of ECS Windows Server](https://partners-intl.aliyun.com/help/doc-detail/40995.htm).
    -   If the `0x800f081f` error occurs when you install .NET Framework, you need to check whether the public network operates normally. If the public network is normal, the error may be caused by an unstable link to the Windows Update server. In this case, we recommend that you try again later.

