# ECS disk encryption {#concept_udk_5wj_ydb .concept}

## What is ECS disk encryption {#concept .section}

When you want to encrypt the data stored on a disk due to business needs or certification requirements, you can use ECS disk encryption function to encrypt cloud disks and shared block storage \(referred to collectively as  **cloud disks**, unless otherwise specified\). This secure encryption feature allows you to encrypt new cloud disks. You do not have to create, maintain, or protect your own key management infrastructure, nor change any of your existing applications or maintenance processes. In addition, no extra decryption operations are required, so the operation of the disk encryption function is practically invisible to your applications or your operations.

Encryption and decryption barely degrades cloud disk performance. For information on the performance testing method, see [Storage parameters and performance test](intl.en-US/Product Introduction/Block storage/Storage parameters and performance test.md#).

After an encrypted cloud disk is created and attached to an ECS instance, the data in the following list can be encrypted:

-   Data on the cloud disk.
-   Data transmitted between the cloud disk and the instance. However, data in the instance operating system is not encrypted.
-   All snapshots created from the encrypted cloud disk. These snapshots are called encrypted snapshots.

Encryption and decryption are performed on the host that runs the ECS instance, so the data transmitted from the ECS instance to the cloud disk is encrypted.

ECS disk encryption supports all available cloud disks \(basic cloud disks, ultra cloud disks, and SSD cloud disks\) and shared block storage \(ultra and SSD\).

ECS disk encryption supports all available instance types.

## ECS disk encryption dependencies {#dependencies .section}

The ECS disk encryption function depends on the Key Management Service \(KMS\) in the same region. However, you are not required to perform any additional operations in the KMS console, unless you want to perform separate KMS operations.

The first time you use the ECS disk encryption function when you are creating ECS instances or cloud disks, you must follow the prompts to authorize and activate KMS. Otherwise, you cannot create encrypted cloud disks or instances with encrypted disks.

If you use an API or the CLI to use the ECS disk encryption function, such as CreateInstance or CreateDisk, you must first activate KMS on the Alibaba Cloud website.

The first time you encrypt a disk in a given region, Alibaba Cloud automatically creates a Customer Master Key \(CMK\) in the KMS region, exclusively for ECS. You cannot delete this CMK and can query it in the KMS console.

## Key management for ECS disk encryption {#kms .section}

The ECS disk encryption function handles key management for you. Each new cloud disk is encrypted by using a unique 256-bit key \(derived from the CMK\). This key is also associated with all snapshots created from this cloud disk and any cloud disks subsequently created from these snapshots. These keys are protected by the key management infrastructure of Alibaba Cloud provided by KMS. This approach implements strong logical and physical security controls to prevent unauthorized access. Your data and the associated keys are encrypted by using an industry standard AES-256 algorithm.

You cannot change the CMK associated with encrypted cloud disks and snapshots.

The key management infrastructure of Alibaba Cloud conforms to the recommendations in \(NIST\) 800-57 and uses cryptographic algorithms that comply with the \(FIPS\) 140-2 standard.

Each Alibaba Cloud account has a unique CMK for ECS product in each region. This key is separate from the data and stored in a system protected by strict physical and logical security controls. Each encrypted disk uses an encryption key unique to the specific disk and its snapshots. The encryption key is created from and encrypted by the CMK for the current user in the current region. The disk encryption key is only used in the memory of the host that runs your ECS instance. The key is never stored in plaintext in any permanent storage media \(such as a disk\).

## Fees {#fees .section}

ECS does not charge any additional fees for the disk encryption function.

The CMK that ECS creates for you in each region is a service key. It does not consume your master key quota in a given region and no additional fees are incurred.

**Note:** No additional fees are charged for any **read/write operations** on a disk, such as mount/umount, partitioning, and formatting. However, when you perform operations on an encrypted disk in the ECS console or by using APIs, KMS APIs are called and such calls consume the KMS API quota in the current region.

These operations include:

-   Creating encrypted cloud disks by calling CreateInstance or CreateDisk.
-   Attaching an encrypted cloud disk to an instance by calling AttachDisk.
-   Detaching an encrypted cloud disk from an instance by calling DetachDisk.
-   Creating a snapshot by calling CreateSnapshot.
-   Restoring a cloud disk by calling ResetDisk.
-   Re-initializing a cloud disk by calling ReInitDisk.

## Create an encrypted cloud disk {#howtocreate .section}

Currently, only cloud disks can be encrypted. You can create an encrypted cloud disk in the following ways:

-   Create a cloud disk as a data disk when creating an ECS instance:

    -   Check Encrypted to create a encrypted blank cloud disk.
    -   Select an encrypted screenshot to create a cloud disk.
-   When using APIs or the CLI:

    -   Set the parameter `DataDisk.n.Encrypted` \(CreateInstance\) or Encrypted  `Encrypted` \(CreateDisk\) to `true`.
    -   In CreateInstance or CreateDisk, specify the `SnapshotId` parameter of the encrypted snapshot.

## Convert unencrypted data to encrypted data {#convert .section}

You cannot directly convert an **unencrypted disk** to an **encrypted disk**. Likewise, you cannot convert a snapshot created from an **unencrypted disk** to an **encrypted snapshot**.

You cannot directly convert an **unencrypted disk** to an **encrypted disk**. Likewise, you cannot convert a snapshot created from an **unencrypted disk** to an **encrypted snapshot**.

Therefore, if you must encrypt existing data from an **unencrypted disk** to an **encrypted snapshot**, we recommend that you use the `rsync` command in a Linux instance or the `robocopy` command in a Windows instance to copy data from an **unencrypted disk** to a \(new\) **encrypted disk**.

If you must encrypt existing data from an **encrypted disk** to an **unencrypted snapshot**, we recommend that you use the `rsync` command in a Linux instance or the `robocopy` command in a Windows instance to copy data from an **encrypted disk** to a \(new\) **unencrypted disk**.

## Limits {#limits .section}

ECS disk encryption has the following limits:

-   You can only encrypt cloud disks, not local disks or ephemeral disks.
-   You can only encrypt data disks, not system disks.
-   You cannot directly convert existing unencrypted disks into encrypted disks.
-   You cannot convert encrypted disks into unencrypted disks.
-   You cannot convert unencrypted snapshots to encrypted snapshots.
-   You cannot convert encrypted snapshots to unencrypted snapshots.
-   You cannot share images created from encrypted snapshots.
-   You cannot copy images created from encrypted snapshots across regions.
-   You cannot export images created from encrypted snapshots.
-   You cannot choose your CMKs for each region, as these are generated by the system.
-   The ECS system creates CMKs for each region. You cannot delete these keys, but no fees are incurred.
-   After a cloud disk is encrypted, you cannot change the CMK used for encryption and decryption.

