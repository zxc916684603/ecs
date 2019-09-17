# 步骤4：配置IPv6地址 {#concept_jpl_cd2_lgb .task}

本文介绍如何为Windows实例自动配置IPv6地址和手动配置IPv6地址，推荐您使用更高效的自动配置工具配置IPv6地址。

## 自动配置IPv6地址 {#section_wcs_yfy_wgb .section}

ecs-util-ipv6能为已分配IPv6地址的ECS实例一键配置IPv6地址，或者为没有分配IPv6地址的ECS实例一键清理IPv6配置。

使用限制如下：

-   ecs-util-ipv6工具仅适用于VPC类型实例，依赖实例元数据服务，使用前请勿将网络禁用或者将相关出口IP端口（100.100.100.200:80）禁用。详情请参见[实例元数据](cn.zh-CN/实例/管理实例/使用实例元数据/实例元数据概述.md#)。
-   ecs-util-ipv6工具运行时会自动重启网卡、网络服务，短时间内网络可能会不可用，请慎重执行。

下载地址：

-   [Windows Server 2003/2008/2012/2016（32位）](http://ecs-image-utils.oss-cn-hangzhou.aliyuncs.com/ipv6/win/32/ecs-utils-ipv6.exe)
-   [Windows Server 2003/2008/2012/2016（64位）](http://ecs-image-utils.oss-cn-hangzhou.aliyuncs.com/ipv6/win/64/ecs-utils-ipv6.exe)

下载与系统版本相对应的脚本到目标系统，使用管理员权限执行：

``` {#codeblock_6d5_cfv_jwd}
ecs-utils-ipv6.exe
```

如果当前ECS已绑定IPv6地址，则会自动配置；否则会自动清理原有IPv6地址配置。

对于需要自动化配置IPv6实例的需求，例如大批量配置，建议您使用云助手或者实例自定义数据。配合脚本的方式来调用。详情请参见[云助手](../../../../cn.zh-CN/运维与监控/云助手/云助手概述.md#)和[实例自定义数据](cn.zh-CN/实例/管理实例/使用实例自定义数据/生成实例自定义数据.md#)。以下为脚本示例（假设是64位，PowerShell脚本）。

``` {#codeblock_248_r2r_oak}
#powershell
$install_dir="C:\Windows\system32"
$install_path = "$install_dir\ecs-utils-ipv6.exe"

if(-not (Test-Path -Path $install_path)){
    # download the tool
    $tool_url = 'http://ecs-image-utils.oss-cn-hangzhou.aliyuncs.com/ipv6/win/64/ecs-utils-ipv6.exe' 
    Invoke-WebRequest -uri $tool_url -OutFile $install_path
    Unblock-File $install_path
}

# run the tool
Start-Process -FilePath "$install_path" -ArgumentList "--noenterkey" -NoNewWindow
```

## 手动配置IPv6地址 {#section_hln_xpg_ygb .section}

完成以下操作，手动配置IPv6地址：

1.  检查实例是否已开启IPv6服务。 
    1.  远程连接实例。具体步骤，请参见[使用管理终端连接Windows实例](../../../../cn.zh-CN/实例/连接实例/连接Windows实例/使用管理终端连接Windows实例.md#)。
    2.  打开Windows命令处理程序CMD。
    3.  运行ipconfig。 
        -   若返回IPv6地址相关内容，表示实例已成功开启IPv6服务。
        -   若实例还未开启IPv6服务，请根据下面步骤开启IPv6服务。
2.  开启IPv6服务。 
    -   Windows Server 2008/2012/2016的操作步骤如下：
        1.  远程连接实例。
        2.  选择**控制面板** \> **网络和共享中心** \> **网络连接**。
        3.  单击当前网络连接名，打开状态界面，再单击**属性**。
        4.  检查IPv6协议这一行是否被勾选。如果没有勾选则需要选中，然后单击**确定**。
    -   Windows Server 2003的操作步骤如下：
        1.  远程连接实例。具体步骤，请参见[使用管理终端连接Windows实例](../../../../cn.zh-CN/实例/连接实例/连接Windows实例/使用管理终端连接Windows实例.md#)。
        2.  选择**控制面板** \> **网络和共享中心** \> **网络连接**。
        3.  单击当前网络连接名，打开状态界面，再单击**属性**。
        4.  根据IPv6协议是否存在，执行不同操作。
            -   如果存在IPv6协议，则勾选**Internet 协议版本 6 （TCP/IPv6）**，再单击**确定**。
            -   如果不存在IPv6协议，您需要手动安装IPv6协议后勾选**Internet 协议版本 6 （TCP/IPv6）**，再单击**确定**。以下为手动安装IPv6协议的操作步骤：
                1.  在本地连接属性页面，单击**安装**，在网络组件类型页面单击**协议** \> **添加**。
                2.  在选择网络协议页面，选择**Microsoft TCP/IP 版本 6** \> **确定**完成安装。
3.  查询实例的IPv6地址。 

    您可以通过控制台和实例元数据查看实例分配的IPv6地址。

    -   控制台：请参见[分配 IPv6 地址](cn.zh-CN/网络/配置IPv6地址/Windows实例配置IPv6地址/步骤2：分配IPv6地址.md#)。
    -   实例元数据：通过以下元数据项获取IPv6地址。详情请参见[实例元数据](cn.zh-CN/实例/管理实例/使用实例元数据/实例元数据概述.md#)。
        -   IPv6 地址：network/interfaces/macs/\[mac\]/ipv6s
        -   IPv6 网关：network/interfaces/macs/\[mac\]/ipv6-gateway
        -   IPv6 虚拟交换机CIDR地址段：network/interfaces/macs/\[mac\]/vswitch-ipv6-cidr-block
4.  手动配置IPv6地址。 
    -   Windows Server 2008/2012/2016的操作步骤如下：
        1.  远程连接实例。具体步骤，请参见[使用管理终端连接Windows实例](../../../../cn.zh-CN/实例/连接实例/连接Windows实例/使用管理终端连接Windows实例.md#)。
        2.  选择**控制面板** \> **网络**。
        3.  单击当前网络连接名，打开状态界面，再单击**属性**。
        4.  选择**IPv6协议** \> **属性**。
        5.  勾选**使用以下IPv6地址**，并填入IPv6地址、子网前缀长度和IPv6网关，单击**确定**。
        6.  （可选）绑定多个IPv6地址：在Internet 协议版本 6（TCP/IP）属性界面，单击 **高级**打开高级设置界面，单击**添加** 做批量处理。完成后单击 **确定**。
    -   Windows Server 2003的操作步骤如下：
        1.  远程连接实例。具体步骤，请参见[使用管理终端连接Windows实例](../../../../cn.zh-CN/实例/连接实例/连接Windows实例/使用管理终端连接Windows实例.md#)。
        2.  选择**控制面板** \> **网络连接**，查看当前网络连接名，假设为**本地连接 2**。
        3.  打开 Windows 命令处理程序 CMD。
        4.  添加IPv6地址。
            -   单个IPv6地址运行以下命令：

                ``` {#codeblock_htl_pvq_ghe}
                netsh interface ipv6 add address "本地连接 2" <IPv6 地址>
                ```

            -   多个IPv6地址运行以下命令：

                ``` {#codeblock_qnd_c2z_p1q}
                netsh interface ipv6 add address "本地连接 2" <IPv6 地址 1>
                netsh interface ipv6 add address "本地连接 2" <IPv6 地址 2>
                ```

        5.  运行以下命令添加默认路由：

            ``` {#codeblock_sgo_vi5_8jv}
            netsh interface ipv6 add route ::/0 "本地连接 2" <IPv6 网关>
            ```


