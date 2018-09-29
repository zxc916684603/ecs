# Metadata {#concept_j5w_pj4_xdb .concept}

The metadata of an instance is the basic information of the ECS instance including Instance ID, IP Address, Operating System, and so on. You can use the metadata to manage and/or configure an instance.

**Note:** If you manually change some instance information, this change will not be reflected in the instance metadata.

## Limits {#section_udb_rj4_xdb .section}

The metadata is only applicable for VPC-Connected instances.

## Get the metadata {#section_ejx_tj4_xdb .section}

**Linux instance**

1.  [Connect to a Linux instance by using a password](reseller.en-US/User Guide/Connect to instances/Connect to a Linux instance by using a password.md#).

2.  Run `curl http://100.100.100.200/latest/meta-data/` to access the root directory of the metadata.

3.  Add the specific metadata name to the preceding command to access the specified metadata. For example:

    -   Run `curl http://100.100.100.200/latest/meta-data/instance-id` to get the ID of an instance. ID.

    -   Run `curl http://100.100.100.200/latest/meta-data/image-id` to get the image ID of an ECS instance. ID.


**Windows instance**

1.  [Connect to a Windows instance](reseller.en-US/User Guide/Connect to instances/Connect to a Windows instance.md#).

2.  Use PowerShell to run `Invoke-RestMethod http://100.100.100.200/latest/meta-data/` to get the metadata.

3.  Add the specific metadata name to the preceding command to access the specified metadata. For example:

    -   Run `Invoke-RestMethod http://100.100.100.200/latest/meta-data/instance-id` to get the instance ID.

    -   Run `Invoke-RestMethod http://100.100.100.200/latest/meta-data/image-id` to get the image ID of an ECS instance.


## List of instance metadata {#section_yjf_jk4_xdb .section}

|Metadata name|Description|Version|
|dns-conf/nameservers|DNS configurations for an instance.|2016-01-01|
|:------------|:----------|:------|
|:-------------------|:----------------------------------|:---------|
|eipv4|EIP address|2016-01-01|
|hostname|The OS name of an instance.|2016-01-01|
|image-id|ID of the image that is selected at the time of instance creation.|2016-01-01|
|image/market-place/product-code|Product code of the image in the marketpalce.|2016-01-01|
|image/market-place/charge-type|Billing method of the image in the marketplace.|2016-01-01|
|instance-id|Instance ID|2016-01-01|
|mac|The MAC address of an instance. When multiple network interface cards exist in an instance, this metadata indicates the MAC address of eth0.|2016-01-01|
|network-type|Network type, only applicable for VPC.|2016-01-01|
|ntp-conf/ntp-servers|The address of a NTP server.|2016-01-01|
|owner-account-id|The aliuid of the instance owner.|2016-01-01|
|private-ipv4|Private IP address.|2016-01-01|
|public-ipv4|Public network IP address.|2016-01-01|
|public-keys|The list of all public keys of the current instance.|2016-01-01|
|region-id|The region where the instance is located.|2016-01-01|
|zone-id|Zone ID of the zone where the ENS instance is located.|2016-01-01|
|serial-number|The serial number of an instance.|2016-01-01|
|source-address|The source of Yum/apt, only applicable for a Linux instance.|2016-01-01|
|kms-server|Activate the server, only applicable for a Windows instance.|2016-01-01|
|wsus-server/wu-server|Update the server, only applicable for a Windows instance.|2016-01-01|
|wsus-server/wu-status-server|The server that monitors the update status of an instance, only applicable for a Windows instance.|2016-01-01|
|vpc-id|ID of the VPC that an instance is in.|2016-01-01|
|vpc-cidr-block|The CIDR block of the VPC that an instance is in.|2016-01-01|
|vswitch-cidr-block|The CIDR block of the VSwitch that an instance is in.|2016-01-01|
|vswitch-id|ID of the VSwitch that an instance is in.|2016-01-01|
|ram/security-credentials/\[role-name\]|The temporary STS credential is generated according to the policy of a RAM role. Only available when you specify a RAM role to an ECS instance. When you use this metadata to get the STS credential, \[role-name\] must be replaced with the actual RAM role name you create or you have created.**Note:** STS The new STS credential is available 30 minutes prior to the expiration of the old one.

|2016-01-01|
|instance/spot/termination-time|The spot instance release time is based on the instance operating system time zone. It is specified in the UTC time standard. For example, YYYY-MM-DDThh:mm:ssZ For example, 2018-04-07T17:03:00Z.|2016-01-01|
|network/interfaces/macs|The MAC address list of the multiple NIC \(Network Interface Controller\).|2016-01-01|
|network/interfaces/macs/\[mac\]/network-interface-id|The unique ID of the NIC, \[mac\] must be replaced with the actual MAC address.|2016-01-01|
|instance/virtualization-solution|The virtualization solution: ECS Virt 1.0 / 2.0|2016-01-01|
|instance/virtualization-solution-version|The internal Build version.|2016-01-01|
|instance/last-host-landing-time|The latest update time of the physical server, which your instance is hosted on.|2016-01-01|
|instance-identity/document|[Instance identity](reseller.en-US/User Guide/Instances/User-defined data and metadata/Instance identity.md#) Instance identity document.|2016-01-01|
|instance-identity/pkcs7|Instance identity signature.|2016-01-01|

## Other data exposing to instance via metadata {#section_uww_nvm_hfb .section}

-   **Maintenance**: On-going [system events](reseller.en-US/User Guide/Monitoring/System events.md#), run the following command in the instance to get data updated:

```
curl http://100.100.100.200/latest/maintenance/active-system-events
```

-   **Signature**: [Instance identity](reseller.en-US/User Guide/Instances/User-defined data and metadata/Instance identity.md#) document, run the following command in the instance to get data updated:

```
curl http://100.100.100.200/latest/dynamic/instance-identity/document
```

-   **Boot behavior configuration**: [Instance user data](reseller.en-US/User Guide/Instances/User-defined data and metadata/User data.md#), run the following command in the instance to get data updated:

```
curl http://100.100.100.200/latest/user-data
```


