# Install cloud-init {#concept_e3k_vnm_xdb .concept}

If you need to create ECS instances by using existing images, you can importing them to Alibaba Cloud ECS. To guarantee the successful configuration of the hostname, NTP source, and yum source of the imported image, we recommend that you install cloud-init in your on-premise server, virtual machine, or cloud host before importing an image.

## Limits {#section_bw3_b4m_xdb .section}

-   Currently, cloud-init supports the Linux distributions of CentOS, Debian, Fedora, FreeBSD, Gentoo,  RHEL \(Red Hat Enterprise Linux\), SLES \(SUSE Linux Enterprise Server\), and Ubuntu.

-   The AliYun datasource support is present in cloud-init since 0.7.9. If your on-premise server, virtual machine, or cloud host already has cloud-init installed, make sure that the version is later than 0.7.9.

    1.  Connect to your on-premise server, virtual machine or cloud host.
    2.  Run `cloud-init --version` to confirm the version.

        If the version is later than 0.7.9, you can skip this tutorial and start to make your image. Otherwise, follow the tutorial to install cloud-init[Install cloud-init](#Install).


## Prerequisites {#section_kg1_d4m_xdb .section}

Make sure that you have installed the following programs. We use yum as an example to describe the installation. If you manage packages by using zypper or apt-get, the installation methods are similar.

-   git: Downloads the source code package of cloud-init.

    Command: `yum install git`

-   Python2.7: The basis of running and installing cloud-init.

    Command: `yum install python`

-   pip: Installs certain Python libraries on which cloud-init depends.

    Command: `yum install python-pip`


We use `yum` as an example to describe the installation. If you manage packages by using  `zypper` or `apt-get`,  the installation methods are similar to `yum`.

## Install cloud-init {#Install .section}

Follow these steps to install cloud-init:

1.  Connect to your on-premise server, virtual machine or cloud host.
2.  Run `git clone https://git.launchpad.net/cloud-init` to download the cloud-init project.
3.  Run `cd cloud-init` to change the directory to cloud-init.
4.  Run `python setup.py install`  to install setup.py, which is the installation file of cloud-init.
5.  Run `vi /etc/cloud/cloud.cfg` to modify configuration file cloud.cfg.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9704/4621_en-US.png)

    Change the preceding content of cloud\_init\_modules `cloud_init_modules`  to the following:

    ```
    
    # Example datasource config
    # The top level settings are used as module
    # and system configuration.
    # A set of users which may be applied and/or used by various modules
    # When a' default' entry is found it will reference the 'default _ user'
    # From the distro configuration specified below
    users:
    -default
    user:
    name: root
    lock_passwd: False
    # If this is set, 'root' will not be able to SSH in and they 
    # Will get a message to login instead as the above $user
    disable_root: false
    # This will cause the set + update hostname module to not operate (if true)
    preserve_hostname: false
    syslog_fix_perms: root:root
    datasource_list: [aliyun]
    # Example datasource config
    datasource:
    Aliyun:
    support x en: false
    timeout: 5 # (defaults to 50 seconds)
    max_wait: 60 # (defaults to 120 seconds)
    # metadata_urls: ['blah. com']
    # The modules that run in the 'init 'stage
    cloud_init_modules:
    ```


## Troubleshooting {#section_xsx_t4m_xdb .section}

The missing libraries may vary depending on the operating system. You can use pip to install the missing libraries. After you install the missing libraries, install setup.py again.

**Library six or library oauthlib is missing**

-   If the following message appears, it indicates the six library is missing from Python. Run `pip install six` to install the six library.

    ```
    
    File "/root/cloud-init/cloudinit/log. py", line 19, in 
    import six
    Importerror: No module named Six
    
    ```

-   If the following message appears, it means the oauthlib library is missing from Python. Run `pip install oauthlib` to install the oauthlib library.

    ```
    
    File "/root/cloud-init/cloudinit/fig", line 20, in 
    import oauthlib.oauth1 as oauth1
    Importerror: No module named oauthlib.oauth1
    
    ```


**No library is specified when an error occurs during installation**

If no dependency library is specified according to the error output, you may `pip install -r requirements.txt` to install all the dependency libraries listed in file requirements.txt of cloud-init.

## Next step {#section_bf1_mpm_xdb .section}

Make an image and [Import custom images](intl.en-US/User Guide/Images/Import images/Import custom images.md#).

## Reference {#section_qsb_npm_xdb .section}

cloud-init [Alibaba Cloud \(AliYun\)](http://cloudinit.readthedocs.io/en/latest/topics/datasources/aliyun.html)

