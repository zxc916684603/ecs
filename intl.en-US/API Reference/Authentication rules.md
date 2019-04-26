# Authentication rules {#EcsApiAuthorizationRules .reference}

This topic describes how to use Aliyun Resource Name \(ARN\) values as a method of access control to authorize different user operations in ECS.

## Background information {#section_0ph_k63_iqp .section}

**Note:** If you can access resources without the need for authorization, you can skip this topic.

By default, you can use your Alibaba Cloud account or RAM user account to operate on ECS resources by calling ECS API actions. Operation permissions are required when:

-   You create a RAM user account that have no permission to operate on ECS resources under your Alibaba Cloud account.
-   You want to access ECS resources from other Alibaba Cloud services, or access other Alibaba Cloud services from ECS.
-   You want to operate on ECS resources that require prior permissions to be granted by the resource owner.

When an account requests access to resources under your Alibaba Cloud account by calling ECS APIs, Alibaba Cloud ECS checks the permissions granted by using RAM to ensure that the required permissions have been granted to the requester. Depending on the requested resources and API syntax, ECS determines which resources require a permission check for ECS APIs. For more information about authorization policies and permission control, see [What is RAM?](../../../../reseller.en-US/Product Introduction/What is RAM?.md#) and [API overview](../../../../reseller.en-US/API Reference/API overview.md#).

## Use ARN values {#section_0co_wyh_qff .section}

The following procedure describes how to create a custom policy to use Aliyun Resource Name \(ARN\) values in the RAM console. Note that you can also call the [CreatePolicy](../../../../reseller.en-US/API Reference/Policy management APIs/CreatePolicy.md#) API action to use ARN values.

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  In the left-side navigation pane, choose **Permissions** \> **Policies**.
3.  Click **Create Policy**.
4.  Set the **Policy Name** and **Note**.
5.  Select **Script**.

    **Note:** You can also select **Visualized**, in which case you can skip the [Authentication list](#section_d07_a67_vfx) to configure the policy.

6.  Set the **Policy Document** according to the JSON template file, and set the Resource parameter to one of the ARN values in the [Authentication list](#section_d07_a67_vfx). For the setting of other parameters, see [Policy elements](../../../../reseller.en-US/User Guide/Permission management/Policy language/Policy elements.md#).

    ```
    {
        "Statement": [
            {
                "Effect": "Allow",
                "Action": "",
                "Resource": ""
            }
        ],
        "Version": "1"
    }
    ```

7.  Click **OK**.

## Authentication list {#section_d07_a67_vfx .section}

The following table describes commonly used ARN values that correspond to API actions used in Alibaba Cloud ECS. For information about the ARN format, see [Terms](../../../../reseller.en-US/Product Introduction/Terms.md#).

|Action|ARN value|
|:-----|:--------|
|AddTags|acs:ecs:$regionid:$accountid:$resourceType/$resourceId|
|AllocatePublicIpAddress|acs:ecs:$regionid:$accountid:instance/$instanceId|
|ApplyAutoSnapshotPolicy|acs:ecs:\*:$accountid:snapshot/\*|
|AttachClassicLinkVpc|acs:ecs:$regionid:$accountid:instance/$instanceId|
|AttachDisk| -   acs:ecs:$regionid:$accountid:instance/$instanceId
-   acs:ecs:$regionid:$accountid:instance/$diskId

 |
|AttachKeyPair| -   acs:ecs:$regionid:$accountid:instance/$instanceId
-   acs:ecs:$regionid:$accountid:keypair/$keypairName

 |
|AuthorizeSecurityGroup|acs:ecs:$regionid:$accountid:securitygroup/$groupNo|
|AuthorizeSecurityGroupEgress|acs:ecs:$regionid:$accountid:securitygroup/$groupNo|
|CancelAutoSnapshotPolicy|acs:ecs:\*:$accountid:snapshot/\*|
|CancelCopyImage|acs:ecs:$regionid:$accountid:image/$imageNo|
|CopyImage| -   acs:ecs:$fromRegionid:$accountid:image/$imageNo
-   acs:ecs:$toRegionid:$accountid:image/\*

 |
|ConvertNatPublicIpToEip|acs:ecs:$regionid:$accountid:instance/$instanceId|
|CreateAutoSnapshotPolicy|acs:ecs:\*:$accountid:snapshot/\*|
|CreateDisk| -   acs:ecs:$regionid:$accountid:disk/\*
-   acs:ecs:$regionid:$accountid:snapshot/$snapshotId

 |
|CreateImage| -   acs:ecs:$regionid:$accountid:image/\*
-   acs:ecs:$regionid:$accountid:snapshot/$snapshotId
-   acs:ecs:$regionid:$accountid:instance/$instanceId

 |
|CreateInstance| -   acs:ecs:$regionid:$accountid:instance/\*
-   acs:ecs:$regionid:$accountid:image/$imageNo
-   acs:ecs:$regionid:$accountid:securitygroup/$groupNo
-   acs:ecs:$regionid:$accountid:snapshot/$snapshotId
-   \(Optional\) acs:ecs:$regionid:$accountid:keypair/$keyPairName
-   acs:vpc:$regionid:$accountid:vswitch/$vswitchId
-   acs:vpc:$regionid:$accountid:vpc/$vpcId

 |
|CreateKeyPair|acs:ecs:$regionid:$accountid:keypair/\*|
|CreateSecurityGroup|acs:ecs:$regionid:$accountid:securitygroup/\*|
|CreateSnapshot| -   acs:ecs:$regionid:$accountid:snapshot/\*
-   acs:ecs:$regionid:$accountid:disk/$diskId
-   acs:ecs:$regionid:$accountid:volume/$volumeId

 |
|DeleteAutoSnapshotPolicy|acs:ecs:\*:$accountid:snapshot/\*|
|DeleteDisk|acs:ecs:$regionid:$accountid:disk/$diskId|
|DeleteImage|acs:ecs:$regionid:$accountid:image/$imageNo|
|DeleteInstance|acs:ecs:$regionid:$accountid:instance/$instanceId|
|DeleteKeyPairs|acs:ecs:$regionid:$accountid:keypair/$keyPairName|
|DeleteSecurityGroup|acs:ecs:$regionid:$accountid:securitygroup/$groupNo|
|DeleteSnapshot|acs:ecs:$regionid:$accountid:snapshot/$snapshotId|
|DescribeClassicLinkInstances|acs:ecs:$regionid:$accountid:instance/\*|
|DescribeDiskMonitorData|acs:ecs:$regionid:$accountid:disk/$diskId|
|DescribeDisks| -   acs:ecs:$regionid:$accountid:disk/$diskId
-   acs:ecs:$regionid:$accountid:disk/\*

 |
|DescribeImages| -   acs:ecs:$regionid:$accountid:image/$imageNo
-   acs:ecs:$regionid:$accountid:image/\*

 |
|DescribeInstanceMonitorData|acs:ecs:$regionid:$accountid:instance/$instanceId|
|DescribeInstances| -   acs:ecs:$regionid:$accountid:instance/$instanceId
-   acs:ecs:$regionid:$accountid:instance/\*

 |
|DescribeInstanceStatus|acs:ecs:$regionid:$accountid:instance/\*|
|DescribeInstanceVncPasswd|acs:ecs:$regionid:$accountid:instance/$instanceId|
|DescribeInstanceVncUrl|acs:ecs:$regionid:$accountid:instance/$instanceId|
|DescribeKeyPairs| -   acs:ecs:$regionid:$accountid:keypair/$keyPairName
-   acs:ecs:$regionid:$accountid:keypair/\*

 |
|DescribePrice|acs:ecs:\*:$accountid:\*|
|DescribeRenewalPrice|acs:ecs:$regionid:$accountid:instance/$instanceId|
|DescribeSecurityGroupAttribute|acs:ecs:$regionid:$accountid:securitygroup/$groupNo|
|DescribeSecurityGroups| -   acs:ecs:$regionid:$accountid:securitygroup/$groupNo
-   acs:ecs:$regionid:$accountid:securitygroup/\*

 |
|DescribeSnapshotAttribute|acs:ecs:$regionid:$accountid:snapshot/$snapshotId|
|DescribeSnapshotLinks| -   acs:ecs:$regionid:$accountid:disk/$diskId
-   acs:ecs:$regionid:$accountid:disk/\*

 |
|DescribeSnapshotMonitorData|acs:ecs:\*:$accountid:snapshot/\*|
|DescribeSnapshots| -   acs:ecs:$regionid:$accountid:snapshot/$snapshotId
-   acs:ecs:$regionid:$accountid:snapshot/\*

 |
|DescribeTags|acs:ecs:$regionid:$accountid:$resourceType/$resourceId|
|DetachClassicLinkVpc|acs:ecs:$regionid:$accountid:instance/$instanceId|
|DetachDisk| -   acs:ecs:$regionid:$accountid:instance/$instanceId
-   acs:ecs:$regionid:$accountid:instance/$diskId

 |
|DetachKeyPair| -   acs:ecs:$regionid:$accountid:instance/$instanceId
-   acs:ecs:$regionid:$accountid:keypair/$keypairName

 |
|ExportImage|acs:ecs:$regionid:$accountid:image/$imageNo|
|ImportImage|acs:ecs:$regionid:$accountid:image/\*|
|ImportKeyPair|acs:ecs:$regionid:$accountid:keypair/\*|
|JoinSecurityGroup| -   acs:ecs:$regionid:$accountid:instance/$instanceId
-   acs:ecs:$regionid:$accountid:securitygroup/$groupNo

 |
|LeaveSecurityGroup| -   acs:ecs:$regionid:$accountid:instance/$instanceId
-   acs:ecs:$regionid:$accountid:securitygroup/$groupNo

 |
|ModifyAutoSnapshotPolicy|acs:ecs:\*:$accountid:snapshot/\*|
|ModifyDiskAttribute|acs:ecs:$regionid:$accountid:disk/$diskId|
|ModifyImageAttribute|acs:ecs:$regionid:$accountid:image/$imageNo|
|ModifyInstanceAttribute|acs:ecs:$regionid:$accountid:instance/$instanceId|
|ModifyInstanceAutoReleaseTime|acs:ecs:$regionid:$accountid:instance/$instanceId|
|ModifyInstanceChargeType|acs:ecs:$regionid:$accountid:instance/$instanceId|
|ModifyInstanceNetworkSpec|acs:ecs:$regionid:$accountid:instance/$instanceId|
|ModifyInstanceVncPasswd|acs:ecs:$regionid:$accountid:instance/$instanceId|
|ModifyInstanceVpcAttribute| -   acs:ecs:$regionid:$accountid:instance/$instanceId
-   acs:ecs:$regionid:$accountid:vswitch/$vSwitchId

 |
|ModifySecurityGroupAttribute|acs:ecs:$regionid:$accountid:securitygroup/$groupNo|
|ModifySecurityGroupEgressRule|acs:ecs:$regionid:$accountid:securitygroup/$groupNo|
|ModifySecurityGroupRule|acs:ecs:$regionid:$accountid:securitygroup/$groupNo|
|ModifyPrepayInstanceSpec|acs:ecs:$regionid:$accountid:|
|ModifySnapshotAttribute|acs:ecs:$regionid:$accountid:snapshot/$snapshotId|
|RebootInstance|acs:ecs:$regionid:$accountid:instance/$instanceId|
|ReInitDisk|acs:ecs:$regionid:$accountid:disk/$diskId|
|ReleasePublicIpAddress|acs:ecs:$regionid:$accountid:instance/$instanceId|
|RemoveTags|acs:ecs:$regionid:$accountid:$resourceType/$resourceId|
|RenewInstance|acs:ecs:$regionid:$accountid:instance/$instanceId|
|ReplaceSystemDisk| -   acs:ecs:$regionid:$accountid:instance/$instanceId
-   acs:ecs:$regionid:$accountid:image/$imageNo

 |
|ResetDisk|acs:ecs:$regionid:$accountid:disk/$diskId|
|ResizeDisk|acs:ecs:$regionid:$accountid:disk/$diskId|
|RevokeSecurityGroup|acs:ecs:$regionid:$accountid:securitygroup/$groupNo|
|RevokeSecurityGroupEgress|acs:ecs:$regionid:$accountid:securitygroup/$groupNo|
|RunInstances| -   acs:ecs:$regionid:$accountid:instance/\*
-   acs:ecs:$regionid:$accountid:image/$imageNo
-   acs:ecs:$regionid:$accountid:securitygroup/$groupNo
-   acs:ecs:$regionid:$accountid:snapshot/$snapshotId
-   acs:ecs:$regionid:$accountid:keypair/$keyPairName

 |
|StartInstance|acs:ecs:$regionid:$accountid:instance/$instanceId|
|StopInstance|acs:ecs:$regionid:$accountid:instance/$instanceId|

