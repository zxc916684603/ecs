# API overview {#AvailableActions .reference}

See the following tables for the ECS APIs that are available to use.

For more information, see [API Explorer](https://api.aliyun.com/).

## Instances {#section_vvj_q2h_vdb .section}

|API|Description|
|:--|:----------|
|[RunInstances](intl.en-US/API Reference/Instances/RunInstances.md#)|Creates a specified number of Subscription, Pay-As-You-Go, or preemptible instances.|
|[CreateInstance](intl.en-US/API Reference/Instances/CreateInstance.md#)|Creates a Subscription, Pay-As-You-Go, or preemptible instance.|
|[StartInstance](intl.en-US/API Reference/Instances/StartInstance.md#)|Starts a specified instance.|
|[StopInstance](intl.en-US/API Reference/Instances/StopInstance.md#)|Stops a specified instance.|
|[RebootInstance](intl.en-US/API Reference/Instances/RebootInstance.md#)|Restarts a specified instance.|
|[DeleteInstance](intl.en-US/API Reference/Instances/DeleteInstance.md#)|Releases a specified instance.|
|[AttachInstanceRamRole](intl.en-US/API Reference/Instances/AttachInstanceRamRole.md#)|Attaches a RAM role to your Instance.|
|[DetachInstanceRamRole](intl.en-US/API Reference/Instances/DetachInstanceRamRole.md#)|Detaches a RAM role from an instance.|
|[DescribeInstanceStatus](intl.en-US/API Reference/Instances/DescribeInstanceStatus.md#)|Obtains the list of all your instances in batches with status information.|
|[DescribeInstances](intl.en-US/API Reference/Instances/DescribeInstances.md#)|Describes details of your instances.|
|[DescribeInstanceVncUrl](intl.en-US/API Reference/Instances/DescribeInstanceVncUrl.md#)|Describes the management terminal URL before connecting to an instance.|
|[DescribeUserdata](intl.en-US/API Reference/Instances/DescribeUserdata.md#)|Describes the user-defined data of an Instance.|
|[DescribeInstanceAutoRenewAttribute](intl.en-US/API Reference/Instances/DescribeInstanceAutoRenewAttribute.md#)|Queries the automatic renewal status of an instance.|
|[DescribeInstanceRamRole](intl.en-US/API Reference/Instances/DescribeInstanceRamRole.md#)|Describes information related to the instance RAM role for one or more instances.|
|[DescribeSpotPriceHistory](intl.en-US/API Reference/Instances/DescribeSpotPriceHistory.md#)|Describes the price history of the preemptible instances. You can query the price records within 30 days at most.|
|[DescribeInstanceTypeFamilies](intl.en-US/API Reference/Instances/DescribeInstanceTypeFamilies.md#)|Describes the list of instance type families provided by Alibaba Cloud ECS.|
|[DescribeInstanceTypes](intl.en-US/API Reference/Instances/DescribeInstanceTypes.md#)|Describes the list of instance types provided by Alibaba Cloud ECS.|
|[ModifyInstanceVpcAttribute](intl.en-US/API Reference/Instances/ModifyInstanceVpcAttribute.md#)|Modifies the attributes of a VPC to which a specified instance belongs.|
|[ModifyInstanceAttribute](intl.en-US/API Reference/Instances/ModifyInstanceAttribute.md#)|Modifies the information on an instance, such as the name, password, and security group.|
|[ModifyInstanceVncPasswd](intl.en-US/API Reference/Instances/ModifyInstanceVncPasswd.md#)|Modifies the password of management terminal used to connect a specified Instance.|
|[ModifyInstanceAutoReleaseTime](intl.en-US/API Reference/Instances/ModifyInstanceAutoReleaseTime.md#)|Sets the auto release time for a specified instance.|
|[ModifyInstanceAutoRenewAttribute](intl.en-US/API Reference/Instances/ModifyInstanceAutoRenewAttribute.md#)|Sets the auto renewal attribute for a specified instance.|
|[ModifyInstanceSpec](intl.en-US/API Reference/Instances/ModifyInstanceSpec.md#)|Modifies the instance type or Internet bandwidth of a Pay-As-You-Go instance.|
|[ModifyPrepayInstanceSpec](intl.en-US/API Reference/Instances/ModifyPrepayInstanceSpec.md#)|Upgrades or downgrades the instance specification.|

## Launch templates {#section_fsy_hzw_d2b .section}

|API|Description|
|:--|:----------|
|[CreateLaunchTemplate](intl.en-US/API Reference/Launch templates/CreateLaunchTemplate.md#)|Creates an instance launch template \(launch template for short\). An instance launch template allows you to automatically set configuration parameters that are used each time you create a new instance.|
|[CreateLaunchTemplateVersion](intl.en-US/API Reference/Launch templates/CreateLaunchTemplateVersion.md#)|Creates a version based on the specified instance launch template.|
|[DeleteLaunchTemplate](intl.en-US/API Reference/Launch templates/DeleteLaunchTemplate.md#)|Deletes an instance launch template.|
|[DeleteLaunchTemplateVersion](intl.en-US/API Reference/Launch templates/DeleteLaunchTemplateVersion.md#)|Deletes a specified instance launch template version. However, if you want to delete the default version, you must first use the [DeleteLaunchTemplate](intl.en-US/API Reference/Launch templates/DeleteLaunchTemplate.md#) API to delete the entire instance launch template.|
|[DescribeLaunchTemplates](intl.en-US/API Reference/Launch templates/DescribeLaunchTemplates.md#)|Describes available instance launch templates.|
|[DescribeLaunchTemplateVersions](intl.en-US/API Reference/Launch templates/DescribeLaunchTemplateVersions.md#) |Describes instance launch template versions.|
|[ModifyLaunchTemplateDefaultVersion](intl.en-US/API Reference/Launch templates/ModifyLaunchTemplateDefaultVersion.md#)|Sets a specified version of this template as the default version. If you do not specify a template version when creating an instance \([RunInstances](intl.en-US/API Reference/Instances/RunInstances.md#)\), the default version is used.|

## Disks {#section_t3s_t2h_vdb .section}

|API|Description|
|:--|:----------|
|[CreateDisk](intl.en-US/API Reference/Disk/CreateDisk.md#)|Creates a data disk from a cloud disk.|
|[DeleteDisk](intl.en-US/API Reference/Disk/DeleteDisk.md#)|Releases a cloud disk.|
|[DescribeDisks](intl.en-US/API Reference/Disk/DescribeDisks.md#)|Describes your available cloud disks.|
|[AttachDisk](intl.en-US/API Reference/Disk/AttachDisk.md#)|Attaches a data disk to your Instance.|
|[DetachDisk](intl.en-US/API Reference/Disk/DetachDisk.md#)|Detaches a cloud disk from a specified instance.|
|[ModifyDiskChargeType](intl.en-US/API Reference/Disk/ModifyDiskChargeType.md#)|Modifies the billing method for up to 16 disks that are attached to an instance.|
|[ModifyDiskAttribute](intl.en-US/API Reference/Disk/ModifyDiskAttribute.md#)|Modifies the attributes of your cloud disk.|
|[ReplaceSystemDisk](intl.en-US/API Reference/Disk/ReplaceSystemDisk.md#)|Replaces the system disk or the operating system of an Instance.|
|[ReInitDisk](intl.en-US/API Reference/Disk/ReInitDisk.md#)|Initializes a cloud disk to the initial state.|
|[ResetDisk](intl.en-US/API Reference/Disk/ResetDisk.md#)|Rolls back a disk to a specified disk state by using one of its historic disk snapshots.|
|[ResizeDisk](intl.en-US/API Reference/Disk/ResizeDisk.md#)|Expands the size of a cloud disk.|

## Images {#section_image_t2h_vdb .section}

|API|Description|
|:--|:----------|
|[CreateImage](intl.en-US/API Reference/Images/CreateImage.md#)|Creates a custom image.|
|[ImportImage](intl.en-US/API Reference/Images/ImportImage.md#)|Imports your locally saved image files to Alibaba Cloud ECS. Such images will appear in the corresponding regions as custom images.|
|[ExportImage](intl.en-US/API Reference/Images/ExportImage.md#)|Exports a custom image to an OSS bucket in the same region as the custom image.|
|[CopyImage](intl.en-US/API Reference/Images/CopyImage.md#)|Copies a custom image from one region to other regions.|
|[CancelCopyImage](intl.en-US/API Reference/Images/CancelCopyImage.md#)|Cancels an ongoing image copy \(`CopyImage`\) operation.|
|[DescribeImages](intl.en-US/API Reference/Images/DescribeImages.md#)|Describes your available images.|
|[DeleteImage](intl.en-US/API Reference/Images/Deleteimage.md#)|Deletes a specified custom image.|
|[DescribeImageSharePermission](intl.en-US/API Reference/Images/DescribeImageSharePermission.md#)|Describes all the users with whom a custom image is shared.|
|[ModifyImageAttribute](intl.en-US/API Reference/Images/ModifyImageAttribute.md#)|Modifies the name and description of a custom image.|
|[ModifyImageSharePermission](intl.en-US/API Reference/Images/ModifyImageSharePermission.md#)|Shares a custom image to other Alibaba Cloud users.|

## Snapshots {#section_snapshot_t2h_vdb .section}

|API|Description|
|:--|:----------|
|[CreateSnapshot](intl.en-US/API Reference/Snapshots/CreateSnapshot.md#)|Creates a snapshot for a specified disk.|
|[CreateAutoSnapshotPolicy](intl.en-US/API Reference/Snapshots/CreateAutoSnapshotPolicy.md#)|Creates an automatic snapshot policy.|
|[ApplyAutoSnapshotPolicy](intl.en-US/API Reference/Snapshots/ApplyAutoSnapshotPolicy.md#)|Applies automatic snapshot policies to one or more disks.|
|[DeleteSnapshot](intl.en-US/API Reference/Snapshots/DeleteSnapshot.md#)|Deletes a specified snapshot.|
|[CancelAutoSnapshotPolicy](intl.en-US/API Reference/Snapshots/CancelAutoSnapshotPolicy.md#)|Cancels the automatic snapshot policy for one or more disks.|
|[DeleteAutoSnapshotPolicy](intl.en-US/API Reference/Snapshots/DeleteAutoSnapshotPolicy.md#)|Creates an automatic snapshot policy.|
|[DescribeAutoSnapshotPolicyEx](intl.en-US/API Reference/Snapshots/DescribeAutoSnapshotPolicyEx.md#)|Describes your available automatic snapshot policies.|
|[DescribeSnapshots](intl.en-US/API Reference/Snapshots/DescribeSnapshots.md#)|Describes all the disk snapshots for a specified instance.|
|[DescribeSnapshotLinks](intl.en-US/API Reference/Snapshots/DescribeSnapshotLinks.md#)|Describes the snapshot chains of one or more disks.|
|[ModifyAutoSnapshotPolicyEx](intl.en-US/API Reference/Snapshots/ModifyAutoSnapshotPolicyEx.md#)|Modifies an automatic snapshot policy.|
|[DescribeSnapshotsUsage](intl.en-US/API Reference/Snapshots/DescribeSnapshotsUsage.md#)|Describes the quantity and size of snapshots in a region.|
|[DescribeSnapshotPackage](intl.en-US/API Reference/Snapshots/DescribeSnapshotPackage.md#)|Describes your purchased OSS storage plans in an Alibaba Cloud region. These storage plans can be used for snapshot storage.|

## Security groups {#section_securitygroup_t2h_vdb .section}

|API|Description|
|:--|:----------|
|[CreateSecurityGroup](intl.en-US/API Reference/Security groups/CreateSecurityGroup.md#)|Creates a security group.|
|[AuthorizeSecurityGroup](intl.en-US/API Reference/Security groups/AuthorizeSecurityGroup.md#)|Adds an inbound rule for a security group.|
|[AuthorizeSecurityGroupEgress](intl.en-US/API Reference/Security groups/AuthorizeSecurityGroupEgress.md#)|Adds an outbound rule for a security group.|
|[RevokeSecurityGroup](intl.en-US/API Reference/Security groups/RevokeSecurityGroup.md#)|Deletes an inbound rule from a security group.|
|[RevokeSecurityGroupEgress](intl.en-US/API Reference/Security groups/RevokeSecurityGroupEgress.md#)|Deletes an outbound rule from a security group.|
|[JoinSecurityGroup](intl.en-US/API Reference/Security groups/JoinSecurityGroup.md#)|Adds an instance to a specified security group.|
|[LeaveSecurityGroup](intl.en-US/API Reference/Security groups/LeaveSecurityGroup.md#)|Removes an instance from a specified security group.|
|[DeleteSecurityGroup](intl.en-US/API Reference/Security groups/DeleteSecurityGroup.md#)|Deletes a security group.|
|[DescribeSecurityGroupAttribute](intl.en-US/API Reference/Security groups/DescribeSecurityGroupAttribute.md#)|Describes your security groups in detail.|
|[DescribeSecurityGroups](intl.en-US/API Reference/Security groups/DescribeSecurityGroups.md#)|Describes the basic information about your security groups, such as the security group ID and description.|
|[DescribeSecurityGroupReferences](intl.en-US/API Reference/Security groups/DescribeSecurityGroupReferences.md#)|Describes whether a specified security group has been authorized by other security groups.|
|[ModifySecurityGroupAttribute](intl.en-US/API Reference/Security groups/ModifySecurityGroupAttribute.md#)|Modifies the attributes of a specified security group, including the security group name and description.|
|[ModifySecurityGroupPolicy](intl.en-US/API Reference/Security groups/ModifySecurityGroupPolicy.md#)|Modifies the intranet communication policy of a security group.|
|[ModifySecurityGroupRule](intl.en-US/API Reference/Security groups/ModifySecurityGroupRule.md#)|Modifies the description of a security group inbound rule.|

## Deployment sets {#DeploymentSet .section}

|API|Description|
|:--|:----------|
|[CreateDeploymentSetId](intl.en-US/API Reference/Deployment sets/CreateDeploymentSet.md#)|Creates a deployment set in a specified region.|
|[ModifyInstanceDeployment](intl.en-US/API Reference/Deployment sets/ModifyInstanceDeployment.md#)|Migrates an ECS instance to another host in the same region.|
|[ModifyDeploymentSetAttributes](intl.en-US/API Reference/Deployment sets/ModifyDeploymentSetAttributes.md#)|Adds an instance to a deployment set or migrates an instance to another deployment set.|
|[DescribeDeploymentSets](intl.en-US/API Reference/Deployment sets/DescribeDeploymentSets.md#)|Describes the attributes of one or more deployment sets.|
|[DeleteDeploymentSet](intl.en-US/API Reference/Deployment sets/DeleteDeploymentSet.md#)|Deletes a deployment set.|

## SSH key pairs {#section_keypair_t2h_vdb .section}

|API|Description|
|:--|:----------|
|[CreateKeyPair](intl.en-US/API Reference/SSH key pairs/CreateKeyPair.md#)|Creates an SSH key pair.|
|[ImportKeyPair](intl.en-US/API Reference/SSH key pairs/ImportKeyPair.md#)|Imports the public key of an SSH key pair that is created by other key pair generators.|
|[AttachKeyPair](intl.en-US/API Reference/SSH key pairs/AttachKeyPair.md#)|Attaches an SSH key pair to one or more Linux instances.|
|[DetachKeyPair](intl.en-US/API Reference/SSH key pairs/DetachKeyPair.md#)|Detaches an SSH key pair from one or more Linux instances.|
|[DeleteKeyPairs](intl.en-US/API Reference/SSH key pairs/DeleteKeyPairs.md#)|Deletes one or more SSH key pairs.|
|[DescribeKeyPairs](intl.en-US/API Reference/SSH key pairs/DescribeKeyPairs.md#)|Describes one or more SSH key pairs.|

## Network {#section_network_t2h_vdb .section}

|API|Description|
|:--|:----------|
|[AllocatePublicIpAddress](intl.en-US/API Reference/Networks/AllocatePublicIpAddress.md#)|Assigns an Internet IP address to an instance.|
|[ConvertNatPublicIpToEip](intl.en-US/API Reference/Networks/ConvertNatPublicIpToEip.md#)|Changes the Internet IP address \(NatPublicIp\) of a VPC instance to an Elastic IP \(EIP\).|
|[AttachClassicLinkVpc](intl.en-US/API Reference/Networks/AttachClassicLinkVpc.md#)|Links a classic network instance to a VPC so that the classic network instance can communicate with the resources in the VPC over the intranet.|
|[DetachClassicLinkVpc](intl.en-US/API Reference/Networks/DetachClassicLinkVpc.md#)|Removes the link between a classic network instance and a VPC.|
|[DescribeBandwidthLimitation](intl.en-US/API Reference/Networks/DescribeBandwidthLimitation.md#)|Describes a list of bandwidth resources.|
|[DescribeClassicLinkInstances](intl.en-US/API Reference/Networks/DescribeClassicLinkInstances.md#)|Describes one or more classic network instances that have established links with a VPC.|
|[ModifyInstanceNetworkSpec](intl.en-US/API Reference/Networks/ModifyInstanceNetworkSpec.md#)|Modifies the bandwidth configuration for a specified instance.|

For more information about the APIs for VPCs, see [API reference of VPCs](../../../../../intl.en-US/API reference/API overview.md#).

## ENIs {#section_networkinterface_t2h_vdb .section}

|API|Description|
|:--|:----------|
|[CreateNetworkInterface](intl.en-US/API Reference/Elastic network interfaces/CreateNetworkInterface.md#)|Creates an Elastic Network Interface \(ENI\).|
|[AttachNetworkInterface](intl.en-US/API Reference/Elastic network interfaces/AttachNetworkInterface .md#)|Attaches an ENI to a VPC instance.|
|[DetachNetworkInterface](intl.en-US/API Reference/Elastic network interfaces/DetachNetworkInterface.md#)|Detaches an ENI from an instance.|
|[DeleteNetworkInterface](intl.en-US/API Reference/Elastic network interfaces/DeleteNetworkInterface.md#)|Deletes an ENI.|
|[DescribeNetworkInterfaces](intl.en-US/API Reference/Elastic network interfaces/DescribeNetworkInterfaces.md#)|Describes the list of ENIs.|
|[ModifyNetworkInterfaceAttribute](intl.en-US/API Reference/Elastic network interfaces/ModifyNetworkInterfaceAttribute.md#)|Modifies the attributes of an ENI.|
|[AssignPrivateIpAddresses](intl.en-US/API Reference/Elastic network interfaces/AssignPrivateIpAddresses.md#)|Assigns one or more secondary private IP addresses to an ENI. Specifically, you can specify private IP addresses within the CIDR block of the VSwitch to which an ENI belongs. Alternatively, you can specify the number of private IP addresses for ECS to assign them automatically.|
|[UnassignPrivateIpAddresses](intl.en-US/API Reference/Elastic network interfaces/UnassignPrivateIpAddresses.md#)|Releases one or more secondary private IP addresses from an ENI.|

## System events {#section_eqs_vyd_kgb .section}

|API|Description|
|:--|:----------|
|[DescribeDisksFullStatus](intl.en-US/API Reference/System event/DescribeDisksFullStatus.md#)|Describes all the status information on a disk.|
|[CreateSimulatedSystemEvents](intl.en-US/API Reference/System event/CreateSimulatedSystemEvents.md#)|Schedules simulated system events for one or more ECS instances. Simulated system events do not occur in reality, nor do they affect ECS instances.|
|[CancelSimulatedSystemEvents](intl.en-US/API Reference/System event/CancelSimulatedSystemEvents.md#)|Cancels one or more simulated system events that are in the `Scheduled` or `Executing` status. After you cancel a simulated system event, the simulated event is in the `Canceled` status.|
|[DescribeInstancesFullStatus](intl.en-US/API Reference/System event/DescribeInstancesFullStatus.md#)|Describes all the status information on an instance.|
|[DescribeInstanceHistoryEvents](intl.en-US/API Reference/System event/DescribeInstanceHistoryEvents.md#)|Describes the inactive historic events of a specified Instance. The maximum length of query period is two months.|

## O&M and monitoring {#section_monitor_t2h_vdb .section}

|API|Description|
|:--|:----------|
|[DescribeDiskMonitorData](intl.en-US/API Reference/Operations and monitoring/DescribeDiskMonitorData.md#)|Describes the usage information on a specified disk within a certain period of time.|
|[DescribeInstanceMonitorData](intl.en-US/API Reference/Operations and monitoring/DescribeInstanceMonitorData.md#)|Describes all the monitoring data on an instance. The query results can be displayed on multiple pages.|
|[GetInstanceScreenshot](intl.en-US/API Reference/Operations and monitoring/GetInstanceScreenshot.md#)|Obtains screenshot information on an instance.|
|[GetInstanceConsoleOutput](intl.en-US/API Reference/Operations and monitoring/GetInstanceConsoleOutput.md#)|Obtains the command line output of an instance. The returned output is Base64-encoded.|
|[DescribeEniMonitorData](intl.en-US/API Reference/Operations and monitoring/DescribeEniMonitorData.md#)|Describes the traffic information on a secondary ENI within a specified period.|

## Cloud Assistant {#section_cloudassistant_t2h_vdb .section}

|API|Description|
|:--|:----------|
|[CreateCommand](intl.en-US/API Reference/Cloud assistant/CreateCommand.md#)|Creates a [Cloud Assistant](../../../../../intl.en-US/Product Introduction/Cloud assistant.md#) command.|
|[InvokeCommand](intl.en-US/API Reference/Cloud assistant/InvokeCommand.md#)|Executes a specified command on the target instances.|
|[StopInvocation](intl.en-US/API Reference/Cloud assistant/StopInvocation.md#)|Stops Cloud Assistant command processes that are in the `Running` status on the target instances.|
|[DeleteCommand](intl.en-US/API Reference/Cloud assistant/DeleteCommand.md#)|Deletes a created Cloud Assistant command.|
|[DescribeCommands](intl.en-US/API Reference/Cloud assistant/DescribeCommands.md#)|Describes the Cloud Assistant commands that you have created.|
|[DescribeInvocations](intl.en-US/API Reference/Cloud assistant/DescribeInvocations.md#)|Describes the invocation list and status of Cloud Assistant commands on your instances.|
|[DescribeInvocationResults](intl.en-US/API Reference/Cloud assistant/DescribeInvocationResults.md#)|Describes the invocation result of a Cloud Assistant command, namely the actual output on a specified instance.|
|[ModifyCommand](intl.en-US/API Reference/Cloud assistant/ModifyCommand.md#)|Modifies the parameters and content of a Cloud Assistant command.|

## Tags {#section_tag_t2h_vdb .section}

|API|Description|
|:--|:----------|
|[AddTags](intl.en-US/API Reference/Tags/AddTags.md#)|Adds one or more tags to your ECS resources or overwrites the existing tags.|
|[RemoveTags](intl.en-US/API Reference/Tags/RemoveTags.md#)|Removes one or more tags from the specified ECS resources, such as instances, disks, snapshots, images, and security groups.|
|[DescribeTags](intl.en-US/API Reference/Tags/DescribeTags.md#)|Describes the tags that are available to you.|

## Regions and zones {#section_region_t2h_vdb .section}

|API|Description|
|:--|:----------|
|[DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#)|Describes the Alibaba Cloud regions that are available to you.|
|[DescribeZones](intl.en-US/API Reference/Regions/DescribeZones.md#)|Describes the zones that are available to you in a specified region.|
|[DescribeAvailableResource](intl.en-US/API Reference/Regions/DescribeAvailableResource.md#)|Describes a list of the resources available in a certain zone.|
|[DescribeResourcesModification](intl.en-US/API Reference/Regions/DescribeResourcesModification.md#)|Describes a list of resources available in a certain zone upon upgrading or downgrading an instance type or system disk.|

## Other APIs {#section_other_t2h_vdb .section}

|API|Description|
|:--|:----------|
|[CancelTask](intl.en-US/API Reference/Others/CancelTask.md#)|Cancels an ongoing task.|
|[DescribeTasks](intl.en-US/API Reference/Others/DescribeTasks.md#)|Describes the progress of a specified asynchronous request.|
|[DescribeTaskAttribute](intl.en-US/API Reference/Others/DescribeTaskAttribute.md#)|Describes the details of a specified asynchronous task. Currently, the asynchronous tasks that can be queried include importing images \([ImportImage](intl.en-US/API Reference/Images/ImportImage.md#)\) and exporting images \([ExportImage](intl.en-US/API Reference/Images/ExportImage.md#)\).|
|[DescribeAccountAttributes](intl.en-US/API Reference/Others/DescribeAccountAttributes.md#)|Describes the maximum number of ECS resources that you can create in a region. Specifically, you can use this interface to query the quota for security groups, ENIs, Pay-As-You-Go instance vCPU cores, preemptible instance vCPU cores, and Dedicated Hosts \(DDHs\), local network type, and whether your account has been authenticated with real name credentials.|

