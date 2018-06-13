# Notes for importing custom images {#concept_d53_2jm_xdb .concept}

To guarantee the usability of an imported image to improve the efficiency of importing an image, pay attention to the followings before importing an image. Depending on the operating system of the custom image, the notes vary for [Linux operating systems](#linux) and [Windows operationg systems](#windows).

## Linux operating systems {#linux .section}

**Restrictions**

When importing a Linux image, considering the following:

-   Does not support multiple network interfaces.
-   IPv6 address is not allowed.
-   The password must be 8 to 30 characters in length. It must contain uppercase and lowercase letters, numbers, and special symbols.
-   You must install the XEN and KVM virtualization platform drivers.
-   The firewall is disabled, and port 22 is enabled by default.
-   DHCP must be enabled in the image.
-   We recommend that you [Install cloud-init](intl.en-US/User Guide/Images/Import images/Install cloud-init.md#) to guarantee the successful configuration of Hostname, NTP, and Yum sources.

**Notes**

If you want to import a Linux image, you must pay attention to the notes listed in the table.

|Item|Standard operating system|Non-standard platform Mirroring|
|Definition|The official distribution editions of operating systems supported by Alibaba Cloud, includes:-   Alibaba Cloud
-   CentOS 5,6,7
-   CoreOS 681.2.0+
-   Debian 6,7
-   Freebag
-   OpenSUSE 13.1
-   Redhat
-   SUSE Linux 10,11,12
-   Ubuntu 10,12,13,14

|The non-standard operating system refers to either of the followings:-   The operating system that are not included in the list of operating systems that are currently supported by ECS.
-   A standard operating system that fails to comply with the requirements for a standard operating system in terms of critical system configuration files, system basic environment, and applications.

If you want to use an image of a non-standard operating system, you are only allowed to choose:-   Customized Linux: set-up edition mirror. If you import an image of this type of operating system, Alibaba Cloud conducts necessary network or password configuration according to the pre-defined configuration norms. For more information, see [Configure Customized Linux images](intl.en-US/User Guide/Images/Import images/Configure Customized Linux images.md#).
-   Others Linux: ECS identifies all of these images as other system types. If you import an image of such operating system, Alibaba Cloud does not process any of the created instance. After instance creation is complete, you must connect to the instance by using the  **Connect** feature in the ECS console and then manually configure the IP address, the router, and the password.

|
|System critical Profile| -   Do not modify `/etc/issue*`. If it is modified, the distribution of the system cannot be properly recognized and the system creation fails.
-   Do not modify `/boot/grub/menu.lst`. If it is modified, the system may fail to start up.
-   Do not modify `/etc/fstab`. If it is modified, an exception may occur preventing partitions from being loaded, leading to system startup failure.
-   Do not modify `/etc/shadow` to  **read-only**. If it is modified, the password file cannot be modified and the system startup fails.
-   Do not enable SELinux by modifying `/etc/selinux/config`. If it is modified, the system may fail to start up.

 |Fails to comply with the requirements of a standard operating system.|
|Requirements for system basic environments| -   Do not adjust the partition of the system disk. Currently only a single root partition is supported.
-   Check the remaining space on the system tray to make sure that the system tray is not full.
-   Do not modify critical system files,  such as `/sbin`, `/bin`, `/lib*` or /lib\*.
-   Before importing an image, confirm the integrity of the file system.
-   File system: File systems of xfs, ext3, and ext4 for Linux images are supported. MBR is used.

 |Does not meet standard platform mirroring requirements.|
|Applications|Do not install qemu-ga in an imported image. If it is installed, some of the services that Alibaba Cloud needs may become unavailable.|Does not meet standard platform mirroring requirements|
|File format|Currently, images in RAW and VHD formats are supported, and you can [open a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to apply for importing a qcow2 image.

If you want to import images in other formats,  [Convert image file format](intl.en-US/User Guide/Images/Import images/Convert image file format.md#) before importing the image.  We recommend that you import images in a VHD format,|
|File size|Setting the system disk size when importing an image: We recommend that you configure the system disk size for importing based on the virtual file size \(not the usage\) of the image. The size of the disk for importing must be between 40 GB to 500 GB.|

## Windows operationg systems {#windows .section}

When importing a Windows image, pay attention to the following notes.

**Restrictions**

-   The password must be 8 to 30 characters in length and must contain uppercase and lowercase letters, numbers, and special symbols.
-   The firewall is disabled, and port 3389 is enabled by default.

**Distribution editions of Windows operating system**

You are allowed to import the following distribution editions of Windows operating system:

-   Microsoft Windows Server 2016
-   Microsoft Windows Server 2012 R2 \(standard edition\)
-   Microsoft Windows Server 2012 \(standard edition, data center edition\)
-   Microsoft Windows Server 2008 R2 \(standard edition, data center edition, enterprise edition\)
-   Microsoft Windows Server 2008 \(Standard Edition, Data Center Edition, Enterprise Edition\)
-   Microsoft Windows Server 2003 with Service Pack 1 \(SP1\) \(standard edition, data center edition, enterprise edition\)

**Note:** 

Windows XP, Windows 7 \(both Professional Edition and Enterprise Edition\), Windows 8, and Windows 10 are not supported.

**Requirements on the basic system environment**

-   Supports multi-partition system disks.
-   Check the remaining space on the system tray to make sure that the system tray is not full.
-   Do not modify critical system files.
-   Verify the integrity of the file system before importing.
-   File system: Only NTFS file system and MBR is supported.

**Applications**

Do not install qemu-ga in an imported image. If it is installed, some of the services that Alibaba Cloud needs may become unavailable.

**Size and format**

-   Currently, images in RAW and VHD formats are supported, and you can [open a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to apply for importing a qcow2 image. If you want to import a mirror of another format,  [Convert image file format](intl.en-US/User Guide/Images/Import images/Convert image file format.md#)import it again. We recommend that you import images in a VHD format, Format import mirror.
-   Setting the system disk size when importing an image: We recommend that you configure the system disk size for importing based on the virtual disk size rather than the usage of the image. The size of the disk for importing must be between 40 GB to 500 GB.

