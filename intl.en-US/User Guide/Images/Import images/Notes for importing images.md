# Notes for importing images {#concept_d53_2jm_xdb .concept}

To guarantee the usability of an imported image and improve the importing efficiency, pay attention to the following before importing an image:

Depending on the operating system, the notes vary for [Windows images](#) and [Linux images](#).

## Windows images {#windows .section}

**Important suggestions**

-   Verify the integrity of the file system before importing images for Windows.
-   Check the remaining space on the system disk to make sure the system disk is not full.
-   Disable the firewall and allow access to RDP port 3389.
-   The logon password for the administrator account must be 8-30 characters long and must contain uppercase/lowercase letters, numbers, and special characters simultaneously. The special characters can be: \( \) \` ~ ! @ \# $ % ^ & \* - + = | \{ \} \[ \] : ; ‘ < \> , . ? /
-   Configure the system disk size for the importing based on the virtual disk size rather than the usage of the image. The size of the disk for the importing must be from 40 GiB to 500 GiB.
-   Do not modify critical system files.

**What is supported**

-   Multi-partition system disks.
-   NTFS file systems and MBR partitions.
-   Images in RAW, qcow2, or VHD format.

    **Note:** If you want to import an image in another format, [convert image file format](intl.en-US/User Guide/Images/Import images/Convert image file format.md#) before importing it. It is recommended that you convert the format to VHD, which features smaller transmission capacity.

-   Images with the following operating system versions can be imported:
    -   Microsoft Windows Server 2016
    -   Microsoft Windows Server 2012 R2 \(standard edition\)
    -   Microsoft Windows Server 2012 \(standard edition and data center edition\)
    -   Microsoft Windows Server 2008 R2 \(standard edition, data center edition, and enterprise edition\)
    -   Microsoft Windows Server 2008 \(standard edition, data center edition, and enterprise edition\)
    -   Microsoft Windows Server 2003 with Service Pack 1 \(SP1\) \(standard edition, data center edition, and enterprise edition\) or higher

**What is not supported**

-   The installation of qemu-ga in an image is not supported. Otherwise, some services needed by ECS may become unavailable.
-   Windows XP, Windows 7 \(professional and enterprise editions\), Windows 8, and Windows 10.

## Linux images {#linux .section}

**Important suggestions**

-   Verify the integrity of the file system before importing images for Linux.
-   Check the remaining space on the system disk to make sure that the system disk is not full.
-   Disable the firewall and allow access to TCP port 22.
-   Install the virtualization platform XEN or KVM drives.
-   It is recommended to [install cloud-init](intl.en-US/User Guide/Images/Import images/Install cloud-init for Linux images.md#), so as to guarantee that hostname, NTP, and yum sources can be configured successfully.
-   Dynamic Host Configuration Protocol \(DHCP\) needs to be enabled.
-   The logon password for the root account must be 8-30 characters long and must contain uppercase/lowercase letters, numbers, and special characters simultaneously. The special characters can be: \( \) \` ~ ! @ \# $ % ^ & \* - + = | \{ \} \[ \] : ; ‘ < \> , . ? /
-   Do not modify critical system files, such as `/sbin`, `/bin`, and `/lib*`.

**What is supported**

-   Images in RAW, qcow2, or VHD format.

    **Note:** If you want to import an image in another format, [convert image file format](intl.en-US/User Guide/Images/Import images/Convert image file format.md#) before importing it. It is recommended that you convert the format to VHD that features smaller transmission capacity.

-   The xfs, ext3, and ext4 file systems and MBR partitions.

**What is not supported**

-   Multiple network interfaces.
-   IPv6 addresses.
-   System disk partitions cannot be adjusted. Currently, only a single root partition is supported.

**Issues to note**

Depending on whether the Linux system image you are importing is a standard platform image, you need to note different issues.

-   The official operating system releases are defined as the standard platform images. Currently, supported system releases include Aliyun Linux, CentOS 5/6/7, CoreOS 681.2.0+, Debian 6/7, FreeBSD, OpenSUSE 13.1, RedHat, Red Hat Enterprise Linux \(RHEL\), SUSE Linux 10/11/12, and Ubuntu 10/12/13/14.
-   Operating system images that are not in the list of public images provided by ECS are non-standard platform images. Such images, though based on the standard operating system, do not comply with the requirements for a standard operating system regarding critical system configuration files, basic system environments, and applications. If you want to use a non-standard platform image, you can only choose the following when importing an image:
    -   Others Linux: Alibaba Cloud identifies all of these images as other Linux systems. Alibaba Cloud does not handle the instances created if you import an image of Others Linux. If you enable DHCP before creating an image, Alibaba Cloud automatically configures your network. After creating the instance, you need to connect to the instance by using the [**Management Terminal**](intl.en-US/User Guide/Connect to instances/Connect to an instance by using the Management Terminal.md#) feature in the console, and then manually configure the IP address, router, and password.
    -   Customized Linux: Customized images. After importing a customized Linux image, configure the network and password of the instance according to the standard system configuration mode of Alibaba Cloud. For more information, see [Customize Linux images](intl.en-US/User Guide/Images/Import images/Customize Linux images.md#).

|Item|Standard platform image|Non-standard platform image|
|:---|:----------------------|:--------------------------|
|Requirements for critical system configuration files| -   Do not modify `/etc/issue*`. Otherwise, ECS cannot properly identify the system release, leading to system creation failure.
-   Do not modify `/boot/grub/menu.lst`, or the ECS instance cannot be started.
-   Do not modify `/etc/fstab`, or the exception partition cannot be loaded, leading to ECS instance start failure.
-   Do not change `/etc/shadow` to **read only**, or you may be unable to modify the password file, leading to system creation failure.
-   Do not enable SELinux by modifying `/etc/selinux/config`, or the system may fail to start.

 |Does not meet the requirements of standard platform images|
|Requirements for applications|Do not install qemu-ga in an imported image, or some services required by Alibaba Cloud may become unavailable.|Does not meet the requirements of standard platform images|

