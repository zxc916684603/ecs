# 配置 Customized Linux 自定义镜像 {#concept_nt5_4km_xdb .concept}

当您的镜像操作系统不在阿里云所支持的已有平台类型中时，您可以在 [ECS 控制台](https://ecs.console.aliyun.com/#/home)导入镜像页面选择 **Customized Linux**（定制版镜像）的平台类型，如下图所示。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9703/4620_zh-CN.png)

对于定制版镜像，阿里云会将它当作未知的操作系统类型，无法识别操作系统的各种信息，只能利用约定好的方法把实例运行所需要的必要的配置信息传入到实例中，然后实例启动时运行预定义的脚本处理这些配置信息。

## 配置方法及限制条件 {#section_p3m_wkm_xdb .section}

**限制条件**

-   定制版镜像的第一个分区必须可以被写入。

-   定制版镜像的第一个分区类型支持 FAT32/EXT2/EXT3/EXT4/UFS。

-   镜像的虚拟文件大小必须大于 5 GB。


**配置方法**

1.  在镜像的第一个分区的根目录下创建目录 `aliyun_custom_image`。
2.  使用该镜像所创建的实例在启动时，阿里云会在 `aliyun_custom_image` 目录的 **os.conf** 文件中写入实例相关配置信息。如果不存在这个文件，则会自动创建。
3.  镜像中需要有一个预定义的启动脚本，该脚本用来解析 **os.conf** 文件的各项配置，并进行相关配置，详见 [配置解析脚本 − 注意事项](#configureparsingscript) 和 [脚本示例](#scriptdemo)。

## 安全要求 {#section_nbq_zkm_xdb .section}

定制版镜像的基本安全要求如下：

-   不得存在可被远程利用的高危漏洞。
-   使用控制台的 **管理终端** 功能登录时如果存在初始默认密码，则必须在首次登录时修改，修改之前不允许进入系统做任何操作。
-   SSH 不允许有初始默认密码，初始密码必须随机生成（通过阿里云 ECS 控制系统下发）。

## os.conf 配置文件示例 {#configurationfiledemo .section}

**经典网络实例的 os.conf 配置文件示例**

```
hostname=iZ23r29djmjZ
password=cXdlcjEyMzQK
eth0_ip_addr=10.171.254.123
eth0_mac_addr=00:8c:fa:5e:14:23
eth0_netmask=255.255.255.0
eth0_gateway=10.171.254.1
eth0_route="10.0.0.0/8 10.171.254.1;172.16.0.0/12 10.171.254.1"
eth1_ip_addr=42.120.74.105
eth1_mac_addr=00:8c:fa:5e:14:24
eth1_netmask=255.255.255.0
eth1_gateway=42.120.74.1
eth1_route="0.0.0.0/0 42.120.74.1"
dns_nameserver="7.7.7.7 8.8.8.8"
```

其中各个参数的说明如下表所示。

|参数名称|参数说明|
|:---|:---|
|hostname|主机名参数。|
|password|密码参数，Base64 编码的字符串。|
|eth0\_ip\_addr|eth0 网卡 IP 地址。|
|eth0\_mac\_addr|eth0 网卡 MAC 地址。|
|eth0\_netmask|eth0 网卡掩码。|
|eth0\_gateway|eth0 网卡默认网关。|
|eth0\_route|eth0 路由列表（内网路由列表\)，默认用半角分号分隔。|
|eth1\_ip\_addr|eth1 网卡 IP 地址。|
|eth1\_mac\_addr|eth1 网卡 MAC 地址。|
|eth1\_netmask|eth1 网卡掩码。|
|eth1\_gateway|eth1 网卡默认网关。|
|eth1\_route|eth1 路由（默认外网路由）列表，默认用半角分号分隔。|
|dns\_nameserver|DNS 地址列表，默认用空格分隔。|

**VPC 网络的实例配置文件示例**

```
hostname=iZ23r29djmjZ
password=cXdlcjEyMzQK
eth0_ip_addr=10.171.254.123
eth0_mac_addr=00:8c:fa:5e:14:23
eth0_netmask=255.255.255.0
eth0_gateway=10.171.254.1
eth0_route="0.0.0.0/0 10.171.254.1"
dns_nameserver="7.7.7.7 8.8.8.8"
```

其中各个参数的说明如下表所示。

|参数名称|参数说明|
|:---|:---|
|hostname|主机名参数。|
|password|密码参数，Base64 编码的字符串。|
|eth0\_ip\_addr|eth0 网卡 IP 地址。|
|eth0\_mac\_addr|eth0 网卡 MAC 地址。|
|eth0\_netmask|eth0 网卡掩码。|
|eth0\_gateway|eth0 网卡默认网关。|
|eth0\_route|eth0 路由列表，默认用半角分号分隔。|
|dns\_nameserver|DNS 地址列表，默认用空格分隔。|

## 配置解析脚本 − 注意事项 {#configureparsingscript .section}

创建实例时阿里云会将配置项的相关信息写入第一个分区的 `aliyun_custom_image` 目录的os.conf文件中。配置定制版镜像的关键是要在镜像中预定义脚本，该脚本将从os.conf中读取相关配置信息并执行这些配置。下面是设计该脚本时的一些注意事项。

-   各配置项设值规则：如 [os.conf 配置文件示例](#configurationfiledemo) 的配置项所述，VPC 与经典网络实例的配置项数量和部分配置项的取值规则均有所不同。
-   开机启动：该脚本需要设置成开机自动运行。
-   配置文件读取路径：镜像在创建 I/O 优化实例或非 I/O 优化实例时，为第一个分区所分配的设备名默认不一样；所以在脚本中最好可以以 `uuid` 或 `label` 来识别第一个分区的设备。用户密码为 Base64 编码的字符串，所以在设置密码时需要进行相关处理。
-   对于 VPC 及经典网络的判断：需要在脚本中判断该实例是经典网络还是 VPC 网络。目前最简单的方法是判断配置项中是否存在 `eth1_route` 或其他 eth1 相关的配置项。
-   VPC 及经典网络的配置项不同之处：
    -   对于 VPC 实例，会在os.conf的 `eth0_route` 参数中配置默认外网路由；
    -   对于经典网络实例，会在os.conf的 `eth1_route` 参数中配置默认路由，内网路由配置在 `eth0_route` 中。

        所以需要在脚本中在判断出当前实例的网络类型后再有针对性地进行解析和处理。

-   配置优化：os.conf中的配置在实例的整个生命周期中执行一次即可，所以在脚本执行成功后最好删掉os.conf配置文件，同时脚本如果没有读取到os.conf配置，则不执行文件中的配置。
-   自定义镜像的处理：根据 Customized Linux 实例所创建的自定义镜像，在镜像中也会包含这个开机启动脚本。使用该自定义镜像创建实例时，阿里云会在实例第一次启动时写入os.conf配置，脚本在检测到该配置时即可执行相关配置。
-   修改相关配置时的处理：当实例的配置信息通过阿里云的控制台或 API 发生变更时，阿里云会把相关信息写入到os.conf中，脚本将被再次执行从而下发这些更改。

## 脚本示例 {#scriptdemo .section}

以下脚本是以 CentOS 镜像为例的示例脚本，需要注意如下事项：

-   该脚本仅供参考，您需要根据实际的操作系统类型进行调整从而得到具体的脚本。
-   在使用脚本前，请先在镜像中调试脚本，并保证调试通过。
-   该脚本必须配置为开机自动执行，比如将这个脚本放到 `/etc/init.d/` 目录下。

```

#!/bin/bash
### BEGIN INIT INFO
# Provides: os-conf
# Required-Start: $local_fs $network $named $remote_fs
# Required-Stop:
# Should-Stop:
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: The initial os-conf job, config the system.
### END INIT INFO
first_partition_dir='/boot/'
os_conf_dir=${first_partition_dir}/aliyun_custom_image
os_conf_file=${os_conf_dir}/os.conf
load_os_conf() {
if [[ -f $os_conf_file ]]; then
. $os_conf_file
return 0
else
return 1
fi
}
cleanup() {
# ensure $os_conf_file is deleted, to avoid repeating config system
rm $os_conf_file >& /dev/null
# ensure $os_conf_dir is exitst
mkdir -p $os_conf_dir
}
config_password() {
if [[ -n $password ]]; then
password=$(echo $password | base64 -d)
if [[ $? == 0 && -n $password ]]; then
echo "root:$password" | chpasswd
fi
fi
}
config_hostname() {
if [[ -n $hostname ]]; then
sed -i "s/^HOSTNAME=.*/HOSTNAME=$hostname/" /etc/sysconfig/network
hostname $hostname
fi
}
config_dns() {
if [[ -n $dns_nameserver ]]; then
dns_conf=/etc/resolv.conf
sed -i '/^nameserver.*/d' $dns_conf
for i in $dns_nameserver; do
echo "nameserver $i" >> $dns_conf
done
fi
}
is_classic_network() {
# vpc: eth0
# classic: eth0 eth1
grep -q 'eth1' $os_conf_file
}
config_network() {
/etc/init.d/network stop
config_interface eth0 ${eth0_ip_addr} ${eth0_netmask} ${eth0_mac_addr}
config_route eth0 ${eth0_route}
if is_classic_network ; then
config_interface eth1 ${eth1_ip_addr} ${eth1_netmask} ${eth1_mac_addr}
config_route eth1 ${eth1_route}
fi
/etc/init.d/network start
}
config_interface() {
local interface=$1
local ip=$2
local netmask=$3
local mac=$4
inteface_cfg="/etc/sysconfig/network-scripts/ifcfg-${interface}"
cat << EOF > $inteface_cfg
DEVICE=$interface
IPADDR=$ip
NETMASK=$netmask
HWADDR=$mac
ONBOOT=yes
BOOTPROTO=static
EOF
}
config_default_gateway() {
local gateway=$1
sed -i "s/^GATEWAY=.*/GATEWAY=$gateway/" /etc/sysconfig/network
}
config_route() {
local interface=$1
local route=$2
route_conf=/etc/sysconfig/network-scripts/route-${interface}
> $route_conf
echo $route | sed 's/;/\n/' | \
while read line; do
dst=$(echo $line | awk '{print $1}')
gw=$(echo $line | awk '{print $2}')
if ! grep -q "$dst" $route_conf 2> /dev/null; then
echo "$dst via $gw dev $interface" >> $route_conf
fi
if [[ "$dst" == "0.0.0.0/0" ]]; then
config_default_gateway $gw
fi
done
}
################## sysvinit service portal ####################
start() {
if load_os_conf ; then
config_password
config_network
config_hostname
config_dns
cleanup
return 0
else
echo "not load $os_conf_file"
return 0
fi
}
RETVAL=0
case "$1" in
start)
start
RETVAL=$?
;;
*)
echo "Usage: $0 {start}"
RETVAL=3
;;
esac
exit $RETVAL
```

