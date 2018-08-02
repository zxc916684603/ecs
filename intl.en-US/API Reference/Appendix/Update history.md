# Update history {#EcsApiChangeLog .reference}

**API version: May 26, 2014**

Last update: April 25, 2017

|Release date|Update|Description|
|:-----------|:-----|:----------|
|April 25, 2017|Added SSH key pair APIs.| -   Added the CreateKeyPair API to create an SSH key pair.
-   Added the DeleteKeyPairs API to delete SSH key pairs.
-   Added the DescribeKeyPairs API to query SSH key pairs.
-   Added the ImportKeyPair API to import an SSH key pair.
-   Added the AttachKeyPair API to bind an SSH key pair to an ECS instance.
-   Added the DetachKeyPair API to unbind an SSH key pair from an ECS instance.

 |
|April 1, 2016|Added the snapshot APIs.| -   Added the CreateAutoSnapshotPolicy API to create an automatic snapshot policy.
-   Added the DeleteAutoSnapshotPolicy API to release an automatic snapshot policy.
-   Added the ModifyAutoSnapshotPolicyEx API to modify an automatic snapshot policy.
-   Added the DescribeAutoSnapshotPolicyEx API to query an automatic snapshot policy.
-   Added the ApplyAutoSnapshotPolicy API to execute an automatic snapshot policy.
-   Added the CancelAutoSnapshotPolicy API to cancel an automatic snapshot policy.

 |
|December 22, 2015|Added the image import and task management APIs.| -   Added the ImportImage API to import custom images of users.
-   Added the DescribeTasks API to query a task list.
-   Added the DescribeTaskAttribute API to query details of a task.
-   Added the CancelTask API to cancel a task.

 |
|December 9, 2015|Modified the tag APIs.| -   Deprecated the DescribeResourceByTags API.
-   Set ResourceId to mandatory in the RemoveTags API.
-   Set DescribeInstances to support filtering based on the instance type families.

 |
|November 19, 2015|Launched the new instance series.| -   Added the DescribeInstanceTypeFamilies API to query information about the instance type families.
-   Set DescribeInstances to support filtering based on the instance type families.
-   Added AvailableInstanceTypes to ZoneType, which indicates all instance types that can be created in the zone.
-   Added the instance types of series II to the returned results.

 |
|October 10, 2015|Launched HaVip.|Supported HaVip-related APIs.|
|September 4, 2015|Launched the ultra cloud disk.|Supported creation of the ultra cloud disk by setting cloud\_efficiency.|
|August 20, 2015|Launched the Tag function.| You can group resources by tags.|
|August 4, 2015|Launched the VPC function.|Supported creation of VPC instances.-   Added the VPC-related APIs.
-   Added the VRouter-related APIs.
-   Added the VSwitch-related APIs.
-   Added the EIP-related APIs.
-   Added the RouteTable-related APIs.

|
|May 15, 2015| Launched the shared image.|Added the shared image API.|
|May 14, 2015|Modified RAM authorization mode from four-step authorization to five-step authorization.| -   Added the requirement that accountid should be specified for the RAM authorization mode.
-   The original four-step authorization mode is still compatible, but the new five-step authorization is recommended.

 |
|April 21, 2015|Added the disk resizing function.| -   Added the ResizeDisk API.
-   Modified error codes for some APIs.

 |
|March 1, 2015| Added the Chinese description of error codes.| -   Added the Chinese description of error codes related to APIs.
-   Added the missing parameters for security group APIs.
-   Added the security group API ModifySecurityGroupAttribute.

 |
|February 6, 2015|Converted into online files, and added VPC APIs, bug fix information, and small adjustments.| -   Added VPC APIs.
-   Added new instance types.
-   Added the input parameter of EnableAutoSnapshot for the ModifyDiskAttribute API, and added the output parameter of EnableAutoSnapshot for the DescribeDisks API.
-   Corrected the measurement units of InternetTX, InternetRX, IntranetTX, and IntranetRX for DescribeInstanceMonitorData.

 |
|July 23, 2014|Added support for zones, independent basic cloud disks, and automatic snapshots.| -   Added the input parameter of ZoneId \(zone\) for some APIs.
-   Modified output parameters of some query APIs.
-   Added error codes and detailed error code scenarios of each API.
-   Updated a large number of sample codes.
-   Added one topic to describe the API actions when an account is in arrears or is locked for security reasons.
-   Added the status chart and status table of independent basic cloud disks.

 |
|April 3, 2014| Made some modifications for global availability.| -   Added and deleted some APIs.
-   Added some error codes.
-   Described in detail the possible error codes of each API.
-   Modified the optional values of some parameters.
-   Improved API descriptions.
-   Used same RequestId for the same API.
-   Added the limitations on CreateImage/AddDisk when snapshots were created before and on July 15, 2013.
-   Added the limitation for CreateInstance: If the instance memory is 512M, Windows operating system is not supported.
-   If the instance memory is 4G or above, a 32-bit operating system is not supported.
-   Adjusted the DescribeInstanceMonitorData code example and added the InstanceId and Time parameters.

 |
|May 22, 2013| Supplemented descriptions of some instance, disk, and snapshot APIs.|Supplemented descriptions of some instance, disk, and snapshot APIs.|
|April 10, 2013|Added some functions, including resetting instances, displaying snapshot names, and querying specified instances.| -   Added the ResetInstance API.
-   Added the SnapshotName attribute for snapshots.
-   Added InstanceId for GetMonitorData to query monitoring information of the specified instance.
-   Supplemented API descriptions.

 |
|January 24, 2013|Completed the first release of version on May 26, 2014.|Provided operation APIs related to instances, disks, images, snapshots, security groups, public IP addresses, regions, and monitoring.|

