# Install cloud-init for Linux images {#concept_e3k_vnm_xdb .concept}

If you need to create an ECS instance using an existing image, you can import the image to configure the instance. To guarantee successful configuration of the hostname, NTP source, and yum source of the imported Linux image, you are advised to install cloud-init in your on-premise server, virtual machine \(VM\), or cloud host before import.

## Limitations {#section_bw3_b4m_xdb .section}

-   Currently, cloud-init supports the following Linux distributions: CentOS, Debian, Fedora, FreeBSD, Gentoo, RHEL \(Red Hat Enterprise Linux\), SLES \(SUSE Linux Enterprise Server\), and Ubuntu.

-   If cloud-init has been installed on your on-premise server, VM, or cloud host, make sure that the cloud-init version is later than 0.7.9 because images using an earlier-version cloud-init may cause instance configuration failure in NTP, hostname, and yum.

    1.  Log on to your on-premise server, VM, or cloud host.
    2.  Run `cloud-init --version` to query the cloud-init version.

        You can use the cloud-init if its version is later than 0.7.9. Otherwise, do as instructed in [Install cloud-init](#Install).


## Prerequisites {#section_kg1_d4m_xdb .section}

You have installed the following software on your on-premise server, VM, or cloud host:

-   git: Source code package of cloud-init

    Command for installing yum: `yum install git`.

-   Python2.7: Basis of cloud-init installation and running.

    Command for installing yum: `yum install python`

-   pip: Python library on which cloud-init installation depends.

    Command for installing yum: `yum install python-pip`


`yum` installation is used as an example. If you manage packages using `zypper` or `apt-get`, the installation methods are similar to `yum`.

## Install cloud-init {#Install .section}

Do as follows to install cloud-init:

1.  Log on to your on-premise server, VM, or cloud host.
2.  Run `git clone https://git.launchpad.net/cloud-init` to download the cloud-init source code package.
3.  Run `cd cloud-init` to go to the cloud-init directory.
4.  Run `python setup.py install` to install setup.py, which is the cloud-init installation file.
5.  Run `vi /etc/cloud/cloud.cfg` to modify the cloud.cfg configuration file.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9704/15394858294621_en-US.png)

    Modify `cloud_init_modules` configurations to the following:

    ```
    # Example datasource config
     # The top level settings are used as module
     # and system configuration.
     # A set of users which may be applied and/or used by various modules
     # when a 'default' entry is found it will reference the 'default_user'
     # from the distro configuration specified below
     users:
        - default
     user:
         name: root
         lock_passwd: False
     # If this is set, 'root' will not be able to ssh in and they 
     # will get a message to login instead as the above $user
     disable_root: false
     # This will cause the set+update hostname module to not operate (if true)
     preserve_hostname: false
     syslog_fix_perms: root:root
     datasource_list: [ AliYun ]
     # Example datasource config
     datasource:
         AliYun:
             support_xen: false
             timeout: 5 # (defaults to 50 seconds)
             max_wait: 60 # (defaults to 120 seconds)
     #      metadata_urls: [ 'blah.com' ]
     # The modules that run in the 'init' stage
     cloud_init_modules:
    ```


## Troubleshooting {#section_xsx_t4m_xdb .section}

The libraries missing from images may be different. You can install the missing libraries through pip and repeat step [4](#setup.py).

**When the six and oauthlib libraries are missing**

-   The six library is missing from Python if the following message is displayed during installation. You can run `pip install six` to install the six library through pip.

    ```
    File "/root/cloud-init/cloudinit/log.py", line 19, in <module>
          import six
      ImportError: No module named s  )
    ```

-   The oauthlib library is missing from Python if the following message is displayed during installation. You can run `pip install oauthlib` to install the six library through pip.

    ```
    File "/root/cloud-init/cloudinit/url_helper.py", line 20, in <module>
          import oauthlib.oauth1 as oauth1
      ImportError: No module named oauthlib.oaut  )
    ```


**When an error message does not indicate missing libraries**

You can run `pip install -r requirements.txt` to install all dependency libraries according to the library information in the requirements.txt file of cloud-init.

## Next step {#section_bf1_mpm_xdb .section}

You can [import the image to ECS](reseller.en-US/User Guide/Images/Import images/Import custom images.md#).

## Reference {#section_qsb_npm_xdb .section}

cloud-init [Alibaba Cloud \(AliYun\)](http://cloudinit.readthedocs.io/en/latest/topics/datasources/aliyun.html)

