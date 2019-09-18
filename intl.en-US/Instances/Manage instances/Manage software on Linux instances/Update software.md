# Update software {#concept_490666 .concept}

The software packages in Linux distributions are constantly updated to add new functions, bug fixes, and security updates. You can update software to the latest version based on business requirements. This topic describes how to update a specific software application or all applications on different Linux distributions.

## Prerequisites {#section_m25_02y_uyi .section}

You have added the repository of software packages before you update the applications. For more information about adding software repositories, see [Add software repositories](intl.en-US/Instances/Manage instances/Manage software on Linux instances/Add software repositories.md#).

## Update software on CentOS {#section_qt5_pyl_5nf .section}

1.  Connect to a Linux instance. For more information, see [Connect to a Linux instance](intl.en-US/Instances/Connect to instances/Overview.md#section_fjm_rgx_wdb).
2.  Update software applications.

    -   To update a software application, run the following command.

        ``` {#codeblock_2xb_wx4_eia}
        yum update <package> # Replace <package> with the software application you want to update.
        ```

        For example, to update Apache HTTP Server, run the following command:

        ``` {#codeblock_wpi_acd_z39}
        yum update httpd
        ```

    -   To update all software applications in the system, run the following command.

        **Note:** 

        If you run this command, the update process may update the kernel of the operating system and cause some issues. For example, the system may not start up or certain software applications may be incompatible with the updated kernel. Therefore, before you run this command, we recommend that you configure the system to skip kernel changes while applying updates.

        ``` {#codeblock_1n3_vol_7c2}
        yum update
        ```

    After updating a software application, you can check its version. If it is the latest version, the software application has been updated.


## Update software applications on Ubuntu or Debian {#section_cwn_ggl_tcp .section}

1.  Connect to a Linux instance. For more information, see [Connect to a Linux instance](intl.en-US/Instances/Connect to instances/Overview.md#section_fjm_rgx_wdb).
2.  Run the following command to obtain a list of software packages that need to be updated.

    ``` {#codeblock_g4l_exz_e3u}
    apt-get update
    ```

3.  Update software applications.

    -   To update a software application, run the following command.

        ``` {#codeblock_l5l_7ap_xd0}
        apt-get install <package> # Replace <package> with the software application you want to update.
        ```

        For example, to update Python, run the following command:

        ``` {#codeblock_qnr_4gx_jm6}
        apt-get install python
        ```

    -   To update all software applications in the system, run the following command.

        **Note:** 

        If you run this command, the update process may update the kernel of the operating system and cause some issues. For example, the system may not start up or certain software applications may be incompatible with the updated kernel. Therefore, before you run this command, we recommend that you configure the system to skip kernel changes while applying updates.

        ``` {#codeblock_ion_1sa_d7u}
        apt-get upgrade
        ```

    After updating a software application, you can check its version. If it is the latest version, the software application has been updated.


## Update software on openSUSE {#section_z7q_iac_71i .section}

1.  Connect to a Linux instance. For more information, see [Connect to a Linux instance](intl.en-US/Instances/Connect to instances/Overview.md#section_fjm_rgx_wdb).
2.  Run the following command to obtain a list of software packages that need to be updated.

    ``` {#codeblock_wak_asj_0ge}
    zypper list-updates
    ```

3.  Update software applications.

    -   To update a software application, run the following command.

        ``` {#codeblock_a56_l7t_0aw}
        zypper update <package> # Replace <package> with the software application you want to update.
        ```

        For example, to update Python, run the following command.

        ``` {#codeblock_a9w_y91_24b}
        zypper update python
        ```

    -   To update all software applications in the system, run the following command.

        **Note:** 

        If you run this command, the update process may update the kernel of the operating system and cause some issues. For example, the system may not start up or certain software applications may be incompatible with the updated kernel. Therefore, before you run this command, we recommend that you configure the system to skip kernel changes while applying updates.

        ``` {#codeblock_f3o_8ag_al8}
        zypper update
        ```

    After updating a software application, you can check its version. If it is the latest version, the software application has been updated.


