# Convert image file format {#concept_obj_qpm_xdb .concept}

Only image files in RAW or VHD format can be imported. If you want to import images in other formats, convert the format before importing the image. This tutorial describes how to use qemu-img tool to converts custom image file format

such as RAW, Qcow2, VMDK, VDI, VHD \(vpc\), VHDX, qcow1, or QED to vhd or raw format.

## Install qemu-img {#section_bwj_zpm_xdb .section}

You can use different methods to install qemu-img and convert the image file format based on operating system of your computer:

-   [Windows operationg system](#windows)
-   [Linux operationg system](#linux)

**Windows operationg system**

Follow these steps to install qemu-IMG and convert the image file format:

1.  Download and install qemu from [https://qemu.weilnetz.de/w64/](https://qemu.weilnetz.de/w64/). Installation path: C:\\Program Files\\qemu.
2.  Perform the following to create an environment variable \(For Windows 7\):
    1.  Choose **Start** \> **Computer**, right click **properties**.
    2.  In the left-side navigation pane, click **Advanced system settings**.
    3.  In the **System Properties** dialog box, click the **Advanced** tab and click **Environment Variables**.

        ![](images/4624_en-US.png)

    4.  In the  Environment Variables dialog box, in the **System variables**, find the **Path** variable, and click  **Edit**. If the **Path** variable does not exist, click **New**.

        ![](images/4626_en-US.png)

    5.  Add a variable value:
    -   In the **Edit System Variable**: In the **Variable** value, add C:\\Program Files\\qemu. Different variable values are separated with semicolon \(;\).

        ![](images/4627_en-US.png)

    -   In the **New System Variable**: In the **Variable** name,   enter Path. In the **Variable** value, enter C:\\Program Files\\qemu.

        ![](images/4629_en-US.png)

3.  Open **Command** Prompt in Windows and run the qemu-img --help command. If it is displayed successfully, the installation was successful.
4.  In the **Command** prompt, run the cd \[directory of the source image file\] command to change the directory. For example, `cd D:\ConvertImage`.
5.  In **Command** prompt, run the `qemu-img convert -f raw -O qcow2 centos.raw centos.qcow2` command to convert the image file format.

    The command parameters are described as follows:

    -   -f is followed by the source image format.
    -   -O \(uppercase is required\) is followed by the converted image format, the source file name, and the target file name.

When the conversion is complete, the target file appears in the directory where the source image file is located.

**Linux operationg system**

To install qemu-img and convert the image file format, follow these steps:

1.  Install qemu-img, for example:
    -   For Ubuntu, run the command: `apt install qemu-img`.
    -   For CentOS, run the command: `yum install qemu-img`.
2.  Run the `qemu-img convert -f raw -O qcow2 centos.raw centos.qcow2` command to convert the image file format.

    The command parameters are described as follows:

    -   -f is followed by the source image format.
    -   -O \(uppercase is required\) is followed by the converted image format, the source file name, and the target file name.

