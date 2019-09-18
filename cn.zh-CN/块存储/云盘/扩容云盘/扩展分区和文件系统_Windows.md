# 扩展分区和文件系统\_Windows {#concept_rjc_l5h_ydb .task}

扩容云盘只是扩大存储容量，不会扩容文件系统。您需要参照本文描述自行格式化新增的存储容量，以便扩展存储空间。

1.  创建快照以备份数据，防止操作失误导致数据丢失。具体操作，请参见[创建快照](cn.zh-CN/快照/使用快照/创建快照.md#)。
2.  通过ECS控制台或者API扩容云盘。
3.  云盘已挂载到实例上，实例已处于**运行中**状态。
4.  数据盘已完成分区格式化。具体操作，请参见[Windows分区格式化数据盘](../cn.zh-CN/个人版快速入门/格式化数据盘/Windows格式化数据盘.md#)。

本文仅适用于状态为**使用中**的云盘，且所挂载的实例状态为**运行中**。

-   对于待挂载数据盘，请参见[挂载云盘](cn.zh-CN/块存储/云盘/挂载云盘.md#)和[分区格式化数据盘](../cn.zh-CN/个人版快速入门/格式化数据盘/Windows格式化数据盘.md#)。
-   数据盘扩容后容量大于2048GiB时，您必须使用GPT分区格式。如果您已经使用了MBR分区格式，但无需保留数据盘上的数据，请参见[Windows实例更换分区格式步骤](cn.zh-CN/块存储/云盘/分区格式化数据盘/分区格式化大于2 TiB数据盘.md#Windows2012Snapshot)。

## 扩展系统盘分区 {#section_h4v_txm_qgb .section}

在ECS控制台上扩容系统盘后，对应系统盘分区的文件系统并未扩容。您需要连接实例扩容文件系统。本示例中以Windows Server 2008 R2企业版64位中文版操作系统为例。扩容前的系统盘容量为50GiB，扩容为72GiB，文件系统类型为NTFS。

1.  [远程连接Windows实例](cn.zh-CN/实例/连接实例/连接Windows实例/在本地客户端上连接Windows实例.md#)。
2.  打开服务器管理器。
3.  在左侧导航栏中，选择**存储** \> **磁盘管理**。
4.  选择**操作** \> **刷新**或**操作** \> **重新扫描磁盘** 。 

    ![重新扫描磁盘](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9678/156878083841660_zh-CN.png)

5.  在磁盘管理区域，查看未分配容量。本例中，**磁盘 0**是扩容的系统盘。 

    ![磁盘管理](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9678/156878083941658_zh-CN.png)

6.  右键单击**磁盘 0**主分区的空白处，并选择**扩展卷**。 

    ![Windows系统盘扩展卷](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9678/156878083960967_zh-CN.png)

7.  根据扩展卷向导的指示完成扩展卷操作。 

    ![Windows扩展系统盘卷Gif](images/60971_zh-CN.gif)

    完成后，新增空间会自动合入原来的卷中，如下图所示。

    ![扩展卷向导](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9678/156878083941657_zh-CN.png)


## 扩展数据盘分区 {#section_hbw_5lw_dhb .section}

在ECS控制台上扩容数据盘后，数据盘的每个分区的文件系统并未扩容。您需要连接实例扩容文件系统。本示例中以Windows Server 2008 R2企业版64位中文版操作系统为例。扩容前的数据盘容量为80GiB，扩容为120GiB，文件系统类型为NTFS。

1.  [远程连接Windows实例](cn.zh-CN/实例/连接实例/连接Windows实例/在本地客户端上连接Windows实例.md#)。
2.  打开服务器管理器。
3.  在左侧导航栏中，选择**存储** \> **磁盘管理**。
4.  选择**操作** \> **刷新**或**操作** \> **重新扫描磁盘**。 

    ![重新扫描磁盘](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9678/156878083841660_zh-CN.png)

5.  在磁盘管理区域，查看未分配的数据盘容量。本例中，**磁盘 1**是扩容的数据盘。 

    ![磁盘管理](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9678/156878083941665_zh-CN.png)

6.  扩展**磁盘 1**。 
    -   如果新磁盘空间用于扩容已有的分区，按照以下步骤完成扩容：
        1.  右键单击**磁盘1**主分区的空白处，并选择**扩展卷**。

            ![扩展卷](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9678/156878083941661_zh-CN.png)

        2.  根据扩展卷向导的指示完成扩展卷操作。

            完成后，新增的数据盘空间会自动合入原来的卷中。

            ![扩展卷向导](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9678/156878083941662_zh-CN.png)

    -   如果新磁盘空间用于增加新的分区，按照以下步骤完成扩容：
        1.  右键单击**磁盘1**未分配区的空白处，并选择**新建简单卷**。

            ![新建简单卷](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9678/156878083941663_zh-CN.png)

        2.  根据新建简单卷向导的指示完成扩展卷操作。

            完成后，新增的数据盘空间会新建一个分区。

            ![新建简单卷向导](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9678/156878083941664_zh-CN.png)


**相关文档**  


[扩展分区和文件系统\_Linux系统盘](cn.zh-CN/块存储/云盘/扩容云盘/扩展分区和文件系统_Linux系统盘.md#)

[扩展分区和文件系统\_Linux数据盘](cn.zh-CN/块存储/云盘/扩容云盘/扩展分区和文件系统_Linux数据盘.md#)

