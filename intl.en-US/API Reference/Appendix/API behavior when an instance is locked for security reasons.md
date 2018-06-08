# API behavior when an instance is locked for security reasons {#EcsApi .reference}

Note that, disk-related activities in the In\_use status reference the instance OperationLocks. Otherwise, the instance OperationLocks may be ignored.

When a security lock is indicated, the `OperationLocks` in the outgoing parameters returned by the `DescribeInstanceAttribute` will include `LockReason:security`.

|Interface|Behavior|
|:--------|:-------|
|AllocatePublicIpAddress|Error|
|AttachDisk|Error|
|AuthorizeSecurityGroup|Normal logic|
|CreateDisk|Normal logic|
|CreateImage|Normal logic|
|CreateInstance|-|
|CreateSecurityGroup|Normal logic|
|CreateSnapshot|Error \(Only for disks attached on this instance in the In\_use status\)|
|DeleteDisk|Normal logic|
|DeleteImage|Normal logic|
|DeleteInstance|Normal logic|
|DeleteSecurityGroup|Normal logic|
|DeleteSnapshot|Normal logic|
|DescribeAutoSnapshotPolicy|Normal logic|
|DescribeDisks|Normal logic|
|DescribeImages|Normal logic|
|DescribeInstanceAttribute|Normal logic|
|DescribeInstanceStatus|Normal logic|
|DescribeInstanceTypes|Normal logic|
|DescribeInstanceMonitorData|Normal logic|
|DescribeRegions|Normal logic|
|DescribeSecurityGroupAttribute|Normal logic|
|DescribeSecurityGroups|Normal logic|
|DescribeSnapshotAttribute|Normal logic|
|DescribeSnapshots|Normal logic|
|DescribeZones|Normal logic|
|DetachDisk|Error|
|JoinSecurityGroup|Error|
|LeaveSecurityGroup|Error|
|ModifyAutoSnapshotPolicy|Normal logic|
|ModifyDiskAttribute|Normal logic|
|ModifyInstanceAttribute|Error|
|RebootInstance|Error|
|ReInitDisk|Error \(In\_use\), Normal Logic \(another status\)|
|ReplaceSystemDisk|Normal logic|
|ResetDisk|Error|
|RevokeSecurityGroup|Normal logic|
|StartInstance|Error|
|StopInstance|Error|

