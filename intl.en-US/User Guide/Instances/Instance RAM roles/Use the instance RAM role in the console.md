# Use the instance RAM role in the console {#concept_v3v_zct_xdb .concept}

## Limits {#section_x4c_cdt_xdb .section}

The instance RAM role has the following limits:

-   The instance RAM role is only applicable to VPC instances.
-   One instance RAM role can be bound to one instance at a time.
-   After an instance RAM role is attached to an ECS instance, if you want to access other cloud services, such as OSS, SLB, or ApsaraDB for RDS, from the applications within the ECS instance, you must [Metadata](intl.en-US/User Guide/Instances/User-defined data and metadata/Metadata.md#) of the instance RAM role by using metadata. See [6. \(Optional\). Obtain the authorization credential](#Token).
-   Before using this feature, the RAM user must be [7. \(Optional\). Authorize a RAM user to use the instance RAM role](#Authorize).

## Prerequisites {#section_z4c_cdt_xdb .section}

You must have activated the RAM service. See [Activation method](../../../../intl.en-US/Pricing/Activation method.md#) to activate the RAM service.

## 1. Create an instance RAM role {#step2 .section}

1.  Log on to the [RAM console](https://ram.console.aliyun.com/#/overview).
2.  On the left-side navigation pane, click **Roles**.
3.  Click **Create Role**.
4.  In the dialog box:
    1.  Select **Service Role** for **Role Type**.
    2.  Select **ECS \(Elastic Compute Service\)** for **Type**.
    3.  Enter the role name and description, for example, EcsRamRoleDocumentTesting.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9665/15391709975501_en-US.png)

    4.  Click **Create** to create the instance RAM role.

## 2. Authorize the instance RAM role {#section_q1m_sst_xdb .section}

1.  Log on to the [RAM console](https://ram.console.aliyun.com/#/overview).
2.  On the left-side navigation pane, click **Policy**.
3.  Click **Create Authorization Policy**.
4.  In the dialog box:
    1.  Select **Blank Template** for **authorization policy template**.
    2.  Enter the **Authorization Policy Name** and **Policy Content**, for example,  EcsRamRoleDocumentTestingPolicy.

        **Note:** For more information about how to write the authorization policy by using the JSON language, see [Policy syntax structure](../../../../intl.en-US/User Guide/Policy Language/Policy syntax structure.md#).

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9665/15391709975502_en-US.png)

    3.  Click **Create Authorization Policy** to complete authorization.
5.  On the left-side navigation pane, click **Roles**.
6.  On the Roles page, select the created role, for example, EcsRamRoleDocumentTesting, and click **Authorize**.
7.  Enter the **authorization policy name** and click it, for example, EcsRamRoleDocumentTestingPolicy.
8.  Click the icon **\>** to select the policy name, and click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9665/15391709975503_en-US.png)


## 3. Attach an instance RAM role {#section_mpc_cdt_xdb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  On the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Find the target ECS instance and select **More \>** \> **Attach/Detach RAM Role**.
5.  Select Attach for Action, select the created role, for example, EcsRamRoleDocumentTesting, and click **OK** to attach the instance RAM role.

## \(Optional\). Detach an instance RAM role {#section_wn3_bwt_xdb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  On the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Select an ECS instance, and select ** More \>** \> **Attach/Detach RAM Role**.
5.  Select **Detach** for **Action**, and click **OK** to detach the instance RAM role.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9665/15391709975506_en-US.png)


## 5. \(Optional\). Replace an instance RAM role {#section_wfl_2wt_xdb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  On the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Select an ECS instance, and select ** More \>** \> **Attach/Detach RAM Role**.
5.  Select **Attach** for **Action**, select another instance RAM role in the list of RAM Role, and click **OK** to replace the current RAM role.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9665/15391709985507_en-US.png)


## 6. \(Optional\). Obtain the authorization credential {#Token .section}

For the internal application of an ECS instance, you can obtain the STS credential of the instance RAM role, which is a metadata of an instance, to access the role-authorized permissions and resources. The credential is updated periodically. Example:

1.  Connect and log on to your ECS instance.
2.  Obtain the STS credential of the instance RAM role, for example, EcsRamRoleDocumentTesting:
    -   Linux instance: run  `curl http://100.100.100.200/latest/meta-data/Ram/security-credentials/EcsRamRoleDocumentTesting`.
    -   Windows instance: see [Metadata](intl.en-US/User Guide/Instances/User-defined data and metadata/Metadata.md#).
3.  Get the credential. Return example:

    ```
    
    
    "AccessKeyId" : "XXXXXXXXX",
    "AccessKeySecret" : "XXXXXXXXX",
    "Expiration" : "2017-11-01T05:20:01Z",
    "SecurityToken" : "XXXXXXXXX",
    "LastUpdated" : "2017-10-31T23:20:01Z",
    "Code" : "Success"
    
    ```


## 7. \(Optional\). Authorize a RAM user to use the instance RAM role {#Authorize .section}

**Note:** You must grant the RAM user with the **PassRole** permission to use the instance RAM role feature. Without the **PassRole** permission, a RAM user cannot carry out the permission of the authorization policy that is attached to the RAM user.

Log on to the RAM console and authorize a RAM user [Attach policies to a RAM user](../../../../intl.en-US/Quick Start/Attach policies to a RAM user.md#) to complete the authorization, see the following code snippet as an authorization policy example:

```


        "Version": "2016-10-17",
        "Statement": [

            "Effect": "Allow",
            "Action": [
                "ecs: [ECS RAM Action]",
                "ecs: CreateInstance",
                "ecs: AttachInstanceRamRole",
                "ecs: DetachInstanceRAMRole"

            "Resource": "*"


        "Effect": "Allow",
        "Action": "ram:PassRole",
        "Resource": "*"



```

The parameter \[ECS RAM Action\] indicates the action that a ram user can be authorized. For more information, see [Authorization rules](../../../../intl.en-US/API Reference/Authorization rules.md#).

## References {#section_bxr_pwt_xdb .section}

-   You can also [Use the instance RAM role by calling APIs](intl.en-US/User Guide/Instances/Instance RAM roles/Use the instance RAM role by calling APIs.md#).
-   You may want to [Access other cloud products by using the instance RAM role](https://www.alibabacloud.com/help/doc-detail/54579.htm).

