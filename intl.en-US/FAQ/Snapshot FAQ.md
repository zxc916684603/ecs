# Snapshot FAQ {#concept_j5z_vrr_lgb .concept}

-   FAQ about snapshot billing
    -   [How will snapshots get billed after they are commercialized?](#section_cbz_c95_m9r)
    -   [Are there any examples that can show me how the Pay-As-You-Go billing method works?](#section_yp5_7ly_7nl)
    -   [How do I view snapshot prices for different regions?](#section_y5u_joe_y4n)
    -   [Can I continue to use the snapshot service if the payment of my account is overdue?](intl.en-US/Snapshots/FAQ/Snapshot FAQ.md#section_qs5_lyg_4gb)
    -   [How do I reduce snapshot fees?](#section_6ql_762_snz)
-   FAQ about snapshot types
    -   [Does a manual snapshot differ from or conflict with an automatic snapshot?](intl.en-US/Snapshots/FAQ/Snapshot FAQ.md#section_vj5_5ws_ngb)
-   FAQ about snapshot size
    -   [Why is the snapshot size larger than the data volume displayed in the file system?](intl.en-US/Snapshots/FAQ/Snapshot FAQ.md#section_rr2_pyg_4gb)
    -   [Will the space occupied by the disk be reduced when I delete a file from an ECS instance?](intl.en-US/Snapshots/FAQ/Snapshot FAQ.md#section_akt_4yg_4gb)
-   FAQ about snapshot deletion
    -   [How do I maintain my snapshots to avoid being deleted by Alibaba Cloud?](intl.en-US/Snapshots/FAQ/Snapshot FAQ.md#section_wj5_5ws_ngb)
    -   [How do I delete unnecessary snapshots to reduce backup costs?](intl.en-US/Snapshots/FAQ/Snapshot FAQ.md#section_pjl_hqz_ngb)
    -   [Will an automatic snapshot be deleted after I replace the system disk, the instance expires, or the disk is released?](intl.en-US/Snapshots/FAQ/Snapshot FAQ.md#section_ck5_5ws_ngb)
    -   [How do I delete a snapshot that I have used to create images or disks?](intl.en-US/Snapshots/FAQ/Snapshot FAQ.md#section_hji_juh_uhk)
-   FAQ about automatic snapshot policies
    -   [Will the snapshot policy fail to be implemented if I use an automatic snapshot to create a custom image or disk?](intl.en-US/Snapshots/FAQ/Snapshot FAQ.md#section_xj5_5ws_ngb)
    -   [Can I set multiple automatic snapshot policies for a disk?](intl.en-US/Snapshots/FAQ/Snapshot FAQ.md#section_dx2_bzg_4gb)
-   FAQ about using a snapshot to roll back a disk
    -   [Can I use a snapshot of the old system disk to roll back the new system disk after I replace the system disk?](intl.en-US/Snapshots/FAQ/Snapshot FAQ.md#section_hpz_qkh_mgb)

## How will snapshots get billed after they are commercialized? {#section_cbz_c95_m9r .section}

The snapshot service will be billed as Pay-As-You-Go. The unit price of Pay-As-You-Go snapshots will be consistent with the unit price of OSS standard storage. The unit price is given in the following unit: USD/GiB/month. For a comprehensive price list of various Alibaba Cloud regions, see [Alibaba Cloud product pricing](https://www.aliyun.com/price/product#/disk/detail). For the snapshot commercialization schedule, see **Notice of Alibaba Cloud Snapshot Commercialization**.

## Are there any examples that can show me how the Pay-As-You-Go billing method works? {#section_yp5_7ly_7nl .section}

Yes, for more information, see [Billing of snapshots](../../../../intl.en-US/Pricing/Billing of snapshots.md#).

## How do I view snapshot prices for different regions? {#section_y5u_joe_y4n .section}

You can view snapshot prices by region in the **Snapshot Fee** area of the **Pricing** tab page at [ECS product details](https://www.alibabacloud.com/product/ecs). You can also click **Download price** to download a price list in the CSV or JSON format.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10124/156394029351569_en-US.png)

## Can I continue to use the snapshot service if the payment of my account is overdue? {#section_qs5_lyg_4gb .section}

No, if your account is overdue, the snapshot service will be suspended 24 hours since then.

Within the first 15 days, all your snapshots are retained but you cannot create snapshots. Automatic snapshots with a retention duration shorter than 15 days will be deleted after they expire.

Fifteen days after the overdue payment, only snapshots that were used to create disks or custom images are retained.

## How do I reduce snapshot fees? {#section_6ql_762_snz .section}

You can reduce snapshot fees by maintaining an appropriate number of snapshots and also deleting unnecessary snapshots immediately after use. For more information, see [Reduce snapshot fees](intl.en-US/Snapshots/Use snapshots/Reduce snapshot fees.md#).

## Does a manual snapshot differ from or conflict with an automatic snapshot? {#section_vj5_5ws_ngb .section}

No, both manual and automatic snapshots are copies of the data stored on a cloud disk or on Shared Block Storage at a specified point in time. In this regard, they are neither different from each other nor in conflict with each other.

## Why is the size of a snapshot of a disk larger than the disk usage space displayed in the file system? {#section_rr2_pyg_4gb .section}

The simple answer is that data is written is recorder into the snapshot regardless of whether the relevant files have been deleted from file system. For a more detailed answer, see [Why is the size of a snapshot of a disk larger than the disk space usage displayed in the file system?](intl.en-US/Snapshots/FAQ/Why is the size of a snapshot of a disk larger than the disk space usage displayed in the file system?.md#)

## Will the space occupied by the disk be reduced when I delete a file from an ECS instance? {#section_akt_4yg_4gb .section}

No, when you delete a file from an ECS instance, the file system only tags the file head. This does not reduce the space that the disk occupies.

## How can I avoid having my snapshots be automatically deleted by Alibaba Cloud? {#section_wj5_5ws_ngb .section}

This is a problem that is particular to automatic snapshots. To avoid your automatic snapshots from being deleted automatically, you can [modify the automatic snapshot policy](intl.en-US/Snapshots/Use snapshots/Apply automatic snapshot policies to disks.md#) to change the **Keep Snapshots** parameter to **Always Keep**. This way the system will not delete automatic snapshots even if the snapshot quota \(by default, 64 snapshots\) is reached. However, manual snapshots are different. They are not deleted regardless of whether you have released your disk or instance.

## What can I do to delete unnecessary snapshots to reduce backup costs? {#section_pjl_hqz_ngb .section}

The steps you need to take to delete unnecessary snapshots differ between manual and automatic snapshots. For manual snapshots, you can delete unnecessary ones directly. For automatic snapshots, in addition to deleting unnecessary snapshots directly, the system also automatically deletes snapshots, starting with the oldest one, when the snapshot quota \(which, by default, is 64 snapshots\) specified in the automatic snapshot policy is reached.

## Will an automatic snapshot be deleted after I replace the system disk, the instance expires, or the disk is released? {#section_ck5_5ws_ngb .section}

This depends on the settings that you selected when you set the automatic snapshot policy for your automatic snapshots.

-   If you selected **Delete Automatic Snapshots While Releasing Disk**, then automatic snapshots are deleted automatically by the system in the case that you replace the system disk, the corresponding instance expires, or the disk is released.
-   If you cleared **Delete Automatic Snapshots While Releasing Disk**, then automatic snapshots are deleted according to the retention duration you have selected. They are not automatically deleted by the system in the case that you replace the system disk, the corresponding instance expires, or the disk is released. You can [modify the automatic snapshot policy](intl.en-US/Snapshots/Use snapshots/Apply automatic snapshot policies to disks.md#) as needed.

## How do I delete a snapshot that I have used to create disks, images, or instances? {#section_hji_juh_uhk .section}

Snapshots that you have used to create disks or instances can be directly deleted. However, for snapshots that have been used to create images, you must delete the corresponding image before you delete the snapshot. Otherwise, the snapshot cannot be deleted.

## Will the snapshot policy fail to be implemented if I use an automatic snapshot to create a custom image or disk? {#section_xj5_5ws_ngb .section}

No, the snapshot policy will not fail to be implemented.

## Can I set multiple automatic snapshot policies for a single disk? {#section_dx2_bzg_4gb .section}

No, you can only have one automatic snapshot policy for a single disk at a time.

## Can I use a snapshot of the old system disk to roll back the new system disk after I replace the system disk? {#section_hpz_qkh_mgb .section}

No, you cannot use a snapshot of the old system disk to roll back the new system disk after you replace the system disk.

