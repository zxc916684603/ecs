# 安装virtio驱动 {#concept_dvq_cqs_xdb .task}

为避免部分服务器、虚拟机或者云主机的操作系统在导入自定义镜像后，创建的ECS实例无法启动，您需要在导入镜像前检查是否需要在源服务器中安装virtio驱动。

从本地导入自定义镜像时时，阿里云会自动处理导入的自定义镜像的virtio驱动的操作系统有：

-   Windows Server 2008
-   Windows Server 2012
-   Windows Server 2016
-   CentOS 6/7
-   Ubuntu 12/14/16
-   Debian 7/8/9
-   SUSE 11/12

以上列表的镜像，默认已安装virtio驱动的系统，需要注意修复临时文件系统。具体操作，请参见[修复临时文件系统](#)。

其他不在以上列表的操作系统，您需要在导入镜像之前，为源服务器安装virtio驱动。

## 操作步骤 {#section_7ze_lg6_711 .section}

安装virtio驱动的操作步骤如下：

1.  [步骤一：检查服务器内核是否支持virtio驱动](#Sample)
2.  [步骤二：修复临时文件系统](#RecoverTheInitramfs)
3.  [步骤三：下载内核安装包](#compile)
4.  [步骤四：编译内核](#section_e71_j5s_8ud)

## 步骤一：检查服务器内核是否支持virtio驱动 {#Sample .section}

完成以下操作，检查服务器内核是否支持virtio驱动：

1.  运行`grep -i virtio /boot/config-$(uname -r)`检查当前操作系统的内核是否支持virtio驱动。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9707/15681706604632_zh-CN.png)

    **说明：** 

    -   如果在输出信息中没有找到`VIRTIO_BLK`及`VIRTIO_NET`的信息，表示该操作系统没有安装virtio相关驱动，暂时不能直接导入阿里云云平台。您需要为您的服务器编译安装virtio驱动。
    -   如果参数CONFIG\_VIRTIO\_BLK及CONFIG\_VIRTIO\_NET取值为y，表示包含了virtio驱动，您可以直接导入自定义的镜像到阿里云。详情请参见[导入镜像必读](cn.zh-CN/镜像/自定义镜像/导入镜像/导入镜像必读.md#)和[导入自定义镜像](cn.zh-CN/镜像/自定义镜像/导入镜像/导入自定义镜像.md#)。
    -   如果参数CONFIG\_VIRTIO\_BLK及CONFIG\_VIRTIO\_NET取值为m，需要进入第2步。
2.  执行命令`lsinitrd /boot/initramfs-$(uname -r).img | grep virtio`确认virtio驱动是否包含在临时文件系统initramfs或者initrd中。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9707/15681706604633_zh-CN.png)

    **说明：** 

    -   截图表明，initramfs已经包含了virtio\_blk驱动，以及其所依赖的virtio.ko、virtio\_pci.ko和virtio\_ring.ko，您可以直接导入自定义的镜像到阿里云。详情请参见[导入镜像必读](cn.zh-CN/镜像/自定义镜像/导入镜像/导入镜像必读.md#)和[导入自定义镜像](cn.zh-CN/镜像/自定义镜像/导入镜像/导入自定义镜像.md#)。
    -   如果临时文件系统initramfs没有包含virtio驱动，则需要修复临时文件系统。

## 步骤二：修复临时文件系统 {#RecoverTheInitramfs .section}

通过检查，发现源服务器内核支持virtio驱动，但是临时文件系统initramfs或者initrd中没有包含virtio驱动时，需要修复临时文件系统。以CentOS等为例。

-   CentOS/RedHat 5

    ``` {#codeblock_aou_wel_s38}
    mkinitrd -f --allow-missing \
                --with=xen-vbd  --preload=xen-vbd \
                --with=xen-platform-pci --preload=xen-platform-pci \
                --with=virtio_blk --preload=virtio_blk \
                --with=virtio_pci --preload=virtio_pci \
                --with=virtio_console --preload=virtio_console \
    ```

-   CentOS/RedHat 6/7

    ``` {#codeblock_n3t_swd_lz9}
    mkinitrd -f --allow-missing \
                --with=xen-blkfront --preload=xen-blkfront \
                --with=virtio_blk --preload=virtio_blk \
                --with=virtio_pci --preload=virtio_pci \
                --with=virtio_console --preload=virtio_console \
                /boot/initramfs-$(uname -r).img $(uname -r)
    ```

-   Debian/Ubuntu

    ``` {#codeblock_gev_xpt_l68}
    echo -e 'xen-blkfront\nvirtio_blk\nvirtio_pci\nvirtio_console' >> \
    /etc/initramfs-tools/modules
    mkinitramfs -o /boot/initrd.img-$(uname -r)"
    ```


## 步骤三：下载内核安装包 {#compile .section}

完成以下操作，下载内核安装包：

1.  运行`yum install -y ncurses-devel gcc make wget`安装编译内核的必要组件。
2.  运行`uname -r`查询当前系统使用的内核版本，如示例中的4.4.24-2.a17.x86\_64。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9707/15681706604634_zh-CN.png)

3.  前往[Linux内核列表页面](https://www.kernel.org/pub/linux/kernel/)下载对应的内核版本源码，如示例中的4.4.24开头的linux-4.4.24.tar.gz的网址为 [https://www.kernel.org/pub/linux/kernel/v4.x/linux-4.4.24.tar.gz](https://www.kernel.org/pub/linux/kernel/v4.x/linux-4.4.24.tar.gz)。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9707/15681706604638_zh-CN.png)

4.  运行`cd /usr/src/`切换目录。
5.  运行`wget https://www.kernel.org/pub/linux/kernel/v4.x/linux-4.4.24.tar.gz`下载安装包。
6.  运行`tar -xzf linux-4.4.24.tar.gz`解压安装包。
7.  运行`ln -s linux-4.4.24 linux`建立链接。
8.  运行`cd /usr/src/linux`切换目录。

## 步骤四：编译内核 {#section_e71_j5s_8ud .section}

完成以下操作，编译内核：

1.  依次运行以下命令编译内核。 

    ``` {#codeblock_chg_ubi_n6r}
    make mrproper
    symvers_path=$(find /usr/src/ -name "Module.symvers")
    test -f $symvers_path && cp $symvers_path .
    cp /boot/config-$(uname -r) ./.config
    make menuconfig
    ```

2.  出现以下界面时，开始打开virtio相关配置： 

    **说明：** 选\*配置表示编译到内核，选m配置表示编译为模块。

    1.  使用空格勾选Virtualization项。 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9707/15681706604639_zh-CN.png)

        确认是否勾选了KVM（Kernel-based Virtual Machine）选项。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9707/15681706604640_zh-CN.png)

        ``` {#codeblock_9mw_1fe_aw9}
        Processor type and features  --->
           [*] Paravirtualized guest support  --->
             --- Paravirtualized guest support
         (128)   Maximum allowed size of a domain in gigabytes
         [*]   KVM paravirtualized clock
         [*]   KVM Guest support
        ```

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9707/15681706614641_zh-CN.png)

        ``` {#codeblock_k5s_jkk_wle}
        Device Drivers  --->
          [*] Block devices  --->
         <M>   Virtio block driver (EXPERIMENTAL)
         -*- Network device support  --->
             <M>   Virtio network driver (EXPERIMENTAL)
        ```

    2.  按下Esc键退出内核配置界面并根据弹窗提示保存.config文件。
    3.  检查virtio相关配置是否已经正确配置。详情请参见[步骤一：检查服务器内核是否支持virtio驱动](#Sample)。
    4.  若检查后发现暂未设置virtio相关配置，运行以下命令手动编辑.config文件。 

        ``` {#codeblock_1in_s7t_ulj}
        make oldconfig
        make prepare
        make scripts
        make
        make install
        ```

    5.  运行以下命令查看virtio驱动的安装情况。 

        ``` {#codeblock_jmy_wik_per}
        find /lib/modules/"$(uname -r)"/ -name "virtio.*" | grep -E "virtio.*"
        grep -E "virtio.*" < /lib/modules/"$(uname -r)"/modules.builtin
        ```

        如果任一命令输出virtio\_blk、virtio\_pci.virtio\_console等文件列表，表明您已经正确安装了virtio驱动。


检查virtio驱动后，您可以：

-   [使用迁云工具迁移服务器至阿里云](../../../../cn.zh-CN/迁移服务/P2V 迁云工具/使用迁云工具迁移服务器至阿里云.md#)。
-   [导入自定义镜像](cn.zh-CN/镜像/自定义镜像/导入镜像/导入自定义镜像.md#)。

