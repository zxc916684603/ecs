# Authentication rules {#EcsApiAuthorizationRules .reference}

When a RAM user requests access to ECS resources owned by an Alibaba Cloud user by using ECS APIs, ECS sends a request to RAM service to check access permission and make sure that the resource owner allows the caller to access the resources. Each ECS API requires different authentication rules for the requested resources according to the resources specification and the definition of the API. See the following table for specific authentication rules.

|Action|Authentication rule|
|:-----|:------------------|
|AddTags|acs:ecs:$regionid:$accountid:$resourceType/$resourceId|
|AllocatePublicIpAddress|acs:ecs:$regionid:$accountid:instance/$instanceId|
|ApplyAutoSnapshotPolicy| acs:ecs:\*:$accountid:snapshot/\*|
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
|CopyImage| -    acs:ecs:$fromRegionid:$accountid:image/$imageNo
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
|CreateSecurityGroup|acs:ecs:$regionid:$accountid:securitygroup/|
|CreateSnapshot| -   acs:ecs:$regionid:$accountid:snapshot/
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
|DescribeInstanceAttribute|acs:ecs:$regionid:$accountid:instance/$instanceId|
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
|ImportKeyPair|ACS: ECs: $ regionid: $ accounting: keypair /\*|
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
|Modifyinstancevncpasswd|acs:ecs:$regionid:$accountid:instance/$instanceId|
|ModifyInstanceVpcAttribute| -   acs:ecs:$regionid:$accountid:instance/$instanceId
-   acs:ecs:$regionid:$accountid:vswitch/$vSwitchId

 |
|ModifySecurityGroupAttribute|acs:ecs:$regionid:$accountid:securitygroup/$groupNo|
|ModifySecurityGroupEgressRule|ACS: ECs: $ regionid: $ accounting: securitygroup/$ groupno|
|ModifySecurityGroupRule|acs:ecs:$regionid:$accountid:securitygroup/$groupNo|
|ModifyPrepayInstanceSpec |acs:ecs:$regionid:$accountid:|
|ModifySnapshotAttribute|acs:ecs:$regionid:$accountid:snapshot/$snapshotId|
|Rebootinstance|acs:ecs:$regionid:$accountid:instance/$instanceId|
|ReInitDisk|acs:ecs:$regionid:$accountid:disk/$diskId|
|ReleasePublicIpAddress|acs:ecs:$regionid:$accountid:instance/$instanceId|
|RemoveTags|acs:ecs:$regionid:$accountid:$resourceType/$resourceId|
|ReplaceSystemDisk| -   acs:ecs:$regionid:$accountid:instance/$instanceId
-   acs:ecs:$regionid:$accountid:image/$imageNo

 |
|ResetDisk|acs:ecs:$regionid:$accountid:disk/$diskId|
|Resizedisk|acs:ecs:$regionid:$accountid:disk/$diskId|
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

