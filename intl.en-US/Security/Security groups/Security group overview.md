# Security group overview {#concept_o2y_mqw_ydb .concept}

A security group is a virtual firewall that provides Stateful Packet Inspection \(SPI\), also known as dynamic packet filtering. Security groups are used to allow or deny one or more ECS instances to access the Internet or intranet. Specifically, security groups logically isolate security domains in the cloud.

## Security group types {#section_m4b_bdb_3gb .section}

A security group is a logically isolated group of instances within the same region that all share the same security requirements and are mutually accessible. Each instance must belong to at least one security group. You need to specify the security group of instance when you create an instance. Instances in the same security group can communicate through the intranet. However, instances in different security groups are isolated from each other. You can set security group rules to authorize mutual access between two security groups to make instances in different groups no longer isolated from each other.

Security groups can be divided into default and custom security groups. The following table provides information about these two security group types.

|Security group type|Security group rule type|Security group rule priority|Inbound rule|Outbound rule|Scenario|
|:------------------|:-----------------------|:---------------------------|:-----------|:------------|:-------|
|Default security group|Default rules of the default security group|110|Enable ICMP, port SSH 22, and port RDP 3389. Disable other access. You can select Allow port HTTP 80 and port HTTPS 443.|Allow all access.|No custom security group exists in the same VPC.|
|Custom security group|Default rules of the custom security group|110|Deny all access.|Allow all access.|Custom security groups have been created in the same VPC, but no security group rules have been added to these security groups.|
|Custom rules of the custom security group|Custom. Value range: 1 to 100|Add security group rules as needed. For more information, see [Add security group rules](../../../../../reseller.en-US/Security/Security groups/Add security group rules.md#) and [Scenarios](../../../../../reseller.en-US/Security/Security groups/Scenarios.md#).|Add security group rules as needed. For more information, see [Add security group rules](../../../../../reseller.en-US/Security/Security groups/Add security group rules.md#) and [Scenarios](../../../../../reseller.en-US/Security/Security groups/Scenarios.md#).|Custom security groups have been created in the same VPC, and rules have been added to these security groups.|

Security group rules vary depending on network types.

Security group rules for classic networks can apply to either Internet access or intranet access. Security group rules for VPCs apply to both Internet access and intranet access. VPC instances can access the Internet through intranet NIC mapping. Therefore, an Internet NIC will be invisible in your instance. You can only set intranet rules in the security group. The security group rules apply to the intranet and the Internet.

## Security group priority {#section_mgh_wv1_wgb .section}

A smaller priority value of a security group rule indicates a higher priority.

ECS instances can belong to different security groups. As a result, instances may have multiple security group rules that apply to them and that have the same protocol type, port range, authorization type, and authorization object. The rule that takes effect depends on the priority and authorization policy settings of each rule.

-   If the priority among the rules is the same, then the corresponding 'deny' authorization rule takes effect and the 'allow' authorization rule does not take effect.
-   If the priority among the rules is different, the rule with a higher priority takes effect, regardless of the authorization policy settings of each of the rules.

## Procedure {#section_vkd_4kv_vgb .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9569/155403970542063_en-US.png)

## Security group precautions {#section_f2k_nmf_4gb .section}

-   Use a security group as a whitelist.
-   Observe the 'minimum authorization' principle when you configure inbound or outbound rules for applications. For example, you can allow a specific port \(such as port 80\).
-   Do not use one security group to manage all applications because requirements must be different at different layers.
-   Add instances with the same security requirements to the same security group. Do not set a separate security group for each instance.
-   Set simple security group rules. If you add an ECS instance to multiple security groups, hundreds of rules may apply to the instance. This may cause connection errors when you access the instance.
-   The ECS console allows you to clone a security group and security group rules. If you want to modify an active security group and its rules, we recommend that you clone the security group and modify the cloned security group to avoid impact on online applications.

