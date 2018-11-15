# API overview {#AvailableActions .reference}

See the following tables for the ECS APIs that are available to use.

For more information, see the [API Explorer](https://api.aliyun.com/).

## Instances {#section_vvj_q2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[RunInstances](reseller.en-US/API Reference/Instances/RunInstances.md#)|Creates a specified number of instances.|
|[CreateInstance](reseller.en-US/API Reference/Instances/CreateInstance.md#)|Creates an instance.|
|[StartInstance](reseller.en-US/API Reference/Instances/StartInstance.md#)|Starts a specified instance.|
|[StopInstance](reseller.en-US/API Reference/Instances/StopInstance.md#)|Stops a specified instance.|
|[Rebootinstance](reseller.en-US/API Reference/Instances/RebootInstance.md#)|Restarts an instance.|
|[DeleteInstance](reseller.en-US/API Reference/Instances/DeleteInstance.md#)|Releases an instance.|
|[AttachInstanceRamRole](reseller.en-US/API Reference/Instances/AttachInstanceRamRole.md#)|Attaches an instance RAM role to your Instance.|
|[DetachInstanceRamRole](reseller.en-US/API Reference/Instances/DetachInstanceRamRole.md#)|Detaches a RAM role from an instance.|
|[DescribeInstanceStatus](reseller.en-US/API Reference/Instances/DescribeInstanceStatus.md#)|Obtains the list of all your instances in batches with status information.|
|[DescribeInstances](reseller.en-US/API Reference/Instances/DescribeInstances.md#)|Describes details of your instances.|
|[DescribeInstanceVncUrl](reseller.en-US/API Reference/Instances/DescribeInstanceVncUrl.md#)|Describes the management terminal URL before connecting to an instance.|
|[DescribeUserdata](reseller.en-US/API Reference/Instances/DescribeUserdata.md#)|Describes the user-defined data of an Instance.|
|[DescribeInstanceAutoRenewAttribute](reseller.en-US/API Reference/Instances/DescribeInstanceAutoRenewAttribute.md#)|Queries the automatic renewal status of an instance.|
|[DescribeInstanceRamRole](reseller.en-US/API Reference/Instances/DescribeInstanceRamRole.md#)|Describes information related to the instance RAM role.|
|[DescribeSpotPriceHistory](reseller.en-US/API Reference/Instances/DescribeSpotPriceHistory.md#)|Describes the price history of the preemptible instances.  You can query the price records within 30 days at most.|
|[DescribeInstanceTypeFamilies](reseller.en-US/API Reference/Instances/DescribeInstanceTypeFamilies.md#)|Describes the resources list of instance type families provided by Alibaba Cloud ECS.|
|[DescribeInstanceTypes](reseller.en-US/API Reference/Instances/DescribeInstanceTypes.md#)|Describes the resources list of instance types provided by Alibaba Cloud ECS.|
|[ModifyInstanceVpcAttribute](reseller.en-US/API Reference/Instances/ModifyInstanceVpcAttribute.md#)|Modifies the attributes of a VPC to which a specified instance is connected.|
|[ModifyInstanceAttribute](reseller.en-US/API Reference/Instances/ModifyInstanceAttribute.md#)|Modifies the information of an Instance, such as the name, password, host name, and description of an instance.|
|[ModifyInstanceVncPasswd](reseller.en-US/API Reference/Instances/ModifyInstanceVncPasswd.md#)|Changes the password of management terminal used to connect a specified Instance.|
|[ModifyInstanceAutoReleaseTime](reseller.en-US/API Reference/Instances/ModifyInstanceAutoReleaseTime.md#)|Sets the automatic release time for a specified instance.|
|[ModifyInstanceAutoRenewAttribute](reseller.en-US/API Reference/Instances/ModifyInstanceAutoRenewAttribute.md#)|Modifies the information of an Instance, such as the name, password, host name, and description of an instance.|
|[ModifyInstanceSpec](reseller.en-US/API Reference/Instances/ModifyInstanceSpec.md#)|Changes the instance type or modifies the Internet bandwidth of a Pay-As-You-Go instance.|

## Launch templates {#section_fsy_hzw_d2b .section}

|Action|Description|
|:-----|:----------|
|[CreateLaunchTemplate](reseller.en-US/API Reference/Launch templates/CreateLaunchTemplate.md#)|Creates an instance launch template, or launch template for short. An instance launch template saves you the trouble of entering a large number of configuration parameters each time you create an instance.|
|[CreateLaunchTemplateVersion](reseller.en-US/API Reference/Launch templates/CreateLaunchTemplateVersion.md#)|Creates a version based on the specified instance launch template.|
|[DeleteLaunchTemplate](reseller.en-US/API Reference/Launch templates/DeleteLaunchTemplate.md#)|Deletes an instance launch template.|
|[DeleteLaunchTemplateVersion](reseller.en-US/API Reference/Launch templates/DeleteLaunchTemplateVersion.md#)|Deletes a specified instance launch template version. However, if the instance launch template version you intend to delete is the default version, you must use the [DeleteLaunchTemplate](reseller.en-US/API Reference/Launch templates/DeleteLaunchTemplate.md#) API to delete the entire instance launch template. |
|[DescribeLaunchTemplates](reseller.en-US/API Reference/Launch templates/DescribeLaunchTemplates.md#)|Queries available instance launch templates.|
|[DescribeLaunchTemplateVersions](reseller.en-US/API Reference/Launch templates/DescribeLaunchTemplateVersions.md#) |Queries instance launch template versions.|
|[ModifyLaunchTemplateDefaultVersion](reseller.en-US/API Reference/Launch templates/ModifyLaunchTemplateDefaultVersion.md#)|Sets a specified version of this template as the default version. If you do not specify a template version number when creating an instance \([RunInstances](reseller.en-US/API Reference/Instances/RunInstances.md#)\), default version is used.|

## Disks {#section_t3s_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[CreateDisk](reseller.en-US/API Reference/Disk/CreateDisk.md#)|Creates a portable data disk.|
|[DeleteDisk](reseller.en-US/API Reference/Disk/DeleteDisk.md#)|Releases an independent cloud disk when it is no longer in use.|
|[DescribeDisks](reseller.en-US/API Reference/Disk/DescribeDisks.md#)|Describes your available cloud disks.|
|[AttachDisk](reseller.en-US/API Reference/Disk/AttachDisk.md#)|Attaches a data disk to your Instance.|
|[DetachDisk](reseller.en-US/API Reference/Disk/DetachDisk.md#)|Detaches a cloud disk from a specified instance.|
|[ModifyDiskAttribute](reseller.en-US/API Reference/Disk/ModifyDiskAttribute.md#)|Modifies the attribute of your cloud disk.|
|[ReplaceSystemDisk](reseller.en-US/API Reference/Disk/ReplaceSystemDisk.md#)|Replaces the system disk or the operating system of an Instance.|
|[ReInitDisk](reseller.en-US/API Reference/Disk/ReInitDisk.md#)|Initializes a cloud disk to the initial state.|
|[ResetDisk](reseller.en-US/API Reference/Disk/ResetDisk.md#)|Rolls back a disk to a specified disk state by using one of its history disk snapshots.|
|[ResizeDisk](reseller.en-US/API Reference/Disk/ResizeDisk.md#)|Extends the size of a cloud disk.|

## Images {#section_image_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[CreateImage](reseller.en-US/API Reference/Images/CreateImage.md#)|Creates a custom image.|
|[ImportImage](reseller.en-US/API Reference/Images/ImportImage.md#)|Imports on-premises image files to the Alibaba Cloud ECS.|
|[ExportImage](reseller.en-US/API Reference/Images/ExportImage.md#)|Exports a custom image to an OSS bucket in the same region as the custom image.|
|[CopyImage](reseller.en-US/API Reference/Images/CopyImage.md#)|Copies a custom image from one region to other regions.|
|[CancelCopyImage](reseller.en-US/API Reference/Images/CancelCopyImage.md#)|Cancels a pending image copy \(`CopyImage`\) operation.|
|[DescribeImages](reseller.en-US/API Reference/Images/DescribeImages.md#)|Describes your available image.|
|[DeleteImage](reseller.en-US/API Reference/Images/Deleteimage.md#)|Deletes a specified custom image.|
|[DescribeImageSharePermission](reseller.en-US/API Reference/Images/DescribeImageSharePermission.md#)|Describes all the authorized users to whom one of your custom image is shared.|
|[ModifyImageAttribute](reseller.en-US/API Reference/Images/ModifyImageAttribute.md#)|Modifies the name and description of a custom image.|
|[ModifyImageSharePermission](reseller.en-US/API Reference/Images/ModifyImageSharePermission.md#)|Shares a custom image to other Alibaba Cloud users.|

## Snapshots {#section_snapshot_t2h_vdb .section}

|Actions|Description|
|:------|:----------|
|[CreateSnapshot](reseller.en-US/API Reference/Snapshots/CreateSnapshot.md#)|Creates a snapshot for a specified disk device.|
|[CreateAutoSnapshotPolicy](reseller.en-US/API Reference/Snapshots/CreateAutoSnapshotPolicy.md#)|Creates an automatic snapshot policy.|
|[ApplyAutoSnapshotPolicy](reseller.en-US/API Reference/Snapshots/ApplyAutoSnapshotPolicy.md#)|Applies automatic snapshot policies to one or more disks.|
|[DeleteSnapshot](reseller.en-US/API Reference/Snapshots/DeleteSnapshot.md#)|Deletes a specified snapshot.|
|[CancelAutoSnapshotPolicy](reseller.en-US/API Reference/Snapshots/CancelAutoSnapshotPolicy.md#)|Cancels the automatic snapshot policy for one or more disks.|
|[DeleteAutoSnapshotPolicy](reseller.en-US/API Reference/Snapshots/DeleteAutoSnapshotPolicy.md#)|Creates an automatic snapshot policy.|
|[DescribeAutoSnapshotPolicyEx](reseller.en-US/API Reference/Snapshots/DescribeAutoSnapshotPolicyEx.md#)|Describes your available automatic snapshot policies.|
|[DescribeSnapshots](reseller.en-US/API Reference/Snapshots/DescribeSnapshots.md#)|Describes one or more of your available snapshots.|
|[DescribeSnapshotLinks](reseller.en-US/API Reference/Snapshots/DescribeSnapshotLinks.md#)|Describes the snapshot chains of one or more disks.|
|[ModifyAutoSnapshotPolicyEx](reseller.en-US/API Reference/Snapshots/ModifyAutoSnapshotPolicyEx.md#)|Creates an automatic snapshot policy.|

## Network {#section_network_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[AllocatePublicIpAddress](reseller.en-US/API Reference/Networks/AllocatePublicIpAddress.md#)|Assigns an Internet IP address to an instance.|
|[ConvertNatPublicIpToEip](reseller.en-US/API Reference/Networks/ConvertNatPublicIpToEip.md#)|Changes the public IP \(NatPublicIp\) of a VPC-Connected instance to an Elastic IP \(EIP\).|
|[AttachClassicLinkVpc](reseller.en-US/API Reference/Networks/AttachClassicLinkVpc.md#)|Links a classic network instance to a VPC, which allows the classic network instance communicating with the resources that are in the intranet of a VPC.|
|[DetachClassicLinkVpc](reseller.en-US/API Reference/Networks/DetachClassicLinkVpc.md#)|Unlinks a classic network-connected instance from the VPC.|
|[DescribeBandwidthLimitation](reseller.en-US/API Reference/Networks/DescribeBandwidthLimitation.md#)|Describes a list of bandwidth resources.|
|[DescribeClassicLinkInstances](reseller.en-US/API Reference/Networks/DescribeClassicLinkInstances.md#)|Describes one or more of your classic network-connected instances that have established ClassicLink with a VPC.|
|[ModifyInstanceNetworkSpec](reseller.en-US/API Reference/Networks/ModifyInstanceNetworkSpec.md#)|Modifies the bandwidth configuration of your ECS instance.|

For more information about the APIs for Virtual Private Cloud \(VPC\), see [VPC API  References](../../../../reseller.en-US/API reference/API overview.md#).

## Security groups {#section_securitygroup_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[CreateSecurityGroup](reseller.en-US/API Reference/Security groups/CreateSecurityGroup.md#)|Creates a security group. |
|[AuthorizeSecurityGroup](reseller.en-US/API Reference/Security groups/AuthorizeSecurityGroup.md#)|Adds an inbound rule for a security group.|
|[AuthorizeSecurityGroupEgress](reseller.en-US/API Reference/Security groups/AuthorizeSecurityGroupEgress.md#)|Adds an outbound rule for a security group.|
|[RevokeSecurityGroup](reseller.en-US/API Reference/Security groups/RevokeSecurityGroup.md#)|Deletes an inbound rule from a security group.|
|[RevokeSecurityGroupEgress](reseller.en-US/API Reference/Security groups/RevokeSecurityGroupEgress.md#)|Deletes an outbound rule from a security group.|
|[JoinSecurityGroup](reseller.en-US/API Reference/Security groups/JoinSecurityGroup.md#)|Adds an instance to a specified security group.|
|[LeaveSecurityGroup](reseller.en-US/API Reference/Security groups/LeaveSecurityGroup.md#)|Removes an instance from a specified security group.|
|[DeleteSecurityGroup](reseller.en-US/API Reference/Security groups/DeleteSecurityGroup.md#)|Deletes a security group.|
|[DescribeSecurityGroupAttribute](reseller.en-US/API Reference/Security groups/DescribeSecurityGroupAttribute.md#)|Describes your security groups.|
|[DescribeSecurityGroups](reseller.en-US/API Reference/Security groups/DescribeSecurityGroups.md#)|Describes the basic information about your security groups, such as the security group ID and description.|
|[DescribeSecurityGroupReferences](reseller.en-US/API Reference/Security groups/DescribeSecurityGroupReferences.md#)|Describes whether a specified security group has been authorized by other security group or not.|
|[ModifySecurityGroupAttribute](reseller.en-US/API Reference/Security groups/ModifySecurityGroupAttribute.md#)|Modifies the properties of the specified security group, including the security group name and description.|
|[ModifySecurityGroupPolicy](reseller.en-US/API Reference/Security groups/ModifySecurityGroupPolicy.md#)|Modifies the intranet communication policy of a security group.|
|[ModifySecurityGroupRule](reseller.en-US/API Reference/Security groups/ModifySecurityGroupRule.md#)|Modifies the description of a security group inbound rule.|

## SSH key pair {#section_keypair_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[CreateKeyPair](reseller.en-US/API Reference/SSH key pairs/CreateKeyPair.md#)|Creates an SSH key pair.|
|[ImportKeyPair](reseller.en-US/API Reference/SSH key pairs/ImportKeyPair.md#)|Imports the public key of an SSH key pair that you create with other key pair generators into one of the Alibaba Cloud regions.|
|[AttachKeyPair](reseller.en-US/API Reference/SSH key pairs/AttachKeyPair.md#)|Attaches an SSH key pair to one or more of your Linux instances.|
|[DetachKeyPair](reseller.en-US/API Reference/SSH key pairs/DetachKeyPair.md#)|Detaches an SSH key pair from one or more of your Linux instances.|
|[DeleteKeyPairs](reseller.en-US/API Reference/SSH key pairs/DeleteKeyPairs.md#)|Deletes one or more of your SSH key pairs.|
|[DescribeKeyPairs](reseller.en-US/API Reference/SSH key pairs/DescribeKeyPairs.md#)|Describes one or more of your SSH key pairs.|

## ENI {#section_networkinterface_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[CreateNetworkInterface](reseller.en-US/API Reference/Elastic network interfaces/CreateNetworkInterface.md#)|Creates an ENI \(Elastic Network Interface\).|
|[AttachNetworkInterface](reseller.en-US/API Reference/Elastic network interfaces/AttachNetworkInterface .md#)|Attaches an ENI to a VPC-connected instance.|
|[DetachNetworkInterface](reseller.en-US/API Reference/Elastic network interfaces/DetachNetworkInterface.md#)|Detaches an ENI from your Instance.|
|[DeleteNetworkInterface](reseller.en-US/API Reference/Elastic network interfaces/DeleteNetworkInterface.md#)|Deletes an ENI.|
|[DescribeNetworkInterfaces](reseller.en-US/API Reference/Elastic network interfaces/DescribeNetworkInterfaces.md#)|Describes the list of your ENIs.|
|[ModifyNetworkInterfaceAttribute](reseller.en-US/API Reference/Elastic network interfaces/ModifyNetworkInterfaceAttribute.md#)|Modifies the attribute of an ENI.|

## Monitoring {#section_monitor_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[DescribeDisksFullStatus](reseller.en-US/API Reference/Operations and monitoring/DescribeDisksFullStatus.md#)|Describes the lifecycle status and health status information of a disk.|
|[DescribeDiskMonitorData](reseller.en-US/API Reference/Operations and monitoring/DescribeDiskMonitorData.md#)|Queries the monitoring data of a specified disk.|
|[DescribeInstancesFullStatus](reseller.en-US/API Reference/Operations and monitoring/DescribeInstancesFullStatus.md#)|Describes the full status information of the specified Instance.|
|[DescribeInstanceHistoryEvents](reseller.en-US/API Reference/SSH key pairs/CreateKeyPair.md#)|Describes the history events of a specified Instance.|
|[DescribeInstanceMonitorData](reseller.en-US/API Reference/Operations and monitoring/DescribeInstanceMonitorData.md#)|Describes all the instance-related monitoring data.|

## Tags {#section_tag_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[AddTags](reseller.en-US/API Reference/Tags/AddTags.md#)|Adds or overwrites one or more tags to your ECS resource.|
|[RemoveTags](reseller.en-US/API Reference/Tags/RemoveTags.md#)|Removes one or more tags from the specified ECS resource, such as instances, disks, snapshots, images, and security groups.|
|[DescribeTags](reseller.en-US/API Reference/Tags/DescribeTags.md#)|Describes one or more of your available tags.|

## Cloud assistant {#section_cloudassistant_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[CreateCommand](reseller.en-US/API Reference/Cloud assistant/CreateCommand.md#)|Creates a [cloud assistant](https://help.aliyun.com/document_detail/64601.html) command.|
|[InvokeCommand](reseller.en-US/API Reference/Cloud assistant/InvokeCommand.md#)|Performs a specified command on the target Instances.|
|[StopInvocation](reseller.en-US/API Reference/Cloud assistant/StopInvocation.md#)|Stops cloud assistant command processes that are in `Running` status for one or more instances.|
|[DeleteCommand](reseller.en-US/API Reference/Cloud assistant/DeleteCommand.md#)|Deletes a created cloud assistant command.|
|[DescribeCommands](reseller.en-US/API Reference/Cloud assistant/DescribeCommands.md#)|Describes the cloud assistant commands that you have created.|
|[DescribeInvocations](reseller.en-US/API Reference/Cloud assistant/DescribeInvocations.md#)|Describes the cloud assistant command invocation list and status on your Instances.|
|[DescribeInvocationResults](reseller.en-US/API Reference/Cloud assistant/DescribeInvocationResults.md#)|Describes the invocation result of a cloud assistant command. The actual output information of a specified instance is returned.|
|[ModifyCommand](reseller.en-US/API Reference/Cloud assistant/ModifyCommand.md#)|Modifies the parameters and content of a cloud assistant command.|

## Others {#section_other_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[CancelTask](reseller.en-US/API Reference/Others/CancelTask.md#)|Cancels a specified active task.|
|[DescribeTasks](reseller.en-US/API Reference/Others/DescribeTasks.md#)|Describes the progress of a specified asynchronous request.|
|[DescribeTaskAttribute](reseller.en-US/API Reference/Others/DescribeTaskAttribute.md#)|Describes the details about one or more tasks.  Currently, the tasks that can be queried are the importing image action [ImportImage](reseller.en-US/API Reference/Images/ImportImage.md#) and the exporting image action [ExportImage](reseller.en-US/API Reference/Images/ExportImage.md#).|

## Regions and zones {#section_region_t2h_vdb .section}

|Action|Description|
|:-----|:----------|
|[DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#)|Describes the latest Alibaba Cloud regions that are available to you.|
|[DescribeZones](reseller.en-US/API Reference/Regions/DescribeZones.md#)|Describes the zones that are available to you in a specified region.|
|[DescribeAvailableResource](reseller.en-US/API Reference/Regions/DescribeAvailableResource.md#)|Describes a list of the resources available in a certain zone.|
|[DescribeResourcesModification](reseller.en-US/API Reference/Regions/DescribeResourcesModification.md#)|Describes a list of the resources available in a certain zone.|

