# Known issues {#concept_e3m_ktl_jgb .concept}

This topic describes the known issues of Alibaba Cloud images on different platforms, the scope of these issues, and the corresponding solutions.

## Debian 9.6: Classic network configuration {#section_zyc_kxl_jgb .section}

-   **Issue**: Classic network instances created by using Debian 9 public images fail to be pinged.
-   **Cause**: Classic network instances cannot obtain IP addresses automatically through the Dynamic Host Configuration Protocol \(DHCP\) because Debian 9 disables the systemd-networkd service by default.
-   **Image**: debian\_9\_06\_64\_20G\_alibase\_20181212.vhd
-   **Solution**: Run the following command:

    ```
    systemctl enable systemd-networkd 
    systemctl start systemd-networkd
    ```


## CentOS 6.8: An instance installed with the NFS Client fails to respond. {#section_bwm_1hc_dhb .section}

-   **Issue**: An instance that is running CentOS 6.8 and has NFS Client installed fails repeatedly to respond and must be restarted.
-   **Cause**: When you use the NFS service, the NFS Client attempts to end the TCP connection if a glitch occurs due to communication latency. Specifically, if the NFS Server is delayed in sending a response to the NFS Client, the connection used by the NFS Client may be stalled in the FIN\_WAIT2 state. Normally, the FIN\_WAIT2 state expires and closes after one minute and the NFS Client initiates another connection. However, a kernel of version 2.6.32-696 to 2.6.32-696.10 has a defect in TCP connection establishment. As a result, the connection will remain in the FIN\_WAIT2 state indefinitely, which means the NFS Client cannot end the TCP connection or initiate a new TCP connection.
-   **Image**: centos\_6\_08\_32\_40G\_alibase\_20170710.vhd and centos\_6\_08\_64\_20G\_alibase\_20170824.vhd
-   **Solution**: Run the following command to upgrade the kernel to v2.6.32-696.11 or a later version. Note that you must restart the ECS instance for the upgrade to take effect:

    ```
    yum update
    ```

    **Note:** Before you perform any operations on the instance, you must [Create a snapshot](../../../../intl.en-US/Snapshots/Use snapshots/Create a snapshot.md#) to back up your data.


## CentOS 7: The hostname changes from uppercase to lowercase letters after the instance is restarted? {#section_qcx_jvc_dhb .section}

-   **Issue**: After an ECS instance is restarted for the first time, the hostname \(hostname\) of some CentOS 7 instances is changed from uppercase letters to lowercase letters.
-   **Image and solution**: See [EN-US\_TP\_136127.md\#](intl.en-US//Image FAQ/Why does the hostname of my CentOS image change from uppercase to lowercase letters after I restart the instance?.md#)

## Aliyun Linux 2: Enabling the CONFIG\_PARAVIRT\_SPINLOCK kernel feature causes performance issues. {#section_nnm_3mw_fhb .section}

-   **Issue**: After you enable the `CONFIG_PARAVIRT_SPINLOCK` kernel feature, application performance is significantly impacted if there are a large number of vCPUs in an ECS instance and lock contentions in applications. For example, performance of the Nginx application is degraded in terms of short connection processing.
-   **Image**: Aliyun Linux 2
-   **Solution**: We recommend that you do not enable the `CONFIG_PARAVIRT_SPINLOCK` kernel feature for Aliyun Linux 2 \(disabled by default\).

## Aliyun Linux 2: Setting the THP switch to always impacts system stability and causes performance issues. {#section_mrx_xnw_fhb .section}

-   **Issue**: After you set the Transparent Hugepage \(THP\) switch in your production environment to always, the system becomes unstable and performance is noticeably degraded.
-   **Image**: Aliyun Linux 2
-   **Solution**: Set the THP switch to `madvise`. In outlier scenarios \(for example, if you run one or some performance benchmark test suites\), although performance is impacted if this switch is set to `madvise`, we recommend that you do so to prevent the system from being impacted by other contentions.

## Aliyun Linux 2: A delegation conflict occurred in NFS v4.0. {#section_mmx_qrw_fhb .section}

-   **Issue**: A delegation conflict occurred in NFS v4.0. For more information, see [Delegation in NFS Version 4](https://docs.oracle.com/cd/E19253-01/816-4555/rfsrefer-140/index.html).
-   **Image**: Aliyun Linux 2
-   **Solution**: We recommend that you do not enable the Delegation feature when you use NFS v4.0. For information on how to disable this feature at the server side, see [How to Select Different Versions of NFS on a Server](https://docs.oracle.com/cd/E19253-01/816-4555/rfsadmin-965/index.html).

## Aliyun Linux 2: NFS v4.1/4.2 has a defect that may cause logout failure of applications. {#section_w35_dyw_fhb .section}

NFS versions 4.1 and 4.2 have a defect that causes logout failure of applications.

-   **Issue**: In NFS v4.1 or v4.2, if you use Asynchronous I/O \(AIO\) in applications to distribute requests, and close the corresponding file descriptors before all I/Os are returned, a live lock may be triggered and the corresponding process cannot be ended.
-   **Image**: Aliyun Linux 2
-   **Solution**: An update to resolve this kernel issue is in development. Alibaba Cloud have also submitted a comprehensive bug report to the official [Kernel Community](https://marc.info/?l=linux-nfs&m=155134860713098&w=2).

## Aliyun Linux 2: System performance is impacted when the Meltdown or Spectre vulnerability is fixed. {#section_a2j_d4y_ghb .section}

-   **Issue**: In the kernel of Aliyun Linux 2, the repair of high-risk security vulnerabilities in processor hardware is enabled by default, which impacts system performance. As a result, performance degradation may be recorded performance benchmark test suites.
-   **Image**: Aliyun Linux 2
-   **Solution**: We recommend that in normal circumstances you do not disable the repair function. However, if you need to maximize system performance, you can run the following command to disable the repair function:

    ```
    # Add nopti nospectre_v2 to the kernel startup parameters.
    sudo sed -i 's/\(GRUB_CMDLINE_LINUX=".*\)"/\1 nopti nospectre_v2/' /etc/default/grub
    sudo grub2-mkconfig -o /boot/grub2/grub.cfg
    # Restart the system.
    sudo reboot
    ```


