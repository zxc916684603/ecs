# Linux镜像如何开启或关闭Meltdown与Spectre安全漏洞补丁 {#KnownIssueMeltdownSpectre2018 .concept}

本文描述了阿里云ECS如何应对和预防Meltdown与Spectre损害，您可以根据本文描述了解阿里云ECS侧的安全措施。

## 背景信息 {#section_skt_htn_2gb .section}

漏洞Meltdown与Spectre（中文名称为熔断和幽灵）是存在于英特尔（Intel）处理器芯片的安全漏洞。该漏洞事件源于芯片硬件层面的设计缺陷，可导致操作系统内核信息泄露、应用程序越权访问系统内核数据等问题。漏洞编号请在 CVE 网站搜索查看：分别为：

-   [CVE-2017-5753](http://t.cn/E48m0VZ)
-   [CVE-2017-5715](http://t.cn/E48mmqP)
-   [CVE-2017-5754](http://t.cn/E48uvUp)

阿里云于2018年1月20日发布了[安全漏洞公告](https://www.alibabacloud.com/help/faq-detail/64951.htm)公示漏洞风险详情及影响范围。

本文具体介绍阿里云提供的公共镜像（GuestOS）安全补丁设置情况，及您如何根据具体情况配置操作系统。默认安全策略如下所示：

-   对Meltdown漏洞默认采取pti on（Page Table Isolation开启）措施，打开Meltdown安全漏洞补丁。
-   对Spectre漏洞默认采取noibrs（No Indirect Branch Restricted Speculation，禁止间接分支限制推测）措施，结合了reptpoline和ibpb（Indirect Branch Prediction Barriers）的限制策略。

## 如何开启或者关闭Meltdown安全漏洞补丁 {#section_v3p_3tn_2gb .section}

已打开Meltdown安全漏洞补丁（采取pti on措施）的公共镜像包括：

-   CentOS 7.5/7.6
-   Debian 9.6/8.10
-   Red Hat 7.5/7.6
-   SUSE Linux 15
-   Ubuntu 18.04
-   CoreOS 1911.3.0
-   FreeBSD 11.2
-   OpenSUSE 15

以上列表将随阿里云公共镜像的更新而发生变化。

如果您认为开启PTI对实例性能有影响，或者您有其他防护措施，可以根据以下步骤关闭PTI：

1.  远程连接实例。
2.  选择您要做的操作：
    -   CentOS、Debian、OpenSUSE、Red Hat、SUSE Linux和Ubuntu：添加内核参数`nopti`。
    -   CoreOS：运行`vi /usr/share/oem/grub.cfg`，在GRUB配置文件中加入`pti=off`。
    -   FreeBSD：运行`vi /boot/loader.conf`，在配置文件中加入`vm.pmap.pti=0`。
3.  重启实例。

## 如何开启或者关闭Spectre安全漏洞补丁 {#section_orl_jtn_2gb .section}

阿里云目前支持ibrs和ibpb能力输出。公共镜像默认通过reptpoline和ibpb （Indirect Branch Prediction Barriers）的限制策略对Spectre漏洞进行防护，同时通过noibrs参数禁用了ibrs。涉及的公共镜像包括：

-   CentOS 7.5/7.6
-   Debian 9.6/8.10
-   Red Hat 7.5/7.6
-   SUSE Linux 15
-   Ubuntu 18.04
-   CoreOS 1911.3.0
-   FreeBSD 11.2
-   OpenSUSE 15

以上列表将随阿里云公共镜像的更新而发生变化。

如果您需要恢复操作系统默认设置，或者认为当前设置对性能有影响或您有其他防护措施需要关闭Spectre安全漏洞补丁，请按照以下步骤做相应修改：

1.  远程连接实例。
2.  根据下表中的说明选择您要做的操作：

    |发行平台|如何恢复阿里云默认设置|如何恢复操作系统默认设置|如何关闭Spectre漏洞补丁|
    |:---|:----------|:-----------|:--------------|
    |CentOS|添加内核参数noibrs|删除内核参数noibrs|添加内核参数spectre\_v2=off|
    |Red Hat|
    |CoreOS|运行`vi /usr/oem/share/grub.cfg`在GRUB配置文件中添加内核参数spectre\_v2=off|删除内核参数spectre\_v2=off|
    |OpenSUSE|添加内核参数spectre\_v2=off|
    |Debian|已默认开启retpoline与ibpb防护措施|无需修改|
    |Ubuntu|
    |SUSE Linux|已默认开启retpoline防护措施|
    |FreeBSD|添加内核参数hw.ibrs\_disable|删除内核参数hw.ibrs\_disable|添加内核参数hw.ibrs\_disable|

    **说明：** 内核参数`noibrs`对OpenSUSE和CoreOS操作系统无效，您需要通过设置`spectre_v2=off`添加防护措施。

3.  重启实例。

## 如何检测是否开启防护 {#section_twp_ktn_2gb .section}

1.  远程连接实例。
2.  在[GitHub spectre-meltdown-checker Repo](https://github.com/speed47/spectre-meltdown-checker)获取spectre-meltdown-checker.sh检测脚本。
3.  在实例内部运行：

    ```
    chmod +x spectre-meltdown-checker.sh
    sudo bash spectre-meltdown-checker.sh
    ```

4.  根据脚本提示判断是否已开启Meltdown或Spectre防护。

## 相关链接 {#section_dkd_ltn_2gb .section}

若您使用的是下列操作系统，可以前往官网了解更多详情：

-   [Red Hat](https://access.redhat.com/articles/3311301) 
-   [SUSE Linux](https://www.suse.com/support/kb/doc/?id=7022512)
-   [Ubuntu](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown/MitigationControls)

