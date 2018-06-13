# API overview {#AvailableActions .reference}

See the following tables for the ECS APIs that are available to use.

For more information, see the  [API Explorer](https://api.aliyun.com/).

## Instance {#section_vvj_q2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[RunInstances](intl.en-US/API Reference/Instances/RunInstances.md#)|Creates a specified number of Pay-As-You-Go instances.|
|[CreateInstance](intl.en-US/API Reference/Instances/CreateInstance.md#)|Creates an instance.|
|[StartInstance](intl.en-US/API Reference/Instances/StartInstance.md#)|Starts a specified instance.|
|[StopInstance](intl.en-US/API Reference/Instances/StopInstance.md#)| Stops a specified instance.|
|[RebootInstance](intl.en-US/API Reference/Instances/RebootInstance.md#)|Restarts an instance.|
|[DeleteInstance](intl.en-US/API Reference/Instances/DeleteInstance.md#)| Releases an instance.|
|[AttachInstanceRamRole](intl.en-US/API Reference/Instances/AttachInstanceRamRole.md#)|Attaches an instance RAM role to your Instance.|
|[DetachInstanceRamRole](intl.en-US/API Reference/Instances/DetachInstanceRamRole.md#)|Detaches a RAM role from an instance.|
|[DescribeInstanceStatus](intl.en-US/API Reference/Instances/DescribeInstanceStatus.md#)|Obtains the list of all your instances in batches with status information.|
|[DescribeInstances](intl.en-US/API Reference/Instances/DescribeInstances.md#)| Describes details of your instances.|
|[DescribeInstanceVncUrl](intl.en-US/API Reference/Instances/DescribeInstanceVncUrl.md#)|Describes the management terminal URL before connecting to an instance.|
|[DescribeUserdata](intl.en-US/API Reference/Instances/DescribeUserdata.md#)|Describes the user-defined data of an Instance.|
|[DescribeInstanceAutoRenewAttribute](intl.en-US/API Reference/Instances/DescribeInstanceAutoRenewAttribute.md#)|Describes the auto renewal status of an instance.|
|[DescribeInstanceRamRole](intl.en-US/API Reference/Instances/DescribeInstanceRamRole.md#)|Describes information related to the instance RAM role.|
|[DescribeSpotPriceHistory](intl.en-US/API Reference/Instances/DescribeSpotPriceHistory.md#)|Describes the price history of the spot instance.  You can query the price records within 30 days at most.|
|[DescribeInstanceTypeFamilies](intl.en-US/API Reference/Instances/DescribeInstanceTypeFamilies.md#)|Describes the resources list of instance type families provided by Alibaba Cloud ECS.|
|[DescribeInstanceTypes](intl.en-US/API Reference/Instances/DescribeInstanceTypes.md#)|Describes the resources list of instance types provided by Alibaba Cloud ECS.|
|[ModifyInstanceVpcAttribute](intl.en-US/API Reference/Instances/ModifyInstanceVpcAttribute.md#)|Modifies the attributes of a VPC to which a specified instance is connected.|
|[ModifyInstanceAttribute](intl.en-US/API Reference/Instances/ModifyInstanceAttribute.md#)|Modifies the information of an Instance, such as the name, password, host name, and description of an instance.|
|[ModifyInstanceVncPasswd](intl.en-US/API Reference/Instances/ModifyInstanceVncPasswd.md#)|Changes the password of management terminal used to connect a specified Instance.|
|[ModifyInstanceAutoReleaseTime](intl.en-US/API Reference/Instances/ModifyInstanceAutoReleaseTime.md#)|Sets the automatic release time for a specified instance.|
|[ModifyInstanceAutoRenewAttribute](intl.en-US/API Reference/Instances/ModifyInstanceAutoRenewAttribute.md#)|Modifies the information of an Instance, such as the name, password, host name, and description of an instance.|
|[ModifyInstanceSpec](intl.en-US/API Reference/Instances/ModifyInstanceSpec.md#)|Changes the instance type or modifies the Internet bandwidth of a Pay-As-You-Go instance.|
|[ModifyPrepayInstanceSpec](intl.en-US/API Reference/Instances/Modifyprepayinstancespec.md#)|Upgrade or lower the pre-payment instance specification.|

## Disk {#section_t3s_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[CreateDisk](intl.en-US/API Reference/Disk/CreateDisk.md#)|Creates a portable data disk.|
|[DeleteDisk](intl.en-US/API Reference/Disk/DeleteDisk.md#)| Releases an independent cloud disk when it is no longer in use.|
|[DescribeDisks](intl.en-US/API Reference/Disk/DescribeDisks.md#)| Describes your available cloud disks.|
|[AttachDisk](intl.en-US/API Reference/Disk/AttachDisk.md#)|Attaches a data disk to your Instance.|
|[DetachDisk](intl.en-US/API Reference/Disk/DetachDisk.md#)|Detaches a cloud disk from a specified instance.|
|[ModifyDiskAttribute](intl.en-US/API Reference/Disk/ModifyDiskAttribute.md#)|Modifies the attribute of your cloud disk.|
|[ReplaceSystemDisk](intl.en-US/API Reference/Disk/ReplaceSystemDisk.md#)|Replaces the system disk or the operating system of an Instance.|
|[ReInitDisk](intl.en-US/API Reference/Disk/ReInitDisk.md#)|Initializes a cloud disk to the initial state.|
|[ResetDisk](intl.en-US/API Reference/Disk/ResetDisk.md#)|Rolls back a disk to a specified disk state by using one of its history disk snapshots.|
|[Extends the size of a cloud disk.](intl.en-US/API Reference/Disk/ResizeDisk.md#)|Expand a disk.|

## Image {#section_image_t2h_vdb .section}

|Action| Description|
|:-----|:-----------|
|[CreateImage](intl.en-US/API Reference/Images/CreateImage.md#)|Creates a custom image.|
|[ImportImage](intl.en-US/API Reference/Images/ImportImage.md#)|Imports on-premises image files to the Alibaba Cloud ECS.|
|[ExportImage](intl.en-US/API Reference/Images/ExportImage.md#)|Exports a custom image to an OSS bucket in the same region as the custom image.|
|[CopyImage](intl.en-US/API Reference/Images/CopyImage.md#)|Copies a custom image from one region to other regions.|
|[CancelCopyImage](intl.en-US/API Reference/Images/CancelCopyImage.md#)|Cancels a pending image copy \(`CopyImage`\) operation.|
|[DescribeImages](intl.en-US/API Reference/Images/DescribeImages.md#)|Describes your available image.|
|[DeleteImage](intl.en-US/API Reference/Images/Deleteimage.md#)|Deletes a specified custom image.|
|[DescribeImageSharePermission](intl.en-US/API Reference/Images/DescribeImageSharePermission.md#)|Describes all the authorized users to whom one of your custom image is shared.|
|[ModifyImageAttribute](intl.en-US/API Reference/Images/ModifyImageAttribute.md#)|Modifies the name and description of a custom image.|
|[ModifyImageSharePermission](intl.en-US/API Reference/Images/ModifyImageSharePermission.md#)|Shares a custom image to other Alibaba Cloud users.|

## Snapshot {#section_snapshot_t2h_vdb .section}

|Action| Description|
|:-----|:-----------|
|[CreateSnapshot](intl.en-US/API Reference/Snapshots/CreateSnapshot.md#)|Creates a snapshot for a specified disk device.|
|[CreateAutoSnapshotPolicy](intl.en-US/API Reference/Snapshots/CreateAutoSnapshotPolicy.md#)|Creates an automatic snapshot policy.|
|[ApplyAutoSnapshotPolicy](intl.en-US/API Reference/Snapshots/ApplyAutoSnapshotPolicy.md#)|Applies automatic snapshot policies to one or more disks.|
|[DeleteSnapshot](intl.en-US/API Reference/Snapshots/DeleteSnapshot.md#)| Deletes a specified snapshot.|
|[CancelAutoSnapshotPolicy](intl.en-US/API Reference/Snapshots/CancelAutoSnapshotPolicy.md#)|Cancels the automatic snapshot policy for one or more disks.|
|[DeleteAutoSnapshotPolicy](intl.en-US/API Reference/Snapshots/DeleteAutoSnapshotPolicy.md#)|Deletes an automatic snapshot policy.|
|[DescribeAutoSnapshotPolicyEx](intl.en-US/API Reference/Snapshots/DescribeAutoSnapshotPolicyEx.md#)|Describes your available automatic snapshot policies.|
|[DescribeSnapshots](intl.en-US/API Reference/Snapshots/DescribeSnapshots.md#)|Describes one or more of your available snapshots.|
|[DescribeSnapshotLinks](intl.en-US/API Reference/Snapshots/DescribeSnapshotLinks.md#)|Describes the snapshot chains of one or more disks.|
|[ModifyAutoSnapshotPolicyEx](intl.en-US/API Reference/Snapshots/ModifyAutoSnapshotPolicyEx.md#)|Modifies an automatic snapshot policy.|

## Network {#section_network_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[AllocatePublicIpAddress](intl.en-US/API Reference/Networks/AllocatePublicIpAddress.md#)|Assigns an Internet IP address to an instance.|
|[ConvertNatPublicIpToEip](intl.en-US/API Reference/Networks/ConvertNatPublicIpToEip.md#)|Changes the public IP \(NatPublicIp\) of a VPC-connected instance to an Elastic IP \(EIP\).|
|[AttachClassicLinkVpc](intl.en-US/API Reference/Networks/AttachClassicLinkVpc.md#)|Links a classic network instance to a VPC, which allows the classic network instance communicating with the resources that are in the intranet of a VPC.|
|[DetachClassicLinkVpc](intl.en-US/API Reference/Networks/DetachClassicLinkVpc.md#)|Unlinks a classic network-connected instance from the VPC.|
|[DescribeBandwidthLimitation](intl.en-US/API Reference/Networks/Describebandwidthlimitation.md#)|Describes a list of bandwidth resources.|
|[DescribeClassicLinkInstances](intl.en-US/API Reference/Networks/DescribeClassicLinkInstances.md#)|Describes one or more of your classic network-connected instances that have established ClassicLink with a VPC.|
|[ModifyInstanceNetworkSpec](intl.en-US/API Reference/Networks/ModifyInstanceNetworkSpec.md#)|Modifies the bandwidth configuration of your Instance.|

For more information about the APIs for Virtual Private Cloud \(VPC\), see VPC [API  Reference](../../../../intl.en-US/API reference/Overview of API.md#).

## Security group {#section_securitygroup_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[CreateSecurityGroup](intl.en-US/API Reference/Security groups/CreateSecurityGroup.md#)|Creates a security group.|
|[AuthorizeSecurityGroup](intl.en-US/API Reference/Security groups/AuthorizeSecurityGroup.md#)|Adds an inbound rule to a security group.|
|[AuthorizeSecurityGroupEgress](intl.en-US/API Reference/Security groups/AuthorizeSecurityGroupEgress.md#)|Adds an outbound rule to a security group.|
|[RevokeSecurityGroup](intl.en-US/API Reference/Security groups/RevokeSecurityGroup.md#)| Deletes an inbound rule from a security group.|
|[RevokeSecurityGroupEgress](intl.en-US/API Reference/Security groups/RevokeSecurityGroupEgress.md#)|Deletes an outbound rule from a security group.|
|[JoinSecurityGroup](intl.en-US/API Reference/Security groups/JoinSecurityGroup.md#)|Adds an instance to a specified security group.|
|[LeaveSecurityGroup](intl.en-US/API Reference/Security groups/LeaveSecurityGroup.md#)|Removes an instance from a specified security group.|
|[DeleteSecurityGroup](intl.en-US/API Reference/Security groups/DeleteSecurityGroup.md#)|Deletes one of your security groups.|
|[DescribeSecurityGroupAttribute](intl.en-US/API Reference/Security groups/DescribeSecurityGroupAttribute.md#)|Describes one of your security groups.|
|[DescribeSecurityGroups](intl.en-US/API Reference/Security groups/DescribeSecurityGroups.md#)|Describes the basic information about your security groups, such as the security group ID and description.|
|[DescribeSecurityGroupReferences](intl.en-US/API Reference/Security groups/DescribeSecurityGroupReferences.md#)|Describes whether a specified security group has been authorized by other security group or not.|
|[ModifySecurityGroupAttribute](intl.en-US/API Reference/Security groups/ModifySecurityGroupAttribute.md#)|Modifies the attribute of the specified security group, including the security group name and description.|
|[ModifySecurityGroupPolicy](intl.en-US/API Reference/Security groups/ModifySecurityGroupPolicy.md#)|Modifies the intranet communication policy of a security group.|
|[ModifySecurityGroupRule](intl.en-US/API Reference/Security groups/ModifySecurityGroupRule.md#)|Modifies the description of a security group inbound rule.|

## SSH key pair {#section_keypair_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[CreateKeyPair](intl.en-US/API Reference/SSH key pairs/CreateKeyPair.md#)|Creates an SSH key pair.|
|[ImportKeyPair](intl.en-US/API Reference/SSH key pairs/ImportKeyPair.md#)|Imports the public key of an SSH key pair that you create with other key pair generators into one of the Alibaba Cloud regions.|
|[AttachKeyPair](intl.en-US/API Reference/SSH key pairs/AttachKeyPair.md#)|Attaches an SSH key pair to one or more of your Linux instances.|
|[DetachKeyPair](intl.en-US/API Reference/SSH key pairs/DetachKeyPair.md#)|Detaches an SSH key pair from one or more of your Linux instances.|
|[DeleteKeyPairs](intl.en-US/API Reference/SSH key pairs/DeleteKeyPairs.md#)| Deletes one or more of your SSH key pairs.|
|[DescribeKeyPairs](intl.en-US/API Reference/SSH key pairs/DescribeKeyPairs.md#)|Describes one or more of your SSH key pairs.|

## ENI {#section_networkinterface_t2h_vdb .section}

|Action| Description|
|:-----|:-----------|
|[CreateNetworkInterface](intl.en-US/API Reference/Elastic network interfaces/CreateNetworkInterface.md#)|Creates an ENI \(Elastic Network Interface\).|
|[AttachNetworkInterface](intl.en-US/API Reference/Elastic network interfaces/AttachNetworkInterface .md#)|Attaches an ENI to a VPC-connected instance.|
|[DetachNetworkInterface](intl.en-US/API Reference/Elastic network interfaces/DetachNetworkInterface.md#)|Detaches an ENI from your Instance.|
|[DeleteNetworkInterface](intl.en-US/API Reference/Elastic network interfaces/DeleteNetworkInterface.md#)| Deletes an ENI.|
|[DescribeNetworkInterfaces](intl.en-US/API Reference/Elastic network interfaces/DescribeNetworkInterfaces.md#)| Describes the list of your ENIs.|
|[ModifyNetworkInterfaceAttribute](intl.en-US/API Reference/Elastic network interfaces/ModifyNetworkInterfaceAttribute.md#)|Modifies the attribute of an ENI.|

## Region and zone {#section_region_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#)|Describes the latest Alibaba Cloud regions that are available to you.|
|[DescribeZones](intl.en-US/API Reference/Regions/DescribeZones.md#)|Describes the zones that are available to you in a specified region.|

## Monitoring {#section_monitor_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[DescribeDisksFullStatus](intl.en-US/API Reference/Operations and monitoring/DescribeDisksFullStatus.md#)|Describes the full status information of a disk.|
|[DescribeDiskMonitorData](intl.en-US/API Reference/Operations and monitoring/DescribeDiskMonitorData.md#)|Describes the monitoring data of a specified disk.|
|[DescribeInstancesFullStatus](intl.en-US/API Reference/Operations and monitoring/DescribeInstancesFullStatus.md#)|Describes the full status information of the specified Instance.|
|[DescribeInstanceHistoryEvents](intl.en-US/API Reference/SSH key pairs/CreateKeyPair.md#)|Describes the history events of a specified Instance.|
|[DescribeInstanceMonitorData](intl.en-US/API Reference/Operations and monitoring/DescribeInstanceMonitorData.md#)| Describes all the instance-related monitoring data.|

## Tag {#section_tag_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[AddTags](intl.en-US/API Reference/Tags/AddTags.md#)|Adds or overwrites one or more tags to your ECS resource.|
|[RemoveTags](intl.en-US/API Reference/Tags/RemoveTags.md#)|Removes one or more tags from the specified ECS resource, such as instances, disks, snapshots, images, and security groups.|
|[DescribeTags](intl.en-US/API Reference/Tags/DescribeTags.md#)|Describes one or more of your available tags.|

## Cloud assistant {#section_cloudassistant_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[CreateCommand](intl.en-US/API Reference/Cloud assistant/CreateCommand.md#)| Creates a [cloud assistant](https://help.aliyun.com/document_detail/64601.html) command.|
|[InvokeCommand](intl.en-US/API Reference/Cloud assistant/InvokeCommand.md#)|Performs a specified command on the target Instances.|
|[StopInvocation](intl.en-US/API Reference/Cloud assistant/Stopinvention.md#)|Stops cloud assistant command processes that are in `Running` status on Instances.|
|[DeleteCommand](intl.en-US/API Reference/Cloud assistant/DeleteCommand.md#)|Deletes a created cloud assistant command.|
|[DescribeCommands](intl.en-US/API Reference/Cloud assistant/DescribeCommands.md#)|Describes the cloud assistant commands that you have created.|
|[DescribeInvocations](intl.en-US/API Reference/Cloud assistant/DescribeInvocations.md#)|Describes the cloud assistant command invocation list and status on your Instances.|
|[DescribeInvocationResults](intl.en-US/API Reference/Cloud assistant/DescribeInvocationResultsDescribeinvocationresults.md#)|Describes the invocation result of a cloud assistant command, that is, the actual Output information of a specified Instance.|
|[ModifyCommand](intl.en-US/API Reference/Cloud assistant/ModifyCommand.md#)|Modifies the parameters and content of a cloud assistant command.|

## Others {#section_other_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[CancelTask](intl.en-US/API Reference/Others/CancelTask.md#)|Cancels a specified active task.|
|[DescribeAvailableResource](intl.en-US/API Reference/Others/DescribeAvailableResource.md#)|Describes a list of the resources available in a certain zone.|
|[DescribeResourcesModification](intl.en-US/API Reference/Others/DescribeResourcesModification.md#)|Describes a list of the resources available in a certain zone.|
|[DescribeTasks](intl.en-US/API Reference/Others/DescribeTasks.md#)|Describes the progress of a specified asynchronous request.|
|[DescribeTaskAttribute](intl.en-US/API Reference/Others/DescribeTaskAttribute.md#)|Describes the details about one or more tasks.  Currently, the tasks that can be queried are the importing image action \([ImportImage](intl.en-US/API Reference/Images/ImportImage.md#)\) and the exporting image action \([ExportImage](intl.en-US/API Reference/Images/ExportImage.md#)\).|

