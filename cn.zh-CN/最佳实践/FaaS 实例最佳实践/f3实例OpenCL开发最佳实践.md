# f3实例OpenCL开发最佳实践 {#concept_d3c_4sl_2fb .concept}

本文介绍如何在f3实例上使用OpenCL（Open Computing Language）制作镜像文件，并烧写到FPGA芯片中。

**说明：** 

-   本文所述所有操作都必须由同一个账号在同一地域里执行。
-   建议您使用RAM用户操作FaaS实例。您需要为FaaS管理账号创建一个角色，并授予临时权限，让FaaS管理账号能访问指定的OSS Bucket。

## 前提条件 {#section_j5c_ctl_2fb .section}

-   已[创建f3实例](../../../../intl.zh-CN/用户指南/实例/创建实例/创建f3实例.md)。

    **说明：** 

    -   f3实例只能使用我们共享给您的镜像。
    -   创建实例时选择分配公网IP，确保实例能访问公网。
    -   实例所在安全组中已经添加规则放行SSH（22）端口的访问。
-   已在ECS控制台f3实例的详情页上，获取实例ID。
-   使用同一个账号创建了与f3实例在同一地域的OSS Bucket。详细信息参见开通OSS服务和 [创建一个OSS Bucket](../../../../intl.zh-CN/快速入门/创建存储空间.md)。
-   如果您使用RAM用户操作FPGA，确保已经完成以下操作：
    -    [创建RAM用户](../../../../intl.zh-CN/快速入门/创建 RAM 用户.md)并[授权](../../../../intl.zh-CN/快速入门/为 RAM 用户授权.md)。
    -    [创建RAM角色](../../../../intl.zh-CN/用户指南/身份管理/角色.md)并[授权](../../../../intl.zh-CN/用户指南/授权管理/授权.md)。
    -   获取AccessKey ID和AccessKey Secret。

## 操作步骤 {#section_eyg_ltl_2fb .section}

按以下步骤在f3实例上使用OpenCL制作镜像文件，并烧写到FPGA芯片中。

## 步骤 1. 配置环境 {#section_wvk_ntl_2fb .section}

按以下步骤配置环境：

1.  [远程连接f3实例](../../../../intl.zh-CN/用户指南/连接实例/使用用户名密码验证连接Linux实例.md)。
2.  执行以下命令打开安装脚本，并在第5行前加上`#`，注释掉 `unset XILINX_SDX`，再保存退出。

    ```
    vim /root/xbinst_oem/setup.sh
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924562712149_zh-CN.png)

3.  运行以下命令安装Screen。

    ```
    yum install screen -y
    ```

4.  运行以下命令进入Screen。

    ```
    screen -S f3opencl
    ```

5.  运行以下命令配置安全烧写环境。

    ```
    source /root/xbinst_oem/f3_env_setup.sh xocl
    ```


## 步骤 2. 编译二进制文件 {#section_qcn_vtl_2fb .section}

按以下步骤编译二进制文件：

1.  进入命令目录。

    ```
    cd /opt/Xilinx/SDx/2017.4.op/examples/vadd
    ```

2.  运行命令`cat sdaccel.mk | grep "XDEVICE="`，确保`XDEVICE`配置为 `xilinx_aliyun-f3_dynamic_5_0`。
3.  使用 `vim` 修改 `common.mk` 文件。

    ```
    vim ../common/common.mk
    ```

    将如下所示第 63 行代码（参数可能在 60-62 行，视您的文件而定）

    ```
    CLCC_OPT += $(CLCC_OPT_LEVEL) ${DEVICE_REPO_OPT} --platform ${XDEVICE} -o ${XCLBIN} ${KERNEL_DEFS} ${KERNEL_INCS}
    ```

    修改为：

    ```
    CLCC_OPT += $(CLCC_OPT_LEVEL) ${DEVICE_REPO_OPT} --platform ${XDEVICE} -o ${XCLBIN} ${KERNEL_DEFS} ${KERNEL_INCS} --xp param:compiler.acceleratorBinaryContent=dcp
    ```

4.  运行以下命令编译程序。

    ```
    
    export XILINX_SDX=/opt/Xilinx/SDx/2017.4.op
    make -f sdaccel.mk xbin_hw
    ```

    如果您看到如下界面，说明二进制文件编译已经开始。编译过程可能会持续数个小时，请您耐心等待。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924562712150_zh-CN.png)


## 步骤 3. 检查打包脚本 {#section_rjl_d5l_2fb .section}

运行以下命令检查打包脚本是否存在。

```
file /root/xbinst_oem/sdaccel_package.sh
```

如果返回结果中包含 `cannot open (No such file or directory)`，说明不存在该文件，您需要运行以下命令手动下载打包脚本。

```
wget http://fpga-tools.oss-cn-shanghai.aliyuncs.com/sdaccel_package.sh
```

## 步骤 4. 制作镜像 {#section_h1l_g5l_2fb .section}

按以下步骤制作镜像文件。

1.  运行命令配置OSS环境。

    ```
    
    # 将此处的hereIsMySecretId、hereIsMySecretKey、hereIsMyBucket分别替换为您的AccessKeyID、AccessKeySecret和Bucket名称
    faascmd config --id=hereIsMySecretId --key=hereIsMySecretKey 
    faascmd auth --bucket=hereIsMyBucket
    ```

2.  运行 `ls`，获取后缀为`.xclbin`的文件名。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924562712152_zh-CN.png)

3.  打包二进制文件。

    ```
    /root/xbinst_oem/sdaccel_package.sh -xclbin=/opt/Xilinx/SDx/2017.4.op/examples/vadd/bin_vadd_hw.xclbin
    ```

    打包完成后，在同一目录下，您会看到一个打包好的文件，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924562712154_zh-CN.png)


## 步骤 5. 烧写镜像 {#section_ft5_k5l_2fb .section}

您可以采用脚本化流程或者单步操作流程来上传网表文件，并下载FPGA镜像。

-   脚本化流程：仅适用于配备单块FPGA卡的f3实例。
    1.  运行以下命令上传并生成镜像文件。

        ```
        sh /root/xbinst_oem/tool/faas_upload_and_create_image.sh 
        ```

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924562712155_zh-CN.png)

    2.  下载镜像文件。

        ```
        sh /root/xbinst_oem/tool/faas_download_image.sh  0 # 最后的数字为实例中FPGA的序号
        ```

        **说明：** 0为FaaS实例中的第一个FPGA，单芯片实例序号一律为0，对多芯片实例，例如4芯片的序号为0,1,2,3。

        如果需要对多个FPGA下载同一个镜像，可以在末尾添加序号，例如：

        ```
        sh faas_download_image.sh bit.tar.gz 0 1 2
        ```

-   单步操作流程：
    1.  运行以下命令，将压缩包上传到您个人的OSS Bucket，再将存放在您个人OSS Bucket中的gbs上传到FaaS管理单元的OSS Bucket中。

        ```
        
        faascmd upload_object --object=bit.tar.gz --file=bit.tar.gz
        faascmd create_image --object=bit.tar.gz --fpgatype=xilinx --name=hereIsFPGAImageName --tags=hereIsFPGAImageTag --encrypted=false --shell=f30001
        upload_object示例
        ```

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924562812156_zh-CN.png)

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924562812157_zh-CN.png)

    2.  运行命令查看FPGA镜像是否处于可下载状态。

        ```
        faascmd list_images
        ```

        在返回结果中，如果看到 `"State":"success"`，表示FPGA镜像已经可以下载。找到并记录FpgaImageUUID。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924562812158_zh-CN.png)

    3.  运行以下命令，在返回结果中，找到并记录FpgaUUID。

        ```
        faascmd list_instances --instanceId=hereIsYourInstanceId # 将hereIsYourInstanceId替换为f3实例ID
        ```

    4.  运行以下命令下载FPGA镜像。

        ```
        
        faascmd download_image --instanceId=hereIsYourInstanceId --fpgauuid=hereIsFpgaUUID --fpgatype=xilinx --imageuuid=hereIsImageUUID --imagetype=afu --shell=f30001
        # hereIsYourInstanceId替换为f3的实例ID，hereIsFpgaUUID替换为您获取的FpgaUUID，hereIsImageUUID替换为您获取的FpgaImageUUID
        ```

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924562812164_zh-CN.png)

    5.  运行以下命令查看镜像是否下载成功。

        ```
        faascmd fpga_status --fpgauuid=hereIsFpgaUUID --instanceId=hereIsYourInstanceId # hereIsFpgaUUID替换为您获取的FpgaUUID，hereIsYourInstanceId替换为f3实例ID。
        ```

        以下为返回结果示例。如果显示的FpgaImageUUID与您获取的FpgaImageUUID一致，并且显示 `"TaskStatus":"valid"`，说明镜像下载成功。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924562812170_zh-CN.png)


## 步骤 6. 运行Host程序 {#section_tft_w5l_2fb .section}

执行以下命令运行Host程序。

```

make -f sdaccel.mk host
unset XILINX_SDX
./vadd bin_vadd_hw.xclbin
```

如果返回结果中出现 `Test Passed`，说明测试通过。

## 其他操作 {#section_ltf_z5l_2fb .section}

这里介绍 FPGA 实例部分常用的操作。

|任务|命令|
|:-|:-|
|查看帮助文档|`make -f ./sdaccel.mk help`|
|软件仿真|`make -f ./sdaccel.mk run_cpu_em`|
|硬件仿真|`make -f ./sdaccel.mk run_hw_em`|
|只编译 host 代码|`make -f ./sdaccel.mk host`|
|编译生成可以下载的文件|`make -f sdaccel.mk xbin_hw`|
|清理工作目录|`make -f sdaccel.mk clean`|
|强力清除工作目录|`make -f sdaccel.mk cleanall`|

**说明：** 仿真时只需要按照Xilinx标准流程操作，不需要配置f3\_env\_setup环境。

