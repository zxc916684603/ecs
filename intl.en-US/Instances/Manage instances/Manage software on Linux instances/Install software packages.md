# Install software packages {#concept_423126 .concept}

After you add software repositories, you can use the package management tool of the Linux system to install the packages you need. This topic uses Apache HTTP Server in Alibaba Cloud repositories as an example to describe how to install software packages on different Linux distributions.

## Prerequisites {#section_s5d_zmd_gna .section}

You have added the repositories of software packages before you install them. You must add Alibaba Cloud repositories before following the steps in the examples below. For more information about how to add repositories, see [Add software repositories](intl.en-US/Instances/Manage instances/Manage software on Linux instances/Add software repositories.md#).

## Install software packages on CentOS {#section_r6b_reg_izm .section}

1.  Connect to a Linux instance. For more information, see [Connect to a Linux instance](intl.en-US/Instances/Connect to instances/Overview.md#section_fjm_rgx_wdb).
2.  Run the following command to install software packages.

    ``` {#codeblock_cv0_8og_cwk}
    yum install <package> # Replace <package> with the software package you want to install.
    ```

    For example, to install Apache HTTP Server, run the following command.

    ``` {#codeblock_1w0_nc2_lbi}
    yum install httpd
    ```


## Install software packages on Debian or Ubuntu {#section_kkn_27t_923 .section}

1.  Connect to a Linux instance. For more information, see [Connect to a Linux instance](intl.en-US/Instances/Connect to instances/Overview.md#section_fjm_rgx_wdb).
2.  Run the following command to install software packages.

    ``` {#codeblock_pau_svk_x1r}
    # apt-get update
    # apt-get install <package> # Replace <package> with the software package you want to install.
    ```

    For example, to install Apache HTTP Server, run the following command.

    ``` {#codeblock_8vd_tb0_fxt}
    # apt-get update
    # apt-get install apache2
    ```


## Install software packages on openSUSE {#section_fcz_7dx_zyb .section}

1.  Connect to a Linux instance. For more information, see [Connect to a Linux instance](intl.en-US/Instances/Connect to instances/Overview.md#section_fjm_rgx_wdb).
2.  Run the following command to install software packages.

    ``` {#codeblock_h0c_a83_rdr}
    zypper install <package> # Replace <package> with the software package you want to install.
    ```

    For example, to install Apache HTTP Server, run the following command.

    ``` {#codeblock_q2b_jwq_xxo}
    zypper install apache2
    ```


