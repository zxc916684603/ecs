# 使用f1 RTL {#concept_n5c_vt3_dfb .task}

本文介绍如何使用f1 RTL（Register Transfer Level）。

在开始本教程之前，请确保您已完成下列操作：

-   已创建f1实例并且实例能访问公网。

    **说明：** f1实例只能使用镜像市场的FaaS F1基础镜像。更多详情，请参见[创建f1实例](../cn.zh-CN/实例/选择实例规格/FPGA计算型/创建f1实例.md)。

-   已在f1实例使用的安全组中添加规则放行SSH（22）端口。具体操作，请参见[添加安全组规则](../cn.zh-CN/安全/安全组/添加安全组规则.md#)。
-   已在[ECS管理控制台](https://ecs.console.aliyun.com/#/home)f1实例详情页上获取实例ID。
-   已开通OSS服务并创建一个OSS Bucket用于上传您的文件。Bucket与f1实例必须属于同一个账号、同一个地域。具体操作，请参见[创建一个OSS Bucket](../../../../../cn.zh-CN/快速入门/创建存储空间.md)。
-   如果需要加密服务，您还需要开通密钥管理服务。具体操作，请参见[开通密钥管理服务（KMS）](../../../../../cn.zh-CN/快速入门/入门概述.md#)。
-   若使用RAM用户操作FPGA，必须完成以下操作：
    -   [创建RAM用户](../../../../../cn.zh-CN/快速入门/（隐藏）旧版快速入门/创建 RAM 用户.md)并[授权](../../../../../cn.zh-CN/快速入门/（隐藏）旧版快速入门/为 RAM 用户授权.md)。
    -   [创建RAM角色](../../../../../cn.zh-CN/用户指南/（隐藏）旧版用户指南/身份管理/角色.md)并[授权](../../../../../cn.zh-CN/用户指南/（隐藏）旧版用户指南/授权管理/授权.md)。
    -   获取AccessKey ID和AccessKey Secret。
-   使用本教程进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm?)。

在开始本教程之前，请阅读以下注意事项：

-   本教程中所有操作都必须由同一个账号在同一地域里执行。
-   强烈建议您使用RAM用户操作FaaS实例。为了防止意外操作，您需要让RAM用户仅执行必要的操作。在操作FPGA镜像及下载时，因为您需要从指定的OSS Bucket下载原始DCP工程，所以您必须为FaaS管理账号创建一个角色，并授予临时权限，让FaaS管理账号访问指定的OSS Bucket。如果需要对IP加密，必须授予RAM用户KMS相关权限。如果需要做权限检查，必须授予查看用户资源的权限。

1.  远程连接f1实例。具体操作，请参见[远程连接Linux实例](../cn.zh-CN/实例/连接实例/连接Linux实例/使用用户名密码验证连接Linux实例.md)。
2.  运行以下命令配置基础环境。 

    ``` {#codeblock_kt7_58r_m1g}
    source /opt/dcp1_1/script/f1_env_set.sh
    ```

3.  依次运行以下命令编译工程。 

    ``` {#codeblock_y5z_5oq_rw3}
    cd /opt/dcp1_1/hw/samples/dma_afu
    ```

    ``` {#codeblock_47g_9ig_3g8}
    afu_synth_setup --source hw/rtl/filelist.txt build_synth
    ```

    ``` {#codeblock_3tu_g1q_lb5}
    cd build_synth/
    ```

    ``` {#codeblock_l0w_pfo_vq3}
    run.sh
    ```

    **说明：** 编译时间较长，请耐心等待。

4.  制作镜像。 
    1.  依次运行以下命令配置`PATH`环境变量并为faascmd文件添加可执行权限。 

        ``` {#codeblock_01b_pc8_gus}
        export PATH=$PATH:/opt/dcp1_1/script/
        ```

        ``` {#codeblock_ikr_fxw_3s0}
        chmod +x /opt/dcp1_1/script/faascmd
        ```

    2.  依次运行以下命令初始化faascmd配置。 

        ``` {#codeblock_2pq_ale_lba}
        # 将hereIsYourSecretId替换为您的AccessKey ID，hereIsYourSecretKey替换为您的AccessKey Secret
        faascmd config --id=hereIsYourSecretId --key=hereIsYourSecretKey
        ```

        ``` {#codeblock_o6c_n8q_9k5}
        # 将hereIsYourBucket换为华东1地域里OSS Bucket名称
        faascmd auth --bucket=hereIsYourBucket
        ```

    3.  在/opt/dcp1\_1/hw/samples/dma\_afu目录下，运行以下命令上传gbs文件。 

        ``` {#codeblock_l1j_8et_48q}
        faascmd upload_object --object=dma_afu.gbs --file=dma_afu.gbs
        ```

    4.  运行以下命令制作镜像。 

        ``` {#codeblock_20n_31j_876}
        # 将hereIsYourImageName替换为您的镜像名称
        faascmd create_image --object=dma_afu.gbs --fpgatype=intel --name=hereIsYourImageName --tags=hereIsYourImageTag --encrypted=false --shell=V1.1
        ```

5.  下载镜像。 
    1.  运行以下命令查看镜像是否制作成功。 

        ``` {#codeblock_hgz_091_p9o}
        faascmd list_images
        ```

        返回结果里，如果出现`"State":"success"`，表示镜像制作成功。请记录返回结果里显示的FpgaImageUUID的值，稍后会用到。

        ![download_image](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9828/156768003912086_zh-CN.png)

    2.  运行以下命令获取FPGA ID。 

        ``` {#codeblock_aiw_8p9_azh}
        # 将hereIsYourInstanceId替换为您的f1实例ID
        faascmd list_instances --instanceId=hereIsYourInstanceId
        ```

        返回结果如下图所示。请记录FpgaUUID的值。

        ![get_fpga-id](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9828/156768003912087_zh-CN.png)

    3.  运行以下命令下载FPGA镜像到f1实例。 

        ``` {#codeblock_o6m_nit_2q8}
        # 将hereIsYourInstanceID替换为刚刚保存的实例ID；将hereIsFpgaUUID替换为上一条命令中记下的FpgaUUID；将hereIsImageUUID替换为上一步记下FpgaImageUUID
        faascmd download_image --instanceId=hereIsYourInstanceID --fpgauuid=hereIsFpgaUUID --fpgatype=intel --imageuuid=hereIsImageUUID --imagetype=afu --shell=V1.1
        ```

    4.  运行以下命令检查镜像是否下载成功。 

        ``` {#codeblock_0sz_huk_w3v}
        # 将hereIsYourInstanceID替换为刚刚保存的实例ID；将hereIsFpgaUUID替换为上一条命令中记下的FpgaUUID
        faascmd fpga_status --instanceId=hereIsYourInstanceID --fpgauuid=hereIsFpgaUUID
        ```

        如果返回结果中出现`"TaskStatus":"operating"`，且FpgaImageUUID的值和下载镜像时FpgaImageUUID的值一致，说明下载成功。

        ![download_success](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9828/156768003912088_zh-CN.png)

6.  依次运行以下命令测试。 

    ``` {#codeblock_dih_y51_mo5}
    cd /opt/dcp1_1/hw/samples/dma_afu/sw
    ```

    ``` {#codeblock_jty_5n7_ys6}
    make
    ```

    ``` {#codeblock_u9f_9jx_j0p}
    sudo LD_LIBRARY_PATH=/opt/dcp1_1/hw/samples/dma_afu/sw:$LD_LIBRARY_PATH ./fpga_dma_test 0
    ```

    **说明：** 如果没有开启Huge pages，运行以下命令启用Huge pages。

    ``` {#codeblock_q1h_rgv_5hj}
    sudo bash -c "echo 20 > /sys/kernel/mm/hugepages/hugepages-2048kB/nr_hugepages"
    ```

    输出结果如下图所示，说明测试完成。

    ![test_complete](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9828/156768003912089_zh-CN.png)


