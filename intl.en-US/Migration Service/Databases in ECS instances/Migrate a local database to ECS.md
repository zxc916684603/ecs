# Migrate a local database to ECS {#task_xcw_3yb_wgb .task}

Alibaba Cloud Data Transmission Service \(DTS\) allows you to exchange data between various data sources, such as RDBMS, NoSQL, and OLAP. This topic provides an example scenario that describes how to configure a DTS migration task to migrate data from a MySQL database in your on-premises data center to an ECS instance on Alibaba Cloud.

-   Create an ECS instance. For more information, see [Create an instance by using the wizard](../../../../reseller.en-US/Instances/Create an instance/Create an instance by using the wizard.md#).
-   In the security group of the ECS instance, allow inbound access to the port on which the MySQL server listens. The default MySQL port is 3306.
-   Install the MySQL server on the ECS instance.
-   Create a non-root account for the MySQL database on the ECS instance.

    For example, you can run the following command to create an account for the MySQL database, with the name as dts and the password as 123456.

    ``` {#codeblock_2ed_jz1_hw6}
    grant all on *.*  to 'dts'@'%'  IDENTIFIED BY '123456';
    ```

-   Create a non-root account for the local MySQL database.

DTS allows you to migrate data between heterogeneous and homogeneous data sources. It also provides multiple ETL features such as three-level object mapping \(for databases, tables, and columns\) and data filtering. You can use DTS for zero-downtime migration. During the migration process, the source database continues to provide services, minimizing the impact of migration on your business. For information about the databases supported by DTS, see [Data migration](https://partners-intl.aliyun.com/help/doc-detail/26594.htm).

1.  Log on to the [DTS console](https://partners-intl.console.aliyun.com/#/dts).
2.  In the left-side navigation pane, select **Data Migration.**
3.  Select the target region, and click **Create Migration Task**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/129677/156880166539331_en-US.png)

4.  Configure a migration task. 
    1.  Specify a task name. 

        You can use the default name or specify one.

    2.  Configure the source database. 

        DTS supports databases accessed through the Internet, leased lines, VPN gateways, and intelligent gateways. The following configurations are described in terms of a database accessed through the Internet. For the migration scheme of other types of databases, see the DTS user manual.

        |Parameter|Description|
        |:--------|:----------|
        |Instance Type|The database with a public IP address.|
        |Instance Region|The region to which the database belongs.|
        |Database Engine|The type of the local database, MySQL in this example.|
        |Host Name or IP Address|The host name or IP address of the server where the local database exists.|
        |Port|The port number on which the MySQL server listens.|
        |Database Account|The non-root account for accessing the local MySQL database. **Note:** The database account cannot be a root account. Otherwise, errors will occur during connection tests.

 |
        |Database Password|The password for the non-root account.|

    3.  Click **Test the Connection** in the lower right corner of the Source Database area. 

        If the result **Test Passed** is returned, the source database has connected.

    4.  Configure the target database. 

        |Parameter|Description|
        |:--------|:----------|
        |Instance Type|The database in the ECS instance.|
        |Instance Region|The region to which the ECS instance belongs.|
        |ECS Instance ID|The ID of the ECS instance. DTS supports ECS instances in classic networks or VPCs.|
        |Database Engine|The same as the local database, MySQL in this example.|
        |Port|The port number on which the MySQL server listens.|
        |Database Account|The non-root account for accessing the MySQL database in the ECS instance. **Note:** The database account cannot be a root account. Otherwise, errors will occur during connection tests.

 |
        |Database Password|The password for the non-root account.|

    5.  Click **Test the Connection** in the lower right corner of the Target Database area. 

        If the result **Test Passed** is returned, the target database has connected.

    6.  Click **Authorize Whitelist and Enter into Next Step.**
5.  Configure the migration type and migration object. 
    1.  Configure the migration type. 
        -   Zero downtime migration: Select Structure migration + Full data migration + Incremental data migration.
        -   Full data migration: Select Structure migration + Full data migration.
    2.  Configure the migration object. 

        In the **Migration Object** box, click the database object to migrate, such as a database, table, or column. Then click **\>**to add it to the **Selected Objects** box.

        **Note:** By default, after a database object is By default, after a database object is migrated to a MySQL database in your ECS instance, the object name remains the same as that in the local MySQL database. If the migrated database object has different names on the source and target instances, you need to use the object name mapping function provided by DTS to meet the requirements. For more information, see [Object name mapping](https://partners-intl.aliyun.com/help/doc-detail/26628.htm).

6.  Click **Pre-Check and Start**. 

    Before migration begins, DTS pre-checks the connectivity, authority, and log format of the database.

    After the pre-check is successful, you can view the status and progress of your tasks in the **Migration Task List**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/128824/156880166539321_en-US.png)


