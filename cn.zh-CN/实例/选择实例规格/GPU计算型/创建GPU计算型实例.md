# 创建GPU计算型实例 {#concept_g5s_g2z_xdb .concept}

GPU计算型实例必须安装GPU驱动才可以使用。您可以在创建实例时自动安装GPU驱动，也可以在实例创建后手动安装GPU驱动。本文介绍如何创建GPU计算型实例并自动安装驱动。

## 注意事项 {#section_urs_qd1_ydb .section}

如果您使用了自动安装GPU驱动功能，请注意：

-   自动安装只支持Linux公共镜像。
-   自动安装过程受不同实例规格的内网带宽和CPU核数的影响，安装时间约4～10分钟，在安装过程中无法使用GPU，请勿对实例进行任何操作，也不要安装其它GPU相关软件，以防自动安装失败，导致实例不可用。
-   如果您在创建完成后[更换操作系统](cn.zh-CN/镜像/更换操作系统.md#) ，请确保使用同一镜像或者为[可自动安装CUDA和GPU驱动的镜像](cn.zh-CN/实例/选择实例规格/GPU计算型/创建GPU计算型实例.md#section_gbb_nxz_xdb)，以防自动安装失败。
-   您可以[远程连接实例](cn.zh-CN/实例/连接实例/连接方式导航.md#)，通过安装日志查看安装进程和结果：
    -   如果您勾选了**自动安装GPU驱动**，安装日志位于/root/nvidia\_install.log。
    -   如果您在**实例自定义数据**配置nvidia\_install\_v2.0版本的安装脚本，安装日志位于/root/nvidia/nvidia\_install.log。

## 操作步骤 {#section_v1b_nxz_xdb .section}

本步骤重点介绍GPU计算型实例相关的配置，您可以参见[创建ECS实例](cn.zh-CN/实例/创建实例/使用向导创建实例.md#)了解其它通用配置。

1.  前往[ECS售卖页](https://ecs-buy.aliyun.com/wizard/#/)。
2.  完成基础配置。在选择配置时，请注意：
    -   **地域**：请根据表格[提供GPU计算型实例的地域和可用区](cn.zh-CN/实例/选择实例规格/GPU计算型/创建GPU计算型实例.md#section_e2n_pnb_ygb)选择地域和可用区。如果售卖页显示的地域和可用区和表格不一致，以售卖页为准。
    -   **实例**：定位到**异构计算GPU/FPGA** \> **GPU计算型**，然后根据需求选择实例规格。
    -   **镜像**：部分Linux**公共镜像**支持自动安装CUDA和GPU驱动，支持的镜像请参见[支持自动安装的镜像](cn.zh-CN/实例/选择实例规格/GPU计算型/创建GPU计算型实例.md#section_gbb_nxz_xdb)。

        如果您选择的镜像支持自动安装驱动，勾选**自动安装GPU驱动**，并选择驱动版本。如果是新业务系统，建议选择最新的版本。

        如果您不勾选**自动安装GPU驱动**，或者镜像不支持自动安装，则需要在**实例自定义数据**模块下配置安装脚本，或者在创建实例后[手动安装GPU驱动](cn.zh-CN/实例/选择实例规格/GPU计算型/手动安装GPU驱动.md#)。如何配置安装脚本，请参见[脚本版本](cn.zh-CN/实例/选择实例规格/GPU计算型/创建GPU计算型实例.md#section_xcj_1s5_xgb)。

        **说明：** 如果调用[RunInstances](../../../../cn.zh-CN/API参考/实例/RunInstances.md#)创建GPU计算型实例，必须通过UserData参数上传安装脚本，脚本内容需要采用Base64方式编码。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9632/155960265139823_zh-CN.png)

3.  完成网络和安全组配置。在选择配置时，请注意：
    -   **网络**：选择**专有网络**。
    -   **公网带宽**：请根据您的业务需要选择带宽。

        **说明：** 如果您在**基础配置**中选用了Windows 2008 R2及以下版本的镜像，在GPU驱动安装生效后，您将无法通过[管理终端](cn.zh-CN/实例/连接实例/连接Linux实例/使用管理终端连接Linux实例.md#)连接GPU计算型实例，远程连接时会始终显示黑屏或停留在启动界面。您需要在此处勾选**分配公网IP地址**，或者在创建实例后[绑定弹性公网IP](../../../../cn.zh-CN/用户指南/绑定云资源.md#)，以便通过其他协议连接实例，例如RDP（Windows自带的远程连接）、PCOIP、XenDeskop HDX 3D等。其中RDP不支持DirectX、OpenGL等应用，您需要自行安装VNC服务和客户端。

4.  完成系统配置。在选择配置时，请注意：
    -   **登录凭证**：建议选择**密钥对**或**自定义密码**。如果您选择**创建后设置**，通过管理终端登录实例时必须绑定SSH密钥对或者重置密码，然后重启实例使修改生效。如果此时GPU驱动尚未安装完成，重启操作会导致安装失败。
    -   **实例自定义数据**：
        -   如果您在基础配置页面的**镜像**中选择了**自动安装GPU驱动**，此处会显示自动安装CUDA和GPU驱动的注意事项和Shell脚本内容。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9632/155960265139825_zh-CN.png)

        -   如果您未选择**自动安装GPU驱动**，可以在**实例自定义数据**处配置安装脚本，脚本示例请参见[实例自定义数据方式安装脚本](cn.zh-CN/实例/选择实例规格/GPU计算型/创建GPU计算型实例.md#section_bl2_k23_ygb)。
5.  根据需要完成分组设置并确认订单，完成创建GPU计算型实例。

    **说明：** 

    -   如果您配置了自动安装脚本，实例启动后会自动安装GPU驱动。安装完成后实例会自动重启，重启过后GPU驱动才能正常工作。
    -   GPU驱动在Persistence Mode下工作更稳定。安装脚本会自动开启GPU驱动的Persistence Mode，并将该设置添加到Linux系统的自启动脚本中，确保实例重启后还能默认开启Persistence Mode。

## 提供GPU计算型实例的地域和可用区 {#section_e2n_pnb_ygb .section}

提供各GPU计算型实例规格族的地域和可用区如下表所示：

|实例规格|地域和可用区|
|----|------|
|gn4| -   华北2（可用区A）、华东2（可用区B）
-   华南1（可用区C）

 |
|gn5| -   华北2（可用区C、E）、华北5（可用区A）
-   华东1（可用区G、F）、华东2（可用区D、B、E）
-   华南1（可用区D）
-   香港（可用区C、B）
-   亚太东南1（可用区B、A）、亚太东南2（可用区A）、亚太东南3（可用区A）、亚太东南5（可用区A）
-   美国西部1（可用区B、A）、美国东部1（可用区B、A）
-   欧洲中部1（可用区A）

 |
|gn5（部署NGC环境）|部分地域下的gn5实例不支持部署NGC（NVIDIA GPU CLOUD）环境，更多信息请参见[在gn5实例上部署NGC环境](../../../../cn.zh-CN/最佳实践/GPU实例最佳实践/在gn5实例上部署NGC环境.md#)。|
|gn5i| -   华北2（可用区C、E、A）
-   华东1（可用区B）、华东2（可用区D、B）
-   华南1（可用区A）

 |
|gn6v|华东2（可用区F）|

## 支持自动安装的镜像 {#section_gbb_nxz_xdb .section}

支持自动安装CUDA和GPU驱动的镜像如下：

|镜像来源|镜像版本|
|----|----|
|公共镜像|支持如下版本： -   CentOS 64位（目前提供的所有版本都支持）
-   Ubuntu16.04 64位镜像
-   SUSE Linux Enterprise Server 12 SP2 64位镜像

 |
|镜像市场|请按以下方式获取： -   搜索**NVIDIA**并选择需要的镜像，目前只支持CentOS 7.3。
-   如果GPU计算型实例用于深度学习，您可以选择预装深度学习框架的镜像。搜索**深度学习**并选择需要的镜像，目前只支持CentOS 7.3。

 |

## 脚本版本 {#section_xcj_1s5_xgb .section}

实例首次启动时，cloud-init会自动执行Shell脚本安装CUDA和GPU驱动。

-   如果您勾选了**自动安装GPU驱动**，实例会使用安装脚本的nvidia\_install\_v1.0版本。目前，可选的CUDA和GPU驱动版本如下：

    |CUDA|GPU驱动|支持的实例规格|
    |----|-----|-------|
    |9.1.85|390.46|     -   gn5
    -   gn5i
    -   gn6v
    -   gn4
 |
    |9.0.176|     -   390.46
    -   384.125
    -   384.111
 |     -   gn5
    -   gn5i
    -   gn6v
    -   gn4
 |
    |8.0.61|     -   390.46
    -   384.125
    -   384.111
 |     -   gn5
    -   gn5i
    -   gn4
 |

-   如果您在**实例自定义数据**配置安装脚本，建议使用安装脚本的nvidia\_install\_v2.0版本，脚本内容请参见[实例自定义数据方式安装脚本](cn.zh-CN/实例/选择实例规格/GPU计算型/创建GPU计算型实例.md#section_bl2_k23_ygb)。nvidia\_install\_v2.0版本具有以下优势：

    -   提供最新版本的CUDA、GPU驱动和cuDNN库。
    -   登录实例后，如果正在安装驱动，您可以看到安装进度条。如果已经安装成功，您可以看到安装结果提示**NVIDIA INSTALL OK**；如果安装失败，您将看到安装结果提示**NVIDIA INSTALL FAIL**。
    使用nvidia\_install\_v2.0版本时，您需要修改安装脚本的以下参数，指定GPU驱动、CUDA、cuDNN版本号，例如：

    ``` {#codeblock_wlb_x4q_tou}
    driver_version="410.79"
    cuda_version="9.0.176"
    cudnn_version="7.4.2"
    ```

    目前支持的CUDA、GPU驱动和cuDNN库版本如下：

    |CUDA|GPU驱动|cuDNN|
    |----|-----|-----|
    |10.0.130|410.79|     -   7.4.2
    -   7.3.1
 |
    |9.2.148|     -   410.79
    -   396.44
 |     -   7.4.2
    -   7.3.1
    -   7.1.4
 |
    |9.0.176|     -   410.79
    -   396.44
    -   390.46
 |     -   7.4.2
    -   7.3.1
    -   7.1.4
    -   7.0.5
 |
    |8.0.61|     -   410.79
    -   396.44
    -   390.46
 |     -   7.1.3
    -   7.0.5
 |


## 实例自定义数据方式安装脚本 {#section_bl2_k23_ygb .section}

通过**实例自定义数据**方式安装驱动时，建议使用安装脚本的nvidia\_install\_v2.0版本，脚本内容如下：

``` {#codeblock_g4y_yfd_0oo}
#!/bin/sh

driver_version=$1
cuda_version=$2
cudnn_version=$3

NVIDIA_DIR="/root/nvidia"
log=${NVIDIA_DIR}"/nvidia_install.log"
PROCESS_NAME="/var/lib/cloud/instance/scripts/part-001"
DRIVER_PROCESS_NAME=${NVIDIA_DIR}"/NVIDIA-Linux-x86_64"
CUDA_PROCESS_NAME=${NVIDIA_DIR}"/cuda"
CUDNN_PROCESS_NAME=${NVIDIA_DIR}"/cudnn"
DOWNLOAD_PROCESS_NAME="wget"
SUCCESS_STR="NVIDIA INSTALL OK"
DOWNLOAD_SUCCESS_STR="Download OK"

DRIVER_FAIL_STR="Driver INSTALL FAIL"
CUDA_FAIL_STR="CUDA INSTALL FAIL"
CUDNN_FAIL_STR="CUDNN INSTALL FAIL"
DOWNLOAD_FAIL_STR="Download FAIL"

install_notes="The script automatically downloads and installs a NVIDIA GPU driver and CUDA/CUDNN library.
1. The installation takes 6 to 10 minutes, depending on the intranet bandwidth and the quantity of vCPU cores of the instance. Please do not operate the GPU or install any GPU-related software until the GPU driver is installed successfully.
2. After the GPU is installed successfully, the instance will restarts automatically."

check_install()
{
    b=''
    if [ "$1" = "NVIDIA" ]; then
        ProcessName=$DRIVER_PROCESS_NAME
        t=2
    elif [ "$1" = "cuda" ]; then
        ProcessName=$CUDA_PROCESS_NAME
        t=2.5
    elif [ "$1" = "cudnn" ]; then
        ProcessName=$CUDNN_PROCESS_NAME
        t=0.5
    fi
    i=0
    while true
    do
        pid_num=$(ps -ef | grep $ProcessName |grep -v grep | wc -l)
        if [ $pid_num -eq 0 ]; then
            str=$(printf "%-100s" "#")
            b=$(echo "$str" | sed 's/ /#/g')
            printf "| %-100s | %d%% \r\n" "$b" "100";
            break
        fi
        i=$(($i+1))
        str=$(printf "%-${i}s" "#")
        b=$(echo "$str" | sed 's/ /#/g')
        printf "| %-100s | %d%% \r" "$b" "$i";
        sleep $t
    done
    echo
    return 0
}

check_download()
{
    name=$1
    i=0
    b=''
    filesize=0
    percent=0

    sleep 0.5
    while true
    do
        pid_num=$(ps -ef | grep wget |grep $name |grep -v grep | wc -l)
        if [ $pid_num -eq 0 ]; then
            filesize=$(du -sk /root/nvidia/${name}* | awk '{print $1}')
            str=$(printf "%-100s" "#")
            b=$(echo "$str" | sed 's/ /#/g')
            printf "%-8s| %-100s | %d%% \r\n" "${filesize}K" "$b" "100";
            break
        fi
        line=$(tail -2 /root/nvidia/nvidia_install.log)
        filesize=$(echo $line | awk -F ' ' '{print $1}')
        percent=$(echo $line | awk -F '%' '{print $1}' | awk -F ' ' '{print $NF}')
        if [ "$percent" -ge 0 ] 2>/dev/null ;then
           str=$(printf "%-${percent}s" "#")
           b=$(echo "$str" | sed 's/ /#/g')
           printf "%-8s| %-100s | %d%% \r" "${filesize}" "$b" "$percent";
        else
            continue
        fi
        sleep 0.5

    done
    return 0
}

check_install_log()
{
    if [ ! -f "$log" ];then
        echo "NVIDIA install log $log not exist! Install may fail!"
        echo
        exit 1
    fi

    if [ "$1" = "NVIDIA" ]; then
        succstr=$SUCCESS_STR
        str2=$(cat $log |grep "INSTALL_ERROR")
        echo
        if [ -n "$succstr" ] && [ -z "$str2" ]; then
            echo "$succstr !!"
            echo
            return 0
        else
            echo "NVIDIA install may have some INSTALL_ERROR, please check log $log !"
            return 1
        fi
    fi

    if [ "$1" = "DRIVER" ]; then
        failstr=$DRIVER_FAIL_STR
    elif [ "$1" = "CUDA" ]; then
        failstr=$CUDA_FAIL_STR
    elif [ "$1" = "CUDNN" ]; then
        failstr=$CUDNN_FAIL_STR
    fi
    str1=$(cat $log |grep "$failstr")
    if [ -n "$str1" ] ;then
        echo
        echo "NVIDIA $failstr ! please check install log $log !"
        return 1
    fi
}

check_install_process()
{
    echo "CHECKING NVIDIA INSTALL, PLEASE WAIT ......"
    echo "$install_notes"
    echo

    while true
    do
        pid_num=$(ps -ef | grep $PROCESS_NAME |grep -v grep | grep -v check | wc -l)
        if [ $pid_num -eq 0 ];then
            check_install_log "NVIDIA"
            return 0
        else
            pid_num=$(ps -ef | grep $DOWNLOAD_PROCESS_NAME |grep driver |grep -v grep | wc -l)
            if [ $pid_num -gt 0 ];then
                echo "Driver-${1} downloading, need 10 seconds. Remaining installation time 360 - 600 seconds!"
                check_download "NVIDIA" 
            fi

            pid_num=$(ps -ef | grep $DOWNLOAD_PROCESS_NAME |grep cuda |grep -v grep | wc -l)
            if [ $pid_num -gt 0 ];then
                echo "CUDA-${2} downloading, need 150 or more seconds. Remaining installation time 350 - 590 seconds!"
                while true
                do
                    check_download "cuda" 
                    sleep 1
                    pid_num=$(ps -ef | grep $DOWNLOAD_PROCESS_NAME |grep cuda |grep -v grep | wc -l)
                    if [ $pid_num -eq 0 ];then
                        break
                    fi
                done
            fi

            pid_num=$(ps -ef | grep $DOWNLOAD_PROCESS_NAME |grep cudnn |grep -v grep | wc -l)
            if [ $pid_num -gt 0 ];then
                echo "cuDNN-${3} downloading, need about 30 seconds. Remaining installation time 200 - 430 seconds!"
                check_download "cudnn"
            fi

            pid_num=$(ps -ef | grep $DRIVER_PROCESS_NAME |grep -v grep | wc -l)
            if [ $pid_num -gt 0 ];then
                echo
                echo "Driver-${1} installing, need 30 - 160 seconds. Remaining installation time 160 - 400 seconds!"
                check_install "NVIDIA"
                check_install_log "DRIVER"
            fi
            pid_num=$(ps -ef | grep $CUDA_PROCESS_NAME |grep -v grep | wc -l)
            if [ $pid_num -gt 0 ];then
                echo "CUDA-${2} installing, need 80 - 200 seconds. Remaining installation time 90 - 220 seconds!"
                check_install "cuda"
                check_install_log "CUDA"
            fi
            pid_num=$(ps -ef | grep $CUDNN_PROCESS_NAME |grep -v grep | wc -l)
            if [ $pid_num -gt 0 ];then
                echo "cuDNN-${3} installing, need 10 seconds. Installation will be successful soon, please wait......"
                check_install "cudnn"
                check_install_log "CUDNN"
            fi
        fi
        sleep 1
    done
}

create_nvidia_repo_centos()
{
    baseurl_centos=$(cat /etc/yum.repos.d/CentOS-Base.repo |grep baseurl | head -1 | awk -F'[/]' '{print $1"//"$3}')
    if [ -z "$baseurl_centos" ]; then
        url="http://mirrors.cloud.aliyuncs.com"
    fi
    cudaurl=$baseurl_centos"/opsx/ecs/linux/rpm/cuda/${version}/\$basearch/"
    driverurl=$baseurl_centos"/opsx/ecs/linux/rpm/driver/${version}/\$basearch/"
    echo "[ecs-cuda]" > /etc/yum.repos.d/nvidia.repo
    echo "name=ecs cuda - \$basearch" >> /etc/yum.repos.d/nvidia.repo
    echo $cudaurl >> /etc/yum.repos.d/nvidia.repo
    echo "enabled=1" >> /etc/yum.repos.d/nvidia.repo
    echo "gpgcheck=0" >> /etc/yum.repos.d/nvidia.repo
    echo "[ecs-driver]" >> /etc/yum.repos.d/nvidia.repo
    echo "name=ecs driver - \$basearch" >> /etc/yum.repos.d/nvidia.repo
    echo $driverurl >> /etc/yum.repos.d/nvidia.repo
    echo "enabled=1" >> /etc/yum.repos.d/nvidia.repo
    echo "gpgcheck=0" >> /etc/yum.repos.d/nvidia.repo
    yum clean all >> $log 2>&1
    yum makecache >> $log 2>&1
}

disable_nouveau_centos()
{
    echo "blacklist nouveau" > /etc/modprobe.d/blacklist-nouveau.conf
    echo "options nouveau modeset=0" >> /etc/modprobe.d/blacklist-nouveau.conf
    echo "***exec \"dracut --force\" to regenerate the kernel initramfs"
    dracut --force
}

disable_nouveau_ubuntu()
{
    echo "blacklist nouveau" > /etc/modprobe.d/blacklist-nouveau.conf 
    echo "options nouveau modeset=0" >> /etc/modprobe.d/blacklist-nouveau.conf
    echo "***exec \"update-initramfs -u\" to regenerate the kernel initramfs"
    update-initramfs -u
}
install_kernel_centos()
{
    kernel_version=$(uname -r)
    kernel_devel_num=$(rpm -qa | grep kernel-devel | grep $kernel_version | wc -l)
    if [ $kernel_devel_num -eq 0 ];then
        echo "******exec \"yum install -y kernel-devel-$kernel_version\""
        yum install -y kernel-devel-$kernel_version
        if [ $? -ne 0 ]; then
            echo "INSTALL_ERROR: install kernel-devel fail!!!"
            return 1
        fi
    fi
    return 0
}
install_kernel_suse()
{
    kernel_version=$(uname -r|awk -F'-' '{print $1"-"$2}')
    kernel_devel_num=$(rpm -qa | grep kernel-default-devel | wc -l)
    if [ $kernel_devel_num -eq 0 ];then
        echo "***exec \"zypper install -y kernel-default-devel=$kernel_version\""
        zypper install -y kernel-default-devel=$kernel_version
        if [ $? -ne 0 ]; then
            echo "error: install kernel-default-devel fail!!!"
            return 1
        fi
    fi
}
install_kernel_ubuntu()
{
    kernel_version=$(uname -r)
    linux_headers_num=$(dpkg --list |grep linux-headers | grep $kernel_version | wc -l)
    if [ $linux_headers_num -eq 0 ];then
        echo "***exec \"apt-get install -y --allow-unauthenticated linux-headers-$kernel_version\""
        apt-get install -y --allow-unauthenticated linux-headers-$kernel_version
        if [ $? -ne 0 ]; then
            echo "error: install linux-headers fail!!!"
            return 1
        fi
    fi
}

download()
{
    download_url="${baseurl}/opsx/ecs/linux/binary/nvidia"
    wget ${download_url}/driver/${driver_file}
    if [ $? -ne 0 ]; then
        echo "INSTALL_ERROR: Download driver fail!!! return: $?"
        return 1
    fi

    cudafilelist=$(curl ${download_url}/cuda/${cuda_version}/ |grep "cuda_${cuda_version}" | awk -F '>' '{print $2}' | awk -F '<' '{print $1}')
    if [ -z "$cudafilelist" ]; then
        echo "INSTALL_ERROR: Download CUDA fail!!! get cuda-${cuda_version} filename fail!!"
        return 1
    fi

    mkdir /root/nvidia/cuda
    cd /root/nvidia/cuda
    echo $cudafilelist
    for cudafile in $cudafilelist
    do
        sleep 1
        wget ${download_url}/cuda/${cuda_version}/$cudafile
        if [ $? -ne 0 ]; then
            echo "INSTALL_ERROR: Download CUDA fail!!! wget $cudafile fail! return: $?"
            return 1
        fi
    done
    chmod +x /root/nvidia/cuda/*

    cd /root/nvidia
    wget ${download_url}/cudnn/${cuda_big_version}/${cudnn_file}
    if [ $? -ne 0 ]; then
        echo "INSTALL_ERROR: Download cuDNN fail!!! return :$?"
        return 1
    fi
    chmod +x /root/nvidia/*
    echo "$DOWNLOAD_SUCCESS_STR !"
    return 0
}

install_driver()
{
    /root/nvidia/$driver_file --silent
    if [ $? -ne 0 ]; then
        echo "INSTALL_ERROR: driver install fail!!!"
        return 1
    fi
    echo "$DRIVER_SUCCESS_STR !"
    return 0
}

install_cuda()
{
    cd /root/nvidia/cuda
    cuda_file=$(ls -S | grep cuda | grep $cuda_version | head -1)
    echo "cuda file: "$cuda_file
    if [ -z "$cuda_file" ]
    then
        echo "INSTALL_ERROR: cuda file is null, cuda install fail!!!"
        return 1
    fi

    /root/nvidia/cuda/$cuda_file --silent --toolkit --samples --samplespath=/root
    if [ $? -ne 0 ]; then
        echo "INSTALL_ERROR: cuda install fail!!!"
        return 1
    fi

    cuda_patchfile=$(ls | grep cuda | grep $cuda_version | grep -v ${cuda_file})
    for cuda_patch in $cuda_patchfile
    do
        echo "install cuda patch file: "$cuda_patch
        /root/nvidia/cuda/$cuda_patch --silent --installdir=/usr/local/cuda --accept-eula
        if [ $? -ne 0 ]; then
            echo "INSTALL_ERROR: cuda patch install fail!!!"
            return 1
        fi
    done
    echo "$CUDA_SUCCESS_STR !"
    return 0
}

install_cudnn()
{
    tar zxvf /root/nvidia/$cudnn_file -C /usr/local
    if [ $? -ne 0 ]; then
        echo "INSTALL_ERROR: CUDNN INSTALL FAIL !!!"
        return 1
    fi
    echo "$CUDNN_SUCCESS_STR !"
    return 0
}

enable_pm()
{
    echo "#!/bin/bash" > /etc/init.d/enable_pm.sh
    echo "nvidia-smi -pm 1" >> /etc/init.d/enable_pm.sh
    echo "exit 0" >> /etc/init.d/enable_pm.sh

    chmod +x /etc/init.d/enable_pm.sh

    str=$(tail -1 $filename |grep "exit")
    if [ -z "$str" ]; then
        echo "/etc/init.d/enable_pm.sh" >> $filename
    else
        sed -i '$i\/etc/init.d/enable_pm.sh' $filename
    fi
    chmod +x $filename
}

issue=$(cat /etc/issue | grep Ubuntu)
if [ -n "$issue" ];then
    os="ubuntu"
    profile_file="/root/.profile"
    filename="/etc/rc.local"

else
    issue=$(cat /etc/issue | grep SUSE)
    if [ -n "$issue" ];then
        os="suse"
        filename="/etc/init.d/after.local"
    else
        os="centos"
        filename="/etc/rc.d/rc.local"
    fi
    profile_file="/root/.bash_profile"
fi

if [ "$1" = "check" ];then
    check_install_process $driver_version $cuda_version $cudnn_version
    sed -i '/part-001 /d' $profile_file
    exit 0
else
    mkdir $NVIDIA_DIR

    echo "begin to install, driver: $driver_version, cuda: $cuda_version, cudnn: $cudnn_version " >> $log 2>&1
    driver_file="NVIDIA-Linux-x86_64-"${driver_version}".run"
    cuda_big_version=$(echo $cuda_version | awk -F'.' '{print $1"."$2}')
    cudnn_file="cudnn-"${cuda_big_version}"-linux-x64-v"${cudnn_version}".tgz"

    echo "sh /var/lib/cloud/instance/scripts/part-001 check" | tee -a $profile_file
fi
echo "os:$os" >> $log 2>&1
if [ "$os" = "ubuntu" ]; then
    disable_nouveau_ubuntu >> $log 2>&1
    if [ -f "/etc/apt/sources.list.d/sources-aliyun-0.list" ]; then
        repo_file="/etc/apt/sources.list.d/sources-aliyun-0.list"
    else
        repo_file="/etc/apt/sources.list"
    fi

    baseurl=$(cat $repo_file |grep "^deb" | head -1 | awk -F'[/]' '{print $1"//"$3}' |awk -F ' ' '{print $2}')
    if [ -z "$baseurl" ]; then
        baseurl="http://mirrors.cloud.aliyuncs.com"
    fi
elif [ "$os" = "suse" ]; then
    baseurl=$(cat /etc/zypp/repos.d/SLES12-SP2-0.repo |grep baseurl | head -1| awk -F'[=/]' '{print $2"//"$4}')
    if [ -z "$baseurl" ]; then
        baseurl="http://mirrors.cloud.aliyuncs.com"
    fi
elif [ "$os" = "centos" ]; then
    baseurl=$(cat /etc/yum.repos.d/CentOS-Base.repo |grep baseurl | head -1 | awk -F'[/]' '{print $1"//"$3}' |awk -F '=' '{print $2}')
    if [ -z "$url" ]; then
        baseurl="http://mirrors.cloud.aliyuncs.com"
    fi

    if [ ! -f "/usr/bin/lsb_release" ]; then
       pkgname=$(yum provides /usr/bin/lsb_release |grep centos|grep x86_64 |head -1 |awk -F: '{print $1}')
       if [ -z "$pkgname" ]; then
           echo "INSTALL_ERROR: /usr/bin/lsb_release pkg not exists!" >> $log 2>&1
           exit 1
       fi
       yum install -y $pkgname >> $log 2>&1
    fi
    if [ ! -f "/usr/bin/gcc" ]; then
        yum install -y gcc
    fi


    disable_nouveau_centos >> $log 2>&1
    str=$(lsb_release -r | awk -F'[:.]' '{print $2}')
    version=$(echo $str | sed 's/ //g')
    create_nvidia_repo_centos
fi

install_kernel_${os} >> $log 2>&1
if [ $? -ne 0 ]; then
    echo "INSTALL_ERROR: kernel-devel install fail!!!" >> $log 2>&1
    exit 1
fi

cd /root/nvidia

begin_download=$(date '+%s')
download >> $log 2>&1
if [ $? -ne 0 ]; then
    exit 1
fi
end_download=$(date '+%s')
time_download=$((end_download-begin_download))
echo "NVIDIA download OK! Using time $time_download s !!" >> $log 2>&1

begin=$(date '+%s')
install_driver >> $log 2>&1
if [ $? -ne 0 ]; then
    exit 1
fi
end=$(date '+%s')
time_install=$((end-begin))
echo "NVIDIA install driver OK! Using time $time_install s !!" >> $log 2>&1

begin=$(date '+%s')
install_cuda >> $log 2>&1
if [ $? -ne 0 ]; then
    exit 1
fi
end=$(date '+%s')
time_install=$((end-begin))
echo "NVIDIA install cuda OK! Using time $time_install s !!"  >> $log 2>&1

begin=$(date '+%s')
install_cudnn >> $log 2>&1
if [ $? -ne 0 ]; then
    exit 1
fi
end=$(date '+%s')
time_install=$((end-begin))
echo "NVIDIA install cudnn OK! Using time $time_install s !!" >> $log 2>&1
enable_pm
echo "reboot......" >> $log 2>&1
sleep 2
reboot
```

## 相关文档 {#section_o3f_dch_ygb .section}

-   如果在创建实例时没有安装GPU驱动，则必须在创建后手动安装。具体操作，请参见[手动安装GPU驱动](cn.zh-CN/实例/选择实例规格/GPU计算型/手动安装GPU驱动.md#)。
-   如果gn5、gn5i、gn6v、vgn5i或gn6i实例需要支持OpenGL图形显示，必须安装GRID驱动，具体操作，请参见[在GPU计算型实例中安装GRID驱动](../../../../cn.zh-CN/实例/选择实例规格/GPU计算型/在GPU计算型实例中安装GRID驱动.md#)。
-   您可以手动卸载GPU驱动和CUDA，具体操作请参见[从GPU计算型实例中卸载GPU驱动](cn.zh-CN/实例/选择实例规格/GPU计算型/手动卸载GPU驱动.md#)。
-   您可以通过云监控控制台或API查看GPU监控数据，具体操作请参见[GPU监控](../../../../cn.zh-CN/用户指南/主机监控/GPU监控.md#)。

