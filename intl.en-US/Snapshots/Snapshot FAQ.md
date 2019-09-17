# Snapshot FAQ {#concept_j5z_vrr_lgb .concept}

This topic lists frequently asked questions related to ECS snapshots.

-   OSS-related questions
    -   [If I have activated OSS, will snapshots automatically be saved to my OSS buckets?](reseller.en-US/Snapshots/Snapshot FAQ.md#section_wnf_qh1_4gb)
    -   [Can a custom image that was created from a snapshot be saved to an OSS bucket?](#section_agb_789_ug8)
-   Billing-related questions
    -   [Where can I view a list of snapshot prices by Alibaba Cloud region?](#section_nom_iuk_an9)
    -   [What impact will overdue payments have on my stored snapshots?](#section_qs5_lyg_4gb)
    -   [I use snapshots frequently. How can I reduce the amount of fees incurred?](#section_75v_zgn_06k)
-   Snapshot and Block Storage type-related questions
    -   [Do automatic snapshots differ from or conflict with manual snapshots?](#section_vj5_5ws_ngb)
    -   [Can I create snapshots for local disks?](#section_8bp_ymj_xsh)
    -   [I have created a snapshot for an encrypted data disk and generated an image, but I cannot share the image. Why?](#section_m0o_tpa_pb2)
-   Snapshot capacity-related questions
    -   [Will deleting files in an ECS instance free up storage space?](#section_akt_4yg_4gb)
    -   [Why is the snapshot size larger than the disk size displayed in the file system?](#section_rr2_pyg_4gb)
    -   [What is the relationship between a file system and a disk or a snapshot?](#section_tsa_qqu_wdx)
-   Snapshot deletion-related questions
    -   [How can I prevent snapshots from being deleted by Alibaba Cloud?](#section_wj5_5ws_ngb)
    -   [How can I delete snapshots to reduce backup cost?](#section_pjl_hqz_ngb)
    -   [Will automatic snapshots be deleted after the system disk is changed, the instance expires, or the disk is released?](#section_ck5_5ws_ngb)
    -   [How can I delete snapshots that have been used to create images and disks?](#section_hji_juh_uhk)
-   Automatic snapshot policy-related questions
    -   [If I have used an automatic snapshot to create a custom image or a disk, will the automatic snapshot policy fail to be executed?](#section_xj5_5ws_ngb)
    -   [Can I create multiple snapshot policies for a disk?](#section_dx2_bzg_4gb)
-   Disk rollback with snapshot-related questions
    -   [How can I avoid losing data due to incorrect operations?](#section_oou_9ap_jvp)
    -   [After I change the system disk, can a snapshot of the previous system disk be used to roll back the new system disk?](#section_hpz_qkh_mgb)

## If I have activated OSS, will snapshots automatically be saved to my OSS buckets? {#section_wnf_qh1_4gb .section}

No. Snapshots are not saved to existing OSS buckets. Snapshots are stored independently of your OSS buckets. You do not need to create new buckets for snapshots.

## Can a custom image that was created from a snapshot be saved to an OSS bucket? {#section_agb_789_ug8 .section}

Yes. You can export the image to your OSS bucket to download in the future. For more information, see [Export custom images](../../../../reseller.en-US/Images/Custom image/Export custom images.md#). However, custom images cannot be directly stored to an OSS bucket.

## Where can I view a list of snapshot prices by Alibaba Cloud region? {#section_nom_iuk_an9 .section}

The price per GiB used to store snapshots is the same as that of OSS standard storage and is charged on a monthly basis. For information about snapshot prices by Alibaba Cloud region, go to the Pricing tab of the Elastic Compute Service page.

## What impact will overdue payments have on my stored snapshots? {#section_qs5_lyg_4gb .section}

Snapshots will be suspended 24 hours after your account has overdue payments. After your account has overdue payments:

-   In the first 15 days, all existing snapshots will be retained, but no new snapshots can be created. Snapshots whose retention period expires during this period will be deleted.
-   After 15 days, all snapshots will be deleted except for those that have been used to create disks or custom images.

You can recharge your account to resume the snapshot service. For more information, see [Recharging](https://help.aliyun.com/knowledge_list/37106.htm).

## I use snapshots frequently. How can I reduce the amount of fees incurred? {#section_75v_zgn_06k .section}

We recommend that you maintain a manageable number of snapshots, and delete unneeded snapshots. For more information, see [Reduce snapshot fees](reseller.en-US/Snapshots/Use snapshots/Reduce snapshot fees.md#).

## Do automatic snapshots differ from or conflict with manual snapshots? {#section_vj5_5ws_ngb .section}

No. Both manual snapshots and automatic snapshots are data files of a disk or Shared Block Storage device for a point in time. However, you cannot create manual snapshots while automatic snapshots are being created. You must wait until the automatic snapshots are finished being created.

## Can I create snapshots for local disks? {#section_8bp_ymj_xsh .section}

No. If you want to improve the availability of applications, we recommend that you create data redundancy at the application layer or create deployment sets for clusters.

## I have created a snapshot for an encrypted data disk and generated an image, but I cannot share the image. Why? {#section_m0o_tpa_pb2 .section}

To ensure data privacy, custom images created from encrypted snapshots cannot be shared. We recommend that you use unencrypted snapshots to create custom images and share with other users.

## Will deleting files in an ECS instance free up storage space? {#section_akt_4yg_4gb .section}

No. When you delete files in an ECS instance, only tags are added to the file headers but space is not cleared in the cloud disks.

## Why is the snapshot size larger than the disk size displayed in the file system? {#section_rr2_pyg_4gb .section}

-   Issue: You have created a snapshot after deleting files in the ECS instance. However, the size of the snapshot has not been reduced or larger than that of the disk size displayed in the file system.
-   Cause: When snapshots are created, a mechanism identifies empty blocks to reduce the size of the snapshot. However, empty blocks will be occupied when you format the file system, delete files, and write data to blocks. Because of this, the snapshot size may be larger than the disk size currently displayed in the file system. Specific causes:
    -   File system metadata is occupying disk space.
    -   The file system has written data to a large number of blocks divided equally from the logical block address during initialization. This operation also will occupy disk space.
    -   To improve performance, the file system only adds tags to the headers of files when they are deleted. Because the disk cannot detect delete instructions, these data blocks marked for deletion will still be allocated and copied to the snapshots.
    -   The KVM virtio block and Xen block front drivers do not support the TRIM instruction, used to prompt that data in the logical block address is no longer in use and can be deleted.

## What is the relationship between a file system and a disk or a snapshot? {#section_tsa_qqu_wdx .section}

You can create a file system in a disk partition. The file system manages disk space. These management tasks take the form of I/O requests in the disk. The disk records the states of data blocks and copies data to OSS as needed. This process is how snapshots are created. The following figure shows the relationship between a file system and a snapshot.

![Relationship between a file system and a disk or a snapshot](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10122/156871306939434_en-US.png)

**Note:** In the preceding figure, any data blocks with data written to them will be recorded in the snapshot, even if the related files have been deleted from the disk. In the file system, only tags are added to the headers of files to be deleted but space is not cleared in the disks.

## How can I prevent snapshots from being deleted by Alibaba Cloud? {#section_wj5_5ws_ngb .section}

-   Manual snapshots will never be deleted by Alibaba Cloud regardless of whether their corresponding disk or instance has been released.
-   To prevent automatic snapshots from being deleted, you can set the **Keep Snapshots** parameter to **Always Keep** when modifying the automatic snapshot policy. Then, only the earliest snapshots will be deleted when the quota of the snapshots is reached. For more information, see [Modify an automatic snapshot policy](reseller.en-US/Snapshots/Automatic snapshot policies/Modify an automatic snapshot policy.md#). For more information about the snapshot quota, see [Limits](../../../../reseller.en-US/Product Introduction/Limits.md#).

## How can I delete snapshots to reduce backup cost? {#section_pjl_hqz_ngb .section}

-   Manual snapshots: You can delete manual snapshots.
-   Automatic snapshots: You can delete automatic snapshots. When the maximum number of snapshots has been reached, the system will delete the earliest automatic snapshot.

## Will automatic snapshots be deleted after the system disk is changed, the instance expires, or the disk is released? {#section_ck5_5ws_ngb .section}

-   If **Delete Automatic Snapshots While Releasing Disk** is selected for the automatic snapshot policy, the automatic snapshots will be deleted when the corresponding instance or disk is released.
-   If **Delete Automatic Snapshots While Releasing Disk** is not selected for the automatic snapshot policy, the retention period specified by the automatic snapshot policy applies. You can [Modify an automatic snapshot policy](reseller.en-US/Snapshots/Automatic snapshot policies/Modify an automatic snapshot policy.md#) as needed.

## How can I delete snapshots that have been used to create images and disks? {#section_hji_juh_uhk .section}

-   You can delete snapshots that have been used to create disks. After a snapshot is deleted, you cannot perform operations that depend on the status of the original snapshot data, such as the operation to [reinitialize a disk](../../../../reseller.en-US/Block Storage/Block storage/Reinitialize a cloud disk/Reinitialize a cloud disk.md#).
-   If the snapshot has been used to create custom images, you must delete those custom images before the snapshot can be deleted.
-   You can delete images that have been used to create instances. After a snapshot is deleted, you cannot perform operations that depend on the status of the original snapshot data, such as the operation to [reinitialize a disk](../../../../reseller.en-US/Block Storage/Block storage/Reinitialize a cloud disk/Reinitialize a cloud disk.md#).

## If I have used an automatic snapshot to create a custom image or a disk, will the automatic snapshot policy fail to be executed? {#section_xj5_5ws_ngb .section}

No.

## Can I create multiple snapshot policies for a disk? {#section_dx2_bzg_4gb .section}

No.

## How can I avoid losing data due to incorrect operations? {#section_oou_9ap_jvp .section}

You can create snapshots to back up data in advance before you perform operations that carry risks to your data. For example, you can create a snapshot if you need to modify critical system files, migrate instances from a classic network to a VPC, back up data, restore an instance that was released accidentally, prevent network attacks, change operating systems, or provide data support for a production environment. If an error occurs, you can roll back the disk in time to reduce risks. For more information, see [Create a snapshot](reseller.en-US/Snapshots/Use snapshots/Create a snapshot.md#) and [Roll back a disk by using a snapshot](reseller.en-US/Snapshots/Use snapshots/Roll back a disk by using a snapshot.md#).

## After I change the system disk, can a snapshot of the previous system disk be used to roll back the new system disk? {#section_hpz_qkh_mgb .section}

No.

