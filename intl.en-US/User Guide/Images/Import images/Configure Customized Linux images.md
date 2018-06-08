# Configure Customized Linux images {#concept_nt5_4km_xdb .concept}

Customized Linux images are Linux images that currently ECS cannot provide. If you want to run Customized Linux image on your ECS instances, you can import the Customized Linux image in the [ECS console](https://ecs.console.aliyun.com/#/home) and configure **Customized Linux** according to this tutorial, see the following image.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9703/4620_en-US.png)

A Customized Linux image is treated as an unknown operating system. ECS configures the Customized Linux image by writing the necessary configuration information, such as SSH configuration, to the instance, and then runs a predefined script at the instance startup to process the configuration information.

## Limits an procedures {#section_p3m_wkm_xdb .section}

**Limits**

-   The first primary partition of the custom image must be writable.

-   The first primary partition type of the custom image must be FAT32, EXT2, EXT3, EXT4, or UFS.

-   The virtual file size of the image must be greater than 5 GB.


**Procedures**

1.  Create the directory `aliyun_custom_image` in the root directory of the first primary partition.
2.  When the Customized Linux instance starts up, ECS either writes the instance-related configuration information to the os.conf file in the `aliyun_custom_image` directory or, if this file does not exist, a new file with the name as **os.conf** is automatically created.
3.  The image must contain a pre-defined startup script to parse various configuration parameters in the **os.conf** file and implement the configuration. For more information, see [Configure the parsing script](#configureparsingscript) t and [Script sample](#scriptdemo).

## Security requirements {#section_nbq_zkm_xdb .section}

The basic security requirements for Customized Linux are as follows:

-   No high-risk vulnerabilities that can be exploited remotely.
-   If a default initial password exists for **VNC**, the password must be changed at the first log on. Access of the default VNC account is denied until the password is changed.
-   No default initial password for SSH. A random initial password must be generated and distributed by the Alibaba Cloud ECS control system.

## Samples of os.conf configuration file {#configurationfiledemo .section}

**Sample for the classic network-connected instances**

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

The description of the parameters is as follows.

|Parameter|Description|
|:--------|:----------|
|hostname|The host name|
|password |The password, in the format of a Base64-encoded string|
|eth0\_ip\_addr|The IP address of eth0 NIC|
|eth0\_mac\_addr|The MAC address of eth0 NIC|
|eth0\_netmask|The network mask of eth0 NIC|
|eth0\_gateway|The default gateway of eth0 NIC|
|eth0\_route|The route list \(intranet route list\) of eth0, separated with semicolons by default|
|eth1\_ip\_addr|The IP address of eth1 NIC|
|eth1\_mac\_addr|The MAC address of eth1 NIC|
|eth1\_netmask|The network mask of eth1 NIC|
|eth1\_gateway|The default gateway of eth1 NIC|
|eth1\_route|The route \(default Internet route\) list of eth1, separated with semicolons by default|
|dns\_nameserver|DNS address list, separated with spaces by default|

**Sample for VPC-Connected instances**

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

The parameter definitions are as follows.

|Parameter|Description|
|:--------|:----------|
|hostname|The host name|
|password|The password, in the format of a Base64-encoded string|
|eth0\_ip\_addr|The IP address of eth0 NIC|
|eth0\_mac\_addr|The MAC address of eth0 NIC|
|eth0\_netmask|The network mask of eth0 NIC|
|eth0\_gateway|The default gateway of eth0 NIC|
|eth0\_route|The route list of eth0, separated with semicolons by default|
|dns\_nameserver|DNS address list, separated with spaces by default|

## Configure the parsing script {#configureparsingscript .section}

For an optimized Customized Linux configuration, we recommend you predefine the script in the image. When you create an instance, ECS writes information related to the configuration parameters to the os.conf file in the `aliyun_custom_image` directory, in the first primary partition. The script then reads the relevant configuration information from the os.conf file and implements the configuration. During script creation, pay attention to the following:

-   Rules for configuring parameters: As stated in [Samples of os.conf configuration file](#configurationfiledemo), the number of configuration parameters and rules for some configuration parameter values for instances are different for VPC and classic networks.
-   Boot start: The script must be set to boot automatically at system startup.
-   Configuration file path: When you use the image to create an instance, the default device name assigned to the first primary partition varies between I/O-optimized and non-I/O-optimized instances. We recommend you use the `uuid` or `label` in the script to identify the device in the first primary partition. The user password is a Base64-encoded string, and must be entered the same way in the script.
-   Identify VPC or classic network: You must determine the instance network type in the script as either VPC or classic network.  The easiest method is to identify whether `eth1_route` or other eth1-related configuration items exist.
-   Configuration differences between the VPC and classic network:
    -   For a VPC instance, the default Internet route is configured in the `eth0_route` parameter in the os.conf file.
    -   For a classic network instance, the default route is configured in the `eth1_route` parameter, and the intranet route is configured in the `eth0_route` parameter.

        Therefore, it is necessary in the script to determine the network type of the instance, and then have a specific analysis and processing.

-   Configuration optimization: During the life cycle of an instance, the os.conf file must be executed only once, so we recommend that you delete the os.conf configuration file after the script runs successfully. If the script fails to read the os.conf configuration, no configuration is executed.
-   Process a custom image: The custom image created on the Customized Linux instance must include the boot script. When you create an instance using the custom image, ECS writes the os.conf configuration when the instance is started for the first time. The script then implements the related configuration items when it detects the configuration.
-   Modify related configuration: When the instance configuration information is changed in the ECS console or by an API, ECS writes the relevant information to the os.conf file. Changes are implemented when the script runs again.

## Script sample {#scriptdemo .section}

See the following script example for a CentOS image.

-   The script is for reference only. You must modify it based on the actual operating system type to get a valid script.
-   Before you use the script, make sure that the script passes the debugging process.
-   The script must be configured to run at boot automatically, for example, by putting the script in the `/etc/init.d/` directory.

```

/bin/bash
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

cleanup() {
# ensure $os_conf_file is deleted, to avoid repeating config system
rm $os_conf_file >& /dev/null
# ensure $os_conf_dir is exitst
mkdir -p $os_conf_dir

config_password() {
if [[ -n $password ]]; then
password=$(echo $password | base64 -d)
if [[ $? == 0 && -n $password ]]; then
echo "root:$password" | chpasswd
fi
fi

config_hostname() {
if [[ -n $hostname ]]; then
sed -i "s/^HOSTNAME=. */HOSTNAME=$hostname/" /etc/sysconfig/network
hostname $hostname
fi

config_dns() {
if [[ -n $dns_nameserver ]]; then
dns_conf=/etc/resolv.conf
sed -i '/^nameserver.*/d' $dns_conf
for i in $dns_nameserver; do
echo "nameserver $i" >> $dns_conf
done
fi

is_classic_network() {
# vpc: eth0
# classic: eth0 eth1
grep -q 'eth1' $os_conf_file

config_network() {
/etc/init.d/network stop
config_interface eth0 ${eth0_ip_addr} ${eth0_netmask} ${eth0_mac_addr}
config_route eth0 ${eth0_route}
If; then
Config_interface eth1 $ {eth1_ip_addr} $ {eth1_netmask} $ {eth1_mac_addr}
config_route eth1 ${eth1_route}
fi
/etc/init.d/network start

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

config_default_gateway() {
Local gateway = $1
sed -i "s/^GATEWAY=. */GATEWAY=$gateway/" /etc/sysconfig/network

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

RETVAL=0
case "$1" in
start)
start
RETVAL=$?


echo "Usage: $0 {start}"
RETVAL=3

esac
exit $RETVAL
```

