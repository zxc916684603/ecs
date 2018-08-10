# Quick reference {#concept_q3w_45w_wdb .concept}

When using ECS, you may encounter various of issues, such as connecting to the instance, resizing the disk, upgrading or downgrading the instance configurations, and using snapshots or images. This article provides you with a quick reference to popular features of ECS resources.

## Operation instructions and limits {#instructions .section}

To guarantee proper operation of your ECS instance, You must carefully read all the [ECS operation instructions](intl.en-US/User Guide/ECS operation instructions.md#) and [Limits](intl.en-US/User Guide/Limits.md#) before you use it.

## Create and manage ECS instances {#section_fpl_wyw_wdb .section}

**Basic operations**

To use an ECS instances, follow these steps:

1.   [Create an ECS instance](../../../../intl.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#).
2.  Connect to the ECS instance. Use different methods according to its operating system:
    1.  Use [the Management Terminal](intl.en-US/User Guide/Connect/Connect to an instance by using the Management Terminal.md#) regardless of the operating system. Generally, this method is used for troubleshooting and maintenance.
    2.  For Linux or Unix-like OS: [Connect to a Linux instance by using a password](intl.en-US/User Guide/Connect/Connect to a Linux instance by using a password.md#), or [Connect to a Linux instance by using an SSH key pair](intl.en-US/User Guide/Connect/Connect to a Linux instance by using an SSH key pair.md#).
    3.  For Windows OS: [Connect to a Windows instance](intl.en-US/User Guide/Connect/Connect to a Windows instance.md#)
3.  [Stop the ECS instance](intl.en-US/User Guide/Instances/Start or stop an instance.md#).
4.  [Release the instance](intl.en-US/User Guide/Instances/Release an instance.md#).

**Change configurations**

You can change the instance type, IP addresses, and network bandwidth of your instance if the configurations cannot meet your business needs.

-   Subscription instances: [Upgrade configurations of Subscription instances](intl.en-US/User Guide/Instances/Change configurations/Upgrade configurations of Subscription instances.md#) or [Renew for configuration downgrade](../../../../intl.en-US/Pricing/Renew instances/Renew for configuration downgrade.md#)
-   [Change configurations of Pay-As-You-Go instances](intl.en-US/User Guide/Instances/Change configurations/Change configurations of Pay-As-You-Go instances.md#)

-   [Change public IP address](intl.en-US/User Guide/Instances/Change IP addresses/Change public IP address.md#)

-   [Convert public IP address to EIP address](intl.en-US/User Guide/Instances/Change IP addresses/Convert public IP address to EIP address.md#)


If the current operating system does not meet your needs, you can [change the operating system](intl.en-US/User Guide/Instances/Change the operating system.md#).

**Billing**

You can [switch from Pay-As-You-Go to subscription](../../../../intl.en-US/Pricing/Switch from Pay-As-You-Go to subscription.md#).

You can use different ways to renew Subscription instances:

-   [Manual renewal](../../../../intl.en-US/Pricing/Renew instances/Manual renewal.md#)
-   [Auto-renewal](../../../../intl.en-US/Pricing/Renew instances/Auto-renewal.md#)

**Elaborate management of and control over ECS instances**

You can use the following features to elaborate management of and control over ECS instances:

-   [User data](intl.en-US/User Guide/Instances/User-defined data and metadata/User data.md#)

-   [Metadata](intl.en-US/User Guide/Instances/User-defined data and metadata/Metadata.md#), including [instance identity](intl.en-US/User Guide/Instances/Instance identity.md#)

-   [Instance RAM roles](intl.en-US/User Guide/Instances/Instance RAM roles/What is the RAM role of an instance.md#)


## Create and manage cloud disks {#section_h5j_dbx_wdb .section}

**Basic operations**

To use a cloud disk as a data disk, follow these steps:

1.  [Create a cloud disk](intl.en-US/User Guide/Cloud disks/Create a cloud disk.md#).
2.  [Attach a cloud disk](intl.en-US/User Guide/Cloud disks/Attach a cloud disk.md#).
3.  [\(Linux\) Format and mount a data disk](../../../../intl.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Linux _ Format and mount a data disk.md#) or [\(Windows\) Format a data disk](../../../../intl.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Windows _ Format a data disk.md#).
4.  [Create snapshots](intl.en-US/User Guide/Snapshots/Create snapshots.md#) to back up data.
5.  [Detach a cloud disk](intl.en-US/User Guide/Cloud disks/Detach a cloud disk.md#).
6.  [Release a cloud disk](intl.en-US/User Guide/Cloud disks/Release a cloud disk.md#).

**Change configurations**

When the capacity of the system disks or data disks cannot meet your business needs, you can [increase system disk size](intl.en-US/User Guide/Cloud disks/Resize cloud disks/Increase system disk size.md#) or resize the data disks. For more information about resizing a data disk, see [Linux \_ Resize a data disk](intl.en-US/User Guide/Cloud disks/Resize cloud disks/Linux _ Resize a data disk.md)[Windows \_ Resize a data disk](intl.en-US/User Guide/Cloud disks/Resize cloud disks/Windows _ Resize a data disk.md#).

**Manage data on a cloud disk**

When errors occur to data on a cloud disk, you can use a snapshot to [roll back a cloud disk](intl.en-US/User Guide/Cloud disks/Roll back a cloud disk.md#) of the disk to restore data.

If you want to restore a cloud disk to its initial status after it is created, you can [reinitialize a cloud disk](intl.en-US/User Guide/Cloud disks/Reinitialize a cloud disk.md#).

If you want to copy data on an existing cloud disk to a new, empty cloud disk, you can [create a cloud disk from a snapshot](intl.en-US/User Guide/Cloud disks/Create a cloud disk from a snapshot.md#).

## Create and manage snapshots {#section_bc5_3cx_wdb .section}

**Basic operations**

To use a snapshot, follow these steps:

1.  Create a snapshot by using either of the following methods:
    -   [Create snapshots](intl.en-US/User Guide/Snapshots/Create snapshots.md#).
    -   [Create and delete an automatic snapshot policy](intl.en-US/User Guide/Snapshots/Create and delete an automatic snapshot policy.md#), and [apply automatic snapshot policies to disks](intl.en-US/User Guide/Snapshots/Apply automatic snapshot policies to disks.md#), to enable creating snapshots automatically.
2.  [View a snapshot chain](intl.en-US/User Guide/Snapshots/View a snapshot chain.md#).
3.  To save space occupied by snapshots, [delete unnecessary snapshots](intl.en-US/User Guide/Snapshots/Delete snapshots or automatic snapshot policies.md#).

**Using snapshots**

To copy or back up data: you can use a snapshot to [create a cloud disk from a snapshot](intl.en-US/User Guide/Cloud disks/Create a cloud disk from a snapshot.md#), or [roll back a cloud disk](intl.en-US/User Guide/Cloud disks/Roll back a cloud disk.md#).

To ease environment deployment, you can use a system disk snapshot to [create a custom image using a snapshot](intl.en-US/User Guide/Images/Create custom image/Create a custom image by using a snapshot.md#), and [create an instance from a custom Image](intl.en-US/User Guide/Instances/Create an instance/Create an instance from a custom Image.md#).

## Create and manage custom images {#section_mpg_qvw_wdb .section}

Only custom images can be operated in the ECS console. Using custom images can simplify environment deployment.

You can own a custom image by using the following methods:

-   [Create a custom image using a snapshot](intl.en-US/User Guide/Images/Create custom image/Create a custom image by using a snapshot.md#)
-   [Create a custom image by using an instance](intl.en-US/User Guide/Images/Create custom image/Create a custom image by using an instance.md#)
-   [Use Packer to create a custom image](intl.en-US/User Guide/Images/Open source tools/Use Packer to create a custom image.md#)
-   [Copy custom images](intl.en-US/User Guide/Images/Copy custom images.md#) across different regions.
-   [Share images](intl.en-US/User Guide/Images/Share images.md#) across different accounts.
-   [Import custom images](intl.en-US/User Guide/Images/Import images/Import custom images.md#)
-   [Create and import on-premise images by using Packer](intl.en-US/User Guide/Images/Open source tools/Create and import on-premise images by using Packer.md#)

You can [export custom images](intl.en-US/User Guide/Images/Export custom images.md#) to back up the environment and [delete custom images](intl.en-US/User Guide/Images/Delete custom images.md#).

## Create and manage security groups {#section_egt_qcx_wdb .section}

**Basic operations**

To use a security group, follow these steps:

1.  [Create a Security Group](intl.en-US/User Guide/Security groups/Creating a Security Group.md#).
2.  [Add security group rules](intl.en-US/User Guide/Security groups/Add security group rules.md#).
3.  [Add to or remove from a security group](intl.en-US/User Guide/Instances/Add to or remove from a security group.md#)
4.  [Delete a security group rule](intl.en-US/User Guide/Security groups/Delete a security group rule.md#).
5.  [Delete a security group](intl.en-US/User Guide/Security groups/Delete a security group.md#).

**Manage security groups and their rules**

To simplify business deployment, you can [clone a security group](intl.en-US/User Guide/Security groups/Clone a security group.md#) across regions or network types.

When new security group rules impair the online business application, you can  [restore security group rules](intl.en-US/User Guide/Security groups/Restore security group rules.md#) fully or partially.

## Create and manage SSH key pairs {#section_vpg_qvw_wdb .section}

To use an SSH key pair, follow these steps:

1.  [Create an SSH key pair](intl.en-US/User Guide/Key pairs/Create an SSH key pair.md#), or [import an SSH key pair](intl.en-US/User Guide/Key pairs/Import an SSH key pair.md#).
2.  [Bind a SSH key pair](intl.en-US/User Guide/Key pairs/Bind or unbind a SSH key pair.md#), or bind the SSH key pair after a Linux instance is created or when you [create an instance](../../../../intl.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md).
3.  [Connect to a Linux instance by using an SSH key pair](intl.en-US/User Guide/Connect/Connect to a Linux instance by using an SSH key pair.md#).
4.  [Unbind an SSH key pair](intl.en-US/User Guide/Key pairs/Bind or unbind a SSH key pair.md).
5.  [Delete a SSH key pair](intl.en-US/User Guide/Key pairs/Delete a SSH key pair.md#).

## Create and manage ENIs {#section_zpg_qvw_wdb .section}

To use an ENI, follow these steps:

1.  [Create an ENI](intl.en-US/User Guide/Elastic Network Interfaces/Create an ENI.md#).
2.  [Attach an ENI to an instance](intl.en-US/User Guide/Elastic Network Interfaces/Attach an ENI to an instance.md#), or  [attach an ENI when creating an instance](intl.en-US/User Guide/Elastic Network Interfaces/Attach an ENI when creating an instance.md#).
3.  Optional. [Configure an ENI](intl.en-US/User Guide/Elastic Network Interfaces/Configure an ENI.md#).
4.  [Detach an ENI from an instance](intl.en-US/User Guide/Elastic Network Interfaces/Detach an ENI from an instance.md#).
5.  [Delete an ENI](intl.en-US/User Guide/Elastic Network Interfaces/Delete an ENI.md#).

## Use tags {#section_dqg_qvw_wdb .section}

You can use tags to group resources to improve efficiency. To use tags, follow these steps:

1.  [Add a tag to resources](intl.en-US/User Guide/Tags/Add a tag to resources.md#).
2.  [Filter resources by tags](intl.en-US/User Guide/Tags/Filter resources by tags.md#).
3.  [Delete a tag](intl.en-US/User Guide/Tags/Delete a tag.md#).

