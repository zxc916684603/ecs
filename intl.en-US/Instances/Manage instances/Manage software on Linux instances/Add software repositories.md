# Add software repositories {#concept_405791 .concept}

Software packages for Linux are often stored in software repositories. After you add a repository, you can use the package management tool of the Linux system to search, install, and update the software in the repository. This topic uses Alibaba Cloud repositories as an example to describe how to add repositories on different Linux distributions.

**Note:** Both Alibaba Cloud users and non-users have free access to software repositories of Alibaba Cloud. You can visit the [Alibaba Open Source Mirror Site](https://opsx.alibaba.com/mirror) to obtain the software repository of the Linux distribution.

## Add software repositories on CentOS {#section_sw2_rtz_cs8 .section}

To add a software repository on the CentOS 7 operating system, follow these steps. The operations may vary depending on the version of your operating system.

1.  Connect to a Linux instance. For more information, see [Connect to a Linux instance](intl.en-US/Instances/Connect to instances/Overview.md#section_fjm_rgx_wdb).
2.  Run the following command to back up the original software repository.

    ``` {#codeblock_rtk_wkh_8h4}
    sudo mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
    ```

3.  Run any of the following commands to add a software repository on CentOS 7.

    ``` {#codeblock_27l_2x4_cfs}
    sudo wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
    ```

    ``` {#codeblock_nq6_cij_isz}
    sudo curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
    ```

    **Note:** 

    -   To view the steps of adding Alibaba Cloud repositories on other versions of the CentOS operating system, visit the [Alibaba Open Source Mirror Site](https://opsx.alibaba.com/mirror?lang=zh-CN), find `centos`, and click **Help**.
    -   To add a software repository that is not from Alibaba Cloud, replace the URL of `http://mirrors.aliyun.com/repo/Centos-7.repo` in the commands above with the URL of the software repository that you want to add.
4.  Run the following command to generate a local cache for faster searching and installation of software.

    ``` {#codeblock_f5q_z22_01j}
    sudo yum clean all && sudo yum makecache
    ```

5.  Run the `sudo yum repolist` command to check whether the software repository is added. You will see the following content after you add a software repository of Alibaba Cloud on the CentOS 7 operating system.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/328191/156877916248248_en-US.png)


## Add software repositories on Ubuntu {#section_n68_se1_900 .section}

To add a software repository on the Ubuntu 18.04 operating system, follow these steps. The operations may vary depending on the version of your operating system.

1.  Connect to a Linux instance. For more information, see [Connect to a Linux instance](intl.en-US/Instances/Connect to instances/Overview.md#section_fjm_rgx_wdb).
2.  Run the following command to back up the original software repository.

    ``` {#codeblock_zxl_hyd_q1d}
    sudo cp /etc/apt/sources.list /etc/apt/sources.list.bakup
    ```

3.  Run the sudo vim/etc/apt/sources.list command to open the file. Add the following content to the file. For more information, see [Use the Vim editor](../../../../intl.en-US/Tutorials/Use the Vim editor.md#).

    ``` {#codeblock_iwu_i00_unj}
    deb http://mirrors.cloud.aliyuncs.com/ubuntu/ bionic main restricted universe multiverse
    deb-src http://mirrors.cloud.aliyuncs.com/ubuntu/ bionic main restricted universe multiverse
    deb http://mirrors.cloud.aliyuncs.com/ubuntu/ bionic-security main restricted universe multiverse
    deb-src http://mirrors.cloud.aliyuncs.com/ubuntu/ bionic-security main restricted universe multiverse
    deb http://mirrors.cloud.aliyuncs.com/ubuntu/ bionic-updates main restricted universe multiverse
    deb-src http://mirrors.cloud.aliyuncs.com/ubuntu/ bionic-updates main restricted universe multiverse
    deb http://mirrors.cloud.aliyuncs.com/ubuntu/ bionic-proposed main restricted universe multiverse
    deb-src http://mirrors.cloud.aliyuncs.com/ubuntu/ bionic-proposed main restricted universe multiverse
    deb http://mirrors.cloud.aliyuncs.com/ubuntu/ bionic-backports main restricted universe multiverse
    deb-src http://mirrors.cloud.aliyuncs.com/ubuntu/ bionic-backports main restricted universe multiverse
    ```

    **Note:** 

    -   To view the steps of adding software repositories of Alibaba Cloud on other versions of Ubuntu, visit the [Alibaba Open Source Mirror Site](https://opsx.alibaba.com/mirror?lang=zh-CN), find `ubuntu`, and click **Help**. If you want to add a software repository of Alibaba Cloud on an Elastic Computing Service \(ECS\) instance, replace `http://mirrors.aliyun.com/ubuntu/` in the Help page with `http://mirrors.cloud.aliyuncs.com/ubuntu`. This helps save data transfer costs.
    -   To add a software repository that is not from Alibaba Cloud, replace the added content above with the content of the software repository that you want to add.
4.  Run the `sudo apt-get update` command to update the information about software packages.

## Add software repositories on Debian {#section_4iu_j2p_6da .section}

To add a software repository on the Debian 8.9 operating system, follow these steps. The operations may vary depending on the version of your operating system.

1.  Connect to a Linux instance. For more information, see [Connect to a Linux instance](intl.en-US/Instances/Connect to instances/Overview.md#section_fjm_rgx_wdb).
2.  Run the following command to back up the original software repository.

    ``` {#codeblock_j5l_rgj_xg4}
    sudo cp /etc/apt/sources.list /etc/apt/sources.list.bakup
    ```

3.  Run the sudo vim/etc/apt/sources.list command to open the file. Add the following content to the file. For more information about how to add the content, see [Use the Vim editor](../../../../intl.en-US/Tutorials/Use the Vim editor.md#).

    ``` {#codeblock_bwu_am3_m8n}
    deb http://mirrors.cloud.aliyuncs.com/debian/ jessie main non-free contrib
    deb http://mirrors.cloud.aliyuncs.com/debian/ jessie-proposed-updates main non-free contrib
    deb-src http://mirrors.cloud.aliyuncs.com/debian/ jessie main non-free contrib
    deb-src http://mirrors.cloud.aliyuncs.com/debian/ jessie-proposed-updates main non-free contrib
    ```

    **Note:** 

    -   To view the steps of adding software repositories of Alibaba Cloud on other versions of Debian, visit the [Alibaba Open Source Mirror Site](https://opsx.alibaba.com/mirror?lang=zh-CN), find `debian`, and click **Help**. If you want to add a software repository of Alibaba Cloud on an ECS instance, replace `http://mirrors.aliyun.com/debian/` in the Help page with `http://mirrors.cloud.aliyuncs.com/ubuntu`. This helps save data transfer costs.
    -   To add a software repository that is not from Alibaba Cloud, replace the added content above with the content of the software repository that you want to add.
4.  Run the `sudo apt-get update` command to update the information about software packages.

## Add software repositories on Fedora {#section_zhq_cxs_bvp .section}

1.  Run the following command to back up the original software repository.

    ``` {#codeblock_7bv_p3z_w8u}
    # sudo mv /etc/yum.repos.d/fedora.repo /etc/yum.repos.d/fedora.repo.backup
    # sudo mv /etc/yum.repos.d/fedora-updates.repo /etc/yum.repos.d/fedora-updates.repo.backup
    ```

2.  Run any of the following commands to add software repositories of Alibaba Cloud on Fedora.

    ``` {#codeblock_w9n_g6k_sn8}
    sudo wget -O /etc/yum.repos.d/fedora.repo http://mirrors.aliyun.com/repo/fedora.repo
    ```

    ``` {#codeblock_a86_bob_85o}
    sudo curl -o /etc/yum.repos.d/fedora.repo http://mirrors.aliyun.com/repo/fedora.repo
    ```

    **Note:** To add a software repository that is not from Alibaba Cloud on Fedora, replace the URL of `http://mirrors.aliyun.com/repo/fedora.repo` in the commands with the URL of the software repository that you want add.

3.  Run any of the following commands to add software repositories of Alibaba Cloud on fedora-updates.

    ``` {#codeblock_ds4_72n_ck8}
    sudo wget -O /etc/yum.repos.d/fedora-updates.repo http://mirrors.aliyun.com/repo/fedora-updates.repo
    ```

    ``` {#codeblock_l5n_o7n_mp4}
    sudo curl -o /etc/yum.repos.d/fedora-updates.repo http://mirrors.aliyun.com/repo/fedora-updates.repo
    ```

    **Note:** To add a software repository that is not from Alibaba Cloud on fedora-updates, replace `http://mirrors.aliyun.com/repo/fedora-updates.repo` in the commands with the URL of the software repository that you want.

4.  Run the following command to generate a local cache.

    ``` {#codeblock_t8k_xmv_b5h}
    sudo yum clean all && sudo yum makecache
    ```


## Next steps {#section_img_z0f_hp2 .section}

You can install software packages after you add a software repository. For more information, see [Install software packages](intl.en-US/Instances/Manage instances/Manage software on Linux instances/Install software packages.md#).

