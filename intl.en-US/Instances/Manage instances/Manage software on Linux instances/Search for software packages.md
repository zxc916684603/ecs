# Search for software packages {#concept_422833 .concept}

If you want to install a software application but do not know the name of the software package, you can use the tools in the Linux system to search for the package. This topic describes the commands that you can use to search for software packages and how to use these commands on different Linux distributions.

## Search for software packages on CentOS {#section_4j5_c1g_f9c .section}

-   Command

    ``` {#codeblock_n1e_2cc_fs8}
     yum search [keywords of software packages]
    ```

-   Examples
    -   Example 1: Search for two software applications with the keywords "rz" and "sz".

        Run the following command to search for the software packages to which the two applications belong.

        ``` {#codeblock_466_8n4_ji6}
        yum search sz rz
        ```

        The command result indicates that these two software applications belong to the `lrzsz.x86_64` package, as shown in the following figure. After you install the package, you can use the `lrz` and `lsz` software applications.

        ![sz_rz](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/341803/156877918648376_en-US.png)

    -   Example 2: Search for a software application by using the keyword "mysql-community-server".

        Run the following command to search for the software package to which the application belongs.

        ``` {#codeblock_5qd_jxp_u7u}
         yum search mysql-community-server
        ```

        The command result indicates the package to which the software application belongs, as shown in the following figure.

        ![mysql](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/341803/156877918648384_en-US.png)

        **Note:** If you cannot find the mysql-community-server package in the CentOS operating system, it may be because you have not added the repository of the software package. For more information about how to add the required software repository, and install and use MySQL Server, see [Use MySQL on ECS](../../../../intl.en-US/.md#).


## Search for software packages on Debian or Ubuntu {#section_8nm_gyb_l0h .section}

-   Command

    ``` {#codeblock_x83_6of_dmn}
      apt-cache search [keywords of software packages]
    ```

-   Examples
    -   Example 1: Search for software packages relating to Web servers.

        Run the following command to search for the software packages.

        ``` {#codeblock_fxs_9le_dmr}
        apt-cache search "web server"
        ```

        The command result indicates that apache2 is the software package of the Web server, as shown in the following figure.

        ![web-server](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/341803/156877918648441_en-US.png)

    -   Example 2: Search for Java development environment by using the keyword "openjdk".

        Run the following command to search for "openjdk".

        ``` {#codeblock_yfc_h9o_30i}
        apt-cache search openjdk
        ```

        The command result shows the software packages relating to openjdk, as shown in the following figure.

        ![openjdk](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/341803/156877918648443_en-US.png)


## Next steps {#section_4tt_nsh_hgz .section}

After you find the software packages, you may need to install them. For more information about how to install software packages, see [Install software packages](intl.en-US/Instances/Manage instances/Manage software on Linux instances/Install software packages.md#).

