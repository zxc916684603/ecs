# Use OpenCL on an f3 instance {#concept_d3c_4sl_2fb .concept}

This article introduces how to use Open Computing Language \(OpenCL\) to create an image, and then download the image to an FPGA chip.

**Note:** 

-   All the operations described in this article must be performed by one account in the same region.
-   We recommend that you use an f3 instance as a RAM user. You must create a role for the RAM user and grant temporary permissions to the role to access the OSS buckets.

## Prerequisites {#section_j5c_ctl_2fb .section}

-   [Create an f3 instance](../../../../reseller.en-US/User Guide/Instances/Create an instance/Create an f3 instance.md).

    **Note:** 

    -   Only the image we share with you can be used on an f3 instance.
    -   Select Assign public IP when creating an instance, so that the instance can access the Internet.
    -   The security group of the f3 instance has added the rule for allowing access to the SSH \(22\) port.
-   Log on to the ECS console and obtain the instance ID of your f3 instance.
-   Creat an OSS Bucket in the same region as your f3 instance by using the same account. For details, see Sign up for OSS and [Create a bucket](../../../../reseller.en-US/Quick Start/Create a bucket.md).
-   To operate FPGA as a RAM user, do the following in advance:
    -    [Create a RAM user](../../../../reseller.en-US/Quick Start/Create a RAM user.md) and [attach policies to a RAM user](../../../../reseller.en-US/Quick Start/Attach policies to a RAM user.md).
    -    [Create a RAM user](../../../../reseller.en-US/User Guide/Identities/Role.md) and [attach policies to a RAM user](../../../../reseller.en-US/User Guide/Authorization/Authorization.md).
    -   Create an AccessKey.

## Procedure {#section_eyg_ltl_2fb .section}

To create an image by using OpenCL on an f3 instance and download it to an FPGA chip, follow these steps.

## Step 1. Set up the environment {#section_wvk_ntl_2fb .section}

To set up the environment, follow these steps.

1.  [Connect to an f3 instance](../../../../reseller.en-US/User Guide/Connect to instances/Connect to a Linux instance by using a password.md).
2.  Run the command below to open the installation script. Add `#` to line 5 to comment out `unset XILINX_SDX` and then save the file.

    ```
    vim /root/xbinst_oem/setup.sh
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924563912149_en-US.png)

3.  Run the command to install Screen.

    ```
    yum install screen -y
    ```

4.  Run the command to open a new screen.

    ```
    screen -S f3opencl
    ```

5.  Run the command to set up a secured environment to download a file.

    ```
    source /root/xbinst_oem/f3_env_setup.sh xocl
    ```


## Step 2. Compile a binary file {#section_qcn_vtl_2fb .section}

To compile a binary file, follow these steps.

1.  Run the command to change the directory.

    ```
    cd /opt/Xilinx/SDx/2017.4.op/examples/vadd
    ```

2.  Run the `cat sdaccel.mk | grep "XDEVICE="` command to check the configuration of the `XDEVICE` parameter. Make sure it is set to `xilinx_aliyun-f3_dynamic_5_0`.
3.  Run the `vim` command to modify the `common.mk` file.

    ```
    vim ../common/common.mk
    ```

    Replace Line 63 \(parameters may be in lines 60 - 62, depending on the file\):

    ```
    CLCC_OPT += $(CLCC_OPT_LEVEL) ${DEVICE_REPO_OPT} --platform ${XDEVICE} -o ${XCLBIN} ${KERNEL_DEFS} ${KERNEL_INCS}
    ```

    with

    ```
    CLCC_OPT += $(CLCC_OPT_LEVEL) ${DEVICE_REPO_OPT} --platform ${XDEVICE} -o ${XCLBIN} ${KERNEL_DEFS} ${KERNEL_INCS} --xp param:compiler.acceleratorBinaryContent=dcp
    ```

4.  Run the command to compile the program.

    ```
    
    export XILINX_SDX=/opt/Xilinx/SDx/2017.4.op
    make -f sdaccel.mk xbin_hw
    ```

    If the following information is displayed, the compilation of the binary file has started. The process may take several hours. Please be patient.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924563912150_en-US.png)


## Step 3:  Check the packaging script {#section_rjl_d5l_2fb .section}

Run the command to check whether the packaging script exists or not.

```
file /root/xbinst_oem/sdaccel_package.sh
```

If the returned message contains `cannot open (No such file or directory)`, the file does not exist. You need to download the script by running the following command.

```
wget http://fpga-tools.oss-cn-shanghai.aliyuncs.com/sdaccel_package.sh
```

## Step 4:  Create an image {#section_h1l_g5l_2fb .section}

To create an image, follow these steps.

1.  Run the command to set up the OSS environment.

    ```
    
    # Replace hereIsMySecretId, hereIsMySecretKey and hereIsMyBucket with your AccessKeyID, AccessKeySecret and Bucket name
    faascmd config --id=hereIsMySecretId --key=hereIsMySecretKey 
    Faascmd auth -- bucket = maid
    ```

2.  Run the `ls`command to obtain the file name suffixed by`.xclbin`.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924563912152_en-US.png)

3.  Run the command to package the binary file.

    ```
    /root/xbinst_oem/sdaccel_package.sh -xclbin=/opt/Xilinx/SDx/2017.4.op/examples/vadd/bin_vadd_hw.xclbin
    ```

    After the packaging is completed, you get a packaged file in the same directory, as shown below.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924563912154_en-US.png)


## Step 5:  Create an image {#section_ft5_k5l_2fb .section}

You can use a scripted process or step by step process to upload the package file and download the FPGA image.

-   Scripted process: Only applicable to f3 instances with one FPGA card.
    1.  Run the command to upload the packaged file and create an image.

        ```
        sh /root/xbinst_oem/tool/faas_upload_and_create_image.sh 
        ```

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924564012155_en-US.png)

    2.  Download the image file.

        ```
        sh  /root/xbinst_oem/tool/faas_download_image.sh <bit.tar.gz - the packaged file> 0 # The last number is the FPGA serial No. of the instance
        ```

        **Note:** 0 indicates the first FPGA of the f3 instance. For single-FPGA instances, the FPGA serial No. is always 0. For instances with multiple FPGAs, such as an instance with four FPGAs, the serial No. are 0, 1, 2 and 3.

        To download the same image to multiple FPGAs, add the serial No. to the end:

        ```
        sh faas_download_image.sh bit.tar.gz 0 1 2
        ```

-   Step by step process:
    1.  Run the command to upload the package to your OSS Bucket. Then, upload gbs in your OSS Bucket to the OSS Bucket in the FaaS administrative unit.

        ```
        
        faascmd upload_object --object=bit.tar.gz --file=bit.tar.gz
        faascmd create_image --object=bit.tar.gz --fpgatype=xilinx --name=hereIsFPGAImageName --tags=hereIsFPGAImageTag --encrypted=false --shell=f30001
        upload_object
        ```

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924564012156_en-US.png)

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924564012157_en-US.png)

    2.  Run the command to view if the FPGA image is downloadable.

        ```
        faascmd list_images
        ```

        If the returned message shows `"State":"success"`, the FPGA image is ready for downloading. Find FpgaImageUUID and note it down.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924564012158_en-US.png)

    3.  Run the command to find and note down FpgaUUID in the returned message.

        ```
        faascmd list_instances --instanceId=hereIsYourInstanceId # Replace hereIsYourInstanceId with the f3 instance ID
        ```

    4.  Run the command to download the FPGA image.

        ```
        
        faascmd download_image --instanceId=hereIsYourInstanceId --fpgauuid=hereIsFpgaUUID --fpgatype=xilinx --imageuuid=hereIsImageUUID --imagetype=afu --shell=f30001
        # Replace hereIsYourInstanceId with the f3 instance ID, hereIsFpgaUUID with the FpgaUUID, and hereIsImageUUID with the FpgaImageUUID
        ```

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924564012164_en-US.png)

    5.  Run the command to view if the image is downloaded successfully.

        ```
        faascmd fpga_status --fpgauuid=hereIsFpgaUUID --instanceId=hereIsYourInstanceId # Replace hereIsFpgaUUID with the FpgaUUID, and hereIsYourInstanceId with the f3 instance ID.
        ```

        Below is an example of the returned message. If the FpgaImageUUID in the message is the same as the FpgaImageUUID you note down and the message shows `"TaskStatus":"valid"`, the image is downloaded successfully.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21515/153924564012170_en-US.png)


## Step 6:  Run the Host program {#section_tft_w5l_2fb .section}

Run the commands to execute the Host program.

```

make -f sdaccel.mk host
unset XILINX_SDX
./vadd bin_vadd_hw.xclbin
```

If `Test Passed` is returned, the test is successful.

## Other common commands {#section_ltf_z5l_2fb .section}

In this section, some common commands for an FPGA instance are introduced.

|Task|Command|
|:---|:------|
|View the help document|`make -f ./sdaccel.mk help`|
|Run software simulation|`Make-F./sdaccel. mk maid`|
|Run hardware simulation|`make -f ./sdaccel.mk run_hw_em`|
|Compile the host code only|`make -f ./sdaccel.mk host`|
|Compile and generate files for downloading|`make -f sdaccel.mk xbin_hw`|
|Clear a job directory|`make -f sdaccel.mk clean`|
|Force clear a job directory|`make -f sdaccel.mk cleanall`|

**Note:** During simulation, follow the Xilinx simulation process. You do not need to set up the F3\_env\_setup environment.

