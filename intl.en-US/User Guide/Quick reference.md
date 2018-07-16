# Quick reference {#concept_q3w_45w_wdb .concept}

When using ECS, you may encounter various of issues, such conncting to the instance, resizing the disk, upgrade or downgrade the instance configurations, and use snapshots or images. This article provides you with a quick reference to popular features of ECS resources.

## Operation instructions and limits {#instructions .section}

To guarantee proper operation of your ECS instance, You must carefully read all the  [EN-US\_TP\_9615.md\#](intl.en-US/User Guide/ECS operation instructions.md#)

 and  [EN-US\_TP\_9616.md\#](intl.en-US/User Guide/Limits.md#) before you use it.

## Create and manage ECS instances {#section_fpl_wyw_wdb .section}

**Basic operations**

To use an ECS instances, follow these steps:

1.   [Create an ECS instance.](../../../../intl.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#).
2.  Connect to the ECS instance. Use different methods according to its operating system:
    1.  Use [EN-US\_TP\_9619.md\#](intl.en-US/User Guide/Connect/Connect to an instance by using the Management Terminal.md#) regardless of the operating system. Generally, this method is used for troubleshooting and maintenance.
    2.  For Linux or Unix-like OS: [EN-US\_TP\_9621.md\#](intl.en-US/User Guide/Connect/Connect to a Linux instance by using a password.md#) Or  [EN-US\_TP\_9620.md\#](intl.en-US/User Guide/Connect/Connect to a Linux instance by using an SSH key pair.md#).
    3.  For Windows OS: [EN-US\_TP\_9622.md\#](intl.en-US/User Guide/Connect/Connect to a Windows instance.md#)
3.  [Stop the ECS instance](intl.en-US/User Guide/Instances/Start or stop an instance.md#)
4.  [EN-US\_TP\_9651.md\#](intl.en-US/User Guide/Instances/Release an instance.md#).

**Change configurations**

You can change the instance type, IP addresses, and network bandwidth of your instance if the configurations cannot meet your business needs.

-   Subscription instances: [包年包月实例升级配置](intl.en-US/User Guide/Instances/Change configurations/Upgrade configurations of Subscription instances.md#) or [../../../../dita-oss-bucket/SP\_2/DNA0011810291/EN-US\_TP\_9593.md\#](../../../../intl.en-US/Pricing/Renew instances/Renew for configuration downgrade.md#)
-   [EN-US\_TP\_9644.md\#](intl.en-US/User Guide/Instances/Change configurations/Change configurations of Pay-As-You-Go instances.md#)

-   [EN-US\_TP\_9656.md\#](intl.en-US/User Guide/Instances/Change IP addresses/Change public IP address.md#)

-   [EN-US\_TP\_9657.md\#](intl.en-US/User Guide/Instances/Change IP addresses/Convert public IP address to EIP address.md#)


If the current operating system does not meet your needs, you can [EN-US\_TP\_9640.md\#](intl.en-US/User Guide/Instances/Change the operating system.md#).

**Billing**

You can [按量付费转包年包月](../../../../intl.en-US/Pricing/Switch from Pay-As-You-Go to subscription.md#).

You can use different ways to renew Subscription instances:

-   [../../../../dita-oss-bucket/SP\_2/DNA0011810291/EN-US\_TP\_9591.md\#](../../../../intl.en-US/Pricing/Renew instances/Manual renewal.md#)
-   [../../../../dita-oss-bucket/SP\_2/DNA0011810291/EN-US\_TP\_9592.md\#](../../../../intl.en-US/Pricing/Renew instances/Auto-renewal.md#)

**Elaborate management of and control over ECS instances**

You can use the following features to elaborate management of and control over ECS instances:

-   [EN-US\_TP\_9660.md\#](intl.en-US/User Guide/Instances/User-defined data and metadata/User data.md#)

-   [EN-US\_TP\_9661.md\#](intl.en-US/User Guide/Instances/User-defined data and metadata/Metadata.md#), including [EN-US\_TP\_9662.md\#](intl.en-US/User Guide/Instances/Instance identity.md#)

-   [Instance RAM roles](intl.en-US/User Guide/Instances/Instance RAM roles/What is the RAM role of an instance.md#)


## Create and manage cloud disks {#section_h5j_dbx_wdb .section}

**Basic operations**

To use a cloud disk as a data disk, follow these steps:

1.  [EN-US\_TP\_9669.md\#](intl.en-US/User Guide/Cloud disks/Create a cloud disk.md#).
2.  [EN-US\_TP\_9671.md\#](intl.en-US/User Guide/Cloud disks/Attach a cloud disk.md#).
3.  On [../../../../dita-oss-bucket/SP\_2/DNA0011854887/EN-US\_TP\_9604.md\#](../../../../intl.en-US/Quick Start for Entry-Level Users/Step 4: Format a data disk/Linux _ Format and mount a data disk.md#) or [../../../../dita-oss-bucket/SP\_2/DNA0011854887/EN-US\_TP\_9605.md\#](../../../../intl.en-US/Quick Start for Entry-Level Users/Step 4: Format a data disk/Windows _ Format a data disk.md#).
4.  [EN-US\_TP\_9687.md\#](intl.en-US/User Guide/Snapshots/Create snapshots.md#) back up data.
5.  [EN-US\_TP\_9673.md\#](intl.en-US/User Guide/Cloud disks/Detach a cloud disk.md#).
6.  [EN-US\_TP\_9685.md\#](intl.en-US/User Guide/Cloud disks/Release a cloud disk.md#).

**Change configurations**

When the capacity of the system disks or data disks cannot meet your business needs, you can [EN-US\_TP\_9676.md\#](intl.en-US/User Guide/Cloud disks/Resize cloud disks/Increase system disk size.md#) increase system disk size or resize the data disks. Increase system disk size. Operations vary depending on your operating system. [EN-US\_TP\_9678.md\#](intl.en-US/User Guide/Cloud disks/Resize cloud disks/Windows _ Resize a data disk.md#).

**Manage data on a cloud disk**

When errors occur to data on a cloud disk, you can use a snapshot  [EN-US\_TP\_9680.md\#](intl.en-US/User Guide/Cloud disks/Roll back a cloud disk.md#) of the disk to restore data.

If you want to restore a cloud disk to its initial status after it is created, you can [EN-US\_TP\_9679.md\#](intl.en-US/User Guide/Cloud disks/Reinitialize a cloud disk.md#).

If you want to copy data on an existing cloud disk to a new, empty cloud disk, you can [EN-US\_TP\_9670.md\#](intl.en-US/User Guide/Cloud disks/Create a cloud disk from a snapshot.md#).

## Create and manage snapshots {#section_bc5_3cx_wdb .section}

**Basic operations**

To use a snapshot, follow these steps:

1.  Create a snapshot by using either of the following methods:
    -   [EN-US\_TP\_9687.md\#](intl.en-US/User Guide/Snapshots/Create snapshots.md#).
    -   [EN-US\_TP\_9688.md\#](intl.en-US/User Guide/Snapshots/Create and delete an automatic snapshot policy.md#), and [EN-US\_TP\_9689.md\#](intl.en-US/User Guide/Snapshots/Apply automatic snapshot policies to disks.md#), to enable creating snapshots automatically.
2.  [EN-US\_TP\_9693.md\#](intl.en-US/User Guide/Snapshots/View a snapshot chain.md#).
3.  To save space occupied by snapshots, [delete unnecessary snapshots](intl.en-US/User Guide/Snapshots/Delete snapshots or automatic snapshot policies.md#).

**Using snapshots**

To copy or back up data: you ccan use a snapshot to [EN-US\_TP\_9670.md\#](intl.en-US/User Guide/Cloud disks/Create a cloud disk from a snapshot.md#), or  [EN-US\_TP\_9680.md\#](intl.en-US/User Guide/Cloud disks/Roll back a cloud disk.md#).

To ease environment deployment, you can use a system disk snapshot to [EN-US\_TP\_9696.md\#](intl.en-US/User Guide/Images/Create custom image/Create a custom mirror using a snapshot.md#), and [EN-US\_TP\_9627.md\#](intl.en-US/User Guide/Instances/Create an instance/Create an instance from a custom Image.md#).

## Create and manage custom images {#section_mpg_qvw_wdb .section}

Only custom images can be operated in the ECS console. Using custom images can simplify environment deployment.

You can own a custom image by using the following methods:

-   [EN-US\_TP\_9696.md\#](intl.en-US/User Guide/Images/Create custom image/Create a custom mirror using a snapshot.md#)
-   [EN-US\_TP\_9697.md\#](intl.en-US/User Guide/Images/Create custom image/Create a custom image by using an instance.md#)
-   [EN-US\_TP\_9698.md\#](intl.en-US/User Guide/Images/Create custom image/Use Packer to create a custom image.md#)
-   across different regions [EN-US\_TP\_9699.md\#](intl.en-US/User Guide/Images/Copy custom images.md#)
-   across different accounts [EN-US\_TP\_9700.md\#](intl.en-US/User Guide/Images/Share images.md#)
-   [EN-US\_TP\_9706.md\#](intl.en-US/User Guide/Images/Import images/Import custom images.md#)
-   [EN-US\_TP\_9708.md\#](intl.en-US/User Guide/Images/Import images/Create and import on-premise images by using Packer.md#)

You can [EN-US\_TP\_9712.md\#](intl.en-US/User Guide/Images/Export custom images.md#) to back up the environment and [EN-US\_TP\_9710.md\#](intl.en-US/User Guide/Images/Delete custom images.md#).

## Create and manage security groups {#section_egt_qcx_wdb .section}

**Basic operations**

To use a security group, follow these steps:

1.  [EN-US\_TP\_9717.md\#](intl.en-US/User Guide/Security groups/Creating a Security Group.md#).
2.  [EN-US\_TP\_9718.md\#](intl.en-US/User Guide/Security groups/Add security group rules.md#).
3.  [EN-US\_TP\_9652.md\#](intl.en-US/User Guide/Instances/Add to or remove from a security group.md#)
4.  [EN-US\_TP\_9722.md\#](intl.en-US/User Guide/Security groups/Delete a security group rule.md#).
5.  [EN-US\_TP\_9723.md\#](intl.en-US/User Guide/Security groups/Delete a security group.md#).

**Manage security groups and their rules**

To simplify business deployment, you can [EN-US\_TP\_9724.md\#](intl.en-US/User Guide/Security groups/Clone a security group.md#) across regions or network types.

When new security group rules impair the online business application, you can  [EN-US\_TP\_9726.md\#](intl.en-US/User Guide/Security groups/Restore security group rules.md#) fully or partially.

## Create and manage SSH key pairs {#section_vpg_qvw_wdb .section}

To use an SSH key pair, follow these steps:

1.  [EN-US\_TP\_9728.md\#](intl.en-US/User Guide/Key pairs/Create an SSH key pair.md#), or [EN-US\_TP\_9729.md\#](intl.en-US/User Guide/Key pairs/Import an SSH key pair.md#).
2.  [EN-US\_TP\_9730.md\#](intl.en-US/User Guide/Key pairs/Bind or unbind a SSH key pair.md#), or bind the SSH key pair after a Linux instance is created or when you create a Linux instance.
3.  [EN-US\_TP\_9620.md\#](intl.en-US/User Guide/Connect/Connect to a Linux instance by using an SSH key pair.md#).
4.  Unbind an SSH key pair.
5.  [EN-US\_TP\_9731.md\#](intl.en-US/User Guide/Key pairs/Delete a SSH key pair.md#).

## Create and manage ENIs {#section_zpg_qvw_wdb .section}

To use an ENI, follow these steps:

1.  [EN-US\_TP\_9734.md\#](intl.en-US/User Guide/Elastic Network Interfaces/Create an ENI.md#).
2.  [EN-US\_TP\_9735.md\#](intl.en-US/User Guide/Elastic Network Interfaces/Attach an ENI to an instance.md#), or  [EN-US\_TP\_9733.md\#](intl.en-US/User Guide/Elastic Network Interfaces/Attach an ENI when creating an instance.md#).
3.  Optional. [EN-US\_TP\_9739.md\#](intl.en-US/User Guide/Elastic Network Interfaces/Configure an ENI.md#).
4.  [EN-US\_TP\_9736.md\#](intl.en-US/User Guide/Elastic Network Interfaces/Detach an ENI from an instance.md#).
5.  [EN-US\_TP\_9738.md\#](intl.en-US/User Guide/Elastic Network Interfaces/Delete an ENI.md#).

## Use tags {#section_dqg_qvw_wdb .section}

You can use tags to group resources to improve efficiency.  To use tags, follow these steps:

1.  [EN-US\_TP\_9742.md\#](intl.en-US/User Guide/Tags/Add a tag to resources.md#).
2.  [EN-US\_TP\_9744.md\#](intl.en-US/User Guide/Tags/Filter resources by tags.md#).
3.  [EN-US\_TP\_9743.md\#](intl.en-US/User Guide/Tags/Add a tag to resources.md#).

