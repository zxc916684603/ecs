# Manage user-created databases hosted on an ECS instance {#task_wyv_z3g_chb .task}

This topic describes how to use Alibaba Cloud Data Management Service \(DMS\) to manage user-created MySQL databases hosted on an ECS instance.

1.  [Purchase DMS](https://www.alibabacloud.com/help/doc-detail/47558.htm).
2.  Create an ECS instance. For more information, see [Create an instance by using the wizard](../../../../intl.en-US/Instances/Create an instance/Create an instance by using the wizard.md#).
3.  Add an inbound security group rule to the ECS instance to enable the default port \(port 3306\) on which MySQL is listening.
4.  Install a MySQL database on the ECS instance.
5.  Create a non-root account for the MySQL database.

    **Note:** By default, MySQL does not allow remote access from the root account. If you have changed the default settings to allow remote access from the root account, you can skip this step.

    In this example, run the following command to create an account named dms for the MySQL database and set the password to 123456.

    ``` {#codeblock_vtr_fia_m9v}
    grant all on *.* to 'dms'@'%'IDENTIFIED BY '123456';
    ```


DMS is a Web terminal developed by Alibaba Cloud to help manage your databases hosted on ECS instances that run Windows or Linux. You can use DMS by adding your databases through the SMS console. For example, you can create databases and tables. DMS supports such databases as MySQL, SQLServer, PostgreSQL, MongoDB, and Redis. For more information, see [DMS features](https://www.alibabacloud.com/help/doc-detail/47552.htm).

1.  Log on to the [Data Management Service console](https://dms.console.aliyun.com/#/dms/cloud/login).
2.  In the left-side navigation pane, click **User-created Databases \(ECS, Internet\)**.
3.  Click **Add Database**.
4.  Set the database parameters as needed. 

    The following table describes the database parameters.

    |Parameter|Description|
    |:--------|:----------|
    |Database Type|The type of the database hosted on the ECS instance. In this example, select MySQL.|
    |undefinedInstance Source|Valid values: Internet-based User-Created; ECS-based User-Created. In this example, select ECS-based User-Created.|
    |Region|The region to which the ECS instance belongs.|
    |ECS InstanceID|The ID of the ECS instance.|
    |Port|The number of the port used for listening to the database hosted on the ECS instance. In this example, the port configured for MySQL is 3306.|
    |Databases Username|The username of the database hosted on the ECS instance. In this example, the username of the MySQL database is dms. **Note:** We recommend that you use a non-root account.

 |
    |Password|The password corresponding to the username of the database hosted on the ECS instance. In this example, the password of dms is 123456.|

5.  Click **Logon**. After you log on, the data management page is displayed.

You can manage the database by using the following menus in the top navigation bar:

-   **Create**: creates databases, tables, database users, procedures, functions, views, triggers, and events. For more information, see [Database development](https://www.alibabacloud.com/help/doc-detail/47645.htm).
-   **SQL Operations**: opens the SQL window to run database management commands, including the ability to edit command results. For more information, see [SQL operations](https://www.alibabacloud.com/help/doc-detail/47673.html).
-   **Data Operation**: imports, exports, automatically generates, traces, backs up, and restores data, and clones databases and compares table structures. For more information, see [Data management](https://www.alibabacloud.com/help/doc-detail/47661.html).
-   **Instance Management**: manages the binlog file of the database and calculates the table data volume.
-   **Monitoring Alarm & Diagnosis Optimization**: manages database diagnosis, slow SQL analysis, space diagnosis, instance sessions, real-time performance, and diagnosis reports through the **Performance** menu.
-   **Tools**: manages databases, users, ER diagrams, and batch operations, and generates documents \(Word/Excel/PDF\).

