# Add security group rules {#concept_sm5_2wz_xdb .concept}

You can add security group rules to enable or disable access to and from the Internet or intranet for ECS instances in the security group:

-   VPC: You only need to set inbound and outbound rules. Also, you do not need to create different rules for private networks and Internet. The rules apply to Internet and intranet access at the same time. The Internet access for VPC instance is realized through private NIC mapping. So, you cannot see the Internet NIC inside the instance, and you can only set intranet rules in the security group. The rules apply to Internet and intranet access at the same time.
-   Classic network: It is required to set outbound and inbound rules for Internet and intranet respectively.

Changes to the security group rules are automatically applied to ECS instances in the security group.

## Prerequisite {#section_fxy_lwz_xdb .section}

You have created a security group. For more information, see [Creating a Security Group](intl.en-US/User Guide/Security groups/Creating a Security Group.md#).

You know which Internet or intranet requests need to be allowed or dropped for your instance.

## Procedure {#section_trd_pwz_xdb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  In the left-side navigation pane, select **Networks & Security ** \> **Security group**.
4.  Find the security group to add authorization rules, and in the **Actions** column click **Configure Rules**.
5.  On the Security Group Rules page, click **Add Security Group Rules**.

    **Note:** If you do not need to enable or disable all ports for all protocols, ICMP, or GRE, you can select **Quickly Create Rules**.

    |Protocol|SSH|telnet|HTTP|HTTPS|MS SQL|
    |Port|22|2, 3|80.|443|1433|
    |Protocol|Oracle|MySQL|RDP|PostgreSQL|Redis|
    |Port|1521|3306|3389|5432|6379|

    **Note:** See step 6 for descriptions on each parameter configuration.

6.  In the pop-up dialog box, set the following parameters:
    -   **NIC**:
        -   For a VPC-Connected security group, you can skip selecting the NIC. Note:
            -   If your instances can access the Internet, the rules work for both the Internet and intranet.
            -   If your instances cannot access the Internet, the rules work for intranet only.
        -   For a classic network-connected security group, you must select **Internet** or **Intranet**.
    -   **Rule Direction**:
        -   **Outbound**: ECS instances access other ECS instances over intranet networks, or through Internet resources.
        -   **Inbound**: Other ECS instances in the intranet and Internet resources access the ECS instance.
    -   **Authorization Policy**: Select **Allow** or **Drop**.

        **Note:** **Drop** policies discard the data packet without returning a response. If two security group rules overlap except the authorization policy, the **Drop** rule takes priority over the **Allow** rule.

    -   **Protocol Type** and **Port Range** The port range setting is affected by the selected protocol type. The following table shows the relationship between protocol types and port ranges.

        |Protocol Type|Port Range|Use cases|
        |All|Shown as -1/-1, indicating all ports. You cannot set.|Used in scenarios where both the applications are fully and mutually trusted.|
        |All ICMP|Shown as -1/-1, indicating no port restriction. You cannot set.|range for the ICMP protocol. Used to detect the instance’s network connection status by using `ping`.|
        |All GRE|Shown as -1/-1, indicating no port restriction. You cannot set.|Used for VPN service.|
        |Custom TCP|For custom port ranges, the valid port value 1−65535, and the valid port range format is Start Port/End Port. A valid port range format must be used for one port. For example, use 80/80 to indicate port 80.|It can be used to allow or deny one or several successive ports.|
        |Custom UDP|
        |SSH|Shown as 22/22.After connecting to the ECS instance, you can modify the port number, in particular, see [Server default remote port modifications](https://www.alibabacloud.com/help/doc-detail/51644.htm).

|For SSH to connect to a Linux instance remotely.|
        |TELNET|Shown as 23/23.|Used to remotely log on to instances by using telnet.|
        |HTTP|Shown as 80/80.|The instance is used as a server for a website or a web application.|
        |HTTPS|Shown as 443/443.|The instance is used as a server for a website or a web application that supports the HTTPS protocol.|
        |MS SQL|Shown as 1433/1433.|The instance is used as a MS SQL server.|
        |Oracle|Shown as 1521/1521.|The instance is used as an Oracle SQL server.|
        |MySQL|Shown as 3306/3306.|The instance is used as a MySQL server.|
        |RDP|Shown as 3389/3389, the default RDP port 3389.After connecting to the ECS instance, you can modify the port number, in particular, see  [Server default remote port modifications](https://www.alibabacloud.com/help/doc-detail/51644.htm).

|Used to remotely connect to Windows instances.|
        |PostgreSQL|Shown as 5432/5432.|The instance is used as a PostgreSQL server.|
        |Redis|Shown as 6379/6379.|The instance is used as a Redis server.|

        **Note:** Port 25 is restricted by default and cannot be opened through security group rules, but you can [apply for the unseal of port 25](https://www.alibabacloud.com/help/doc-detail/56130.htm). For more common port information, see [Introduction to common ECS instance ports](intl.en-US/User Guide/Security groups/Introduction to common ECS instance ports.md#).

    -   **Authorization Type** and **Authorization Object**: The authorization object affects setting of authorization type. The following table shows the relationship between them.

        |Authorization Type|Authorization object|
        |Address field access|Use the IP or CIDR block format such as 10.0.0.0 or 192.168.0.0/24. Only IPv4 addresses are supported. 0.0.0.0/0 indicates all IP addresses.|
        |Security Group Access|Only for intranet access. Authorize the instances in a security group under your account or another account to access the instances in this security group.        -   Authorize This Account: Select a security group under your account. Both security groups must be in the same VPC.
        -   Authorize Other Account: Enter the target security group ID and the Account ID. On the **Account Management** \> **Security Settings** You can obtain the account ID.
For VPC network instances, Security Group Access works for private IP addresses only. If you want to authorize Internet IP address access, use **Address Field Access**.|

        **Note:** To guarantee the security of your instance, when you are configuring an intranet inbound rule for a classic network-connected security group, **Security Group Access** is the top priority for Authorization Type. If  **Address Field Access**, and you want to type an IP address in the CIDR format, type an IP address in the format of a.b.c.d/32. Only 32 is the valid CIDR prefix.

    -   **Priority**: 1 ~ The smaller the 100, the higher the priority. For more information, see [ECS security group rule priority explanation](intl.en-US/User Guide/Security groups/Add security group rules.md#priority).

         

7.  Click **OK**.

Security group rules are usually activated immediately, though some delay is possible.

## Verify security group rules {#section_r1s_jzz_xdb .section}

If you have installed a web service in the instance and added a security group rule in a security group: allow all IP addresses to have inbound access to TCP port 80 of the instance. Follow these steps according to your instance OS to verify the security group rule.

**Linux instances:**

For a Linux instance in the security group, follow these steps to verify the security group rule

1.  [Connect to a Linux instance by using a password](intl.en-US/User Guide/Connect/Connect to a Linux instance by using a password.md#).
2.  Run the following command to check whether TCP 80 is being listened.

    ```
    netstat -an | grep 80
    ```

    If the following result returns, web service for TCP port 80 is enabled.

    ```
    tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN
    ```

3.  Type `http://public IP address of the instance` in the address bar of a browser. If access is successful, the rules have been activated.

**Windows instances:**

For a Windows instance in the security group, follow these steps to verify the security group rule

1.  [Connect to a Windows instance](intl.en-US/User Guide/Connect/Connect to a Windows instance.md#).
2.  Run **cmd**, and run the following command to check whether TCP Whether 80 is being listened.

    ```
    netstat -aon | findstr :80
    ```

    Describe TCP if the following results are returned Port 80 is already open.

    ```
    TCP 0.5.0.0: 80 0.5.0.0: 0 listening 1172
    ```

3.  Enter the  `http: // instance public IP address` in the browser address bar. If access is successful, the rules have been activated.

## ECS security group rule priority explanation {#priority .section}

The Priority of a security group rule can be a number from 1 to 100. A smaller number indicates a higher priority.

ECS instances can belong to different security groups. As a result, instances may have multiple security group rules that have the same protocol types, port ranges, authorization types, and authorization objects. The rule that takes effect depends on the setting of Priority and Authorization Policy:

-   If the rules have the same **priority**, the **Drop** rule takes effect, and the **Allow** rule does not.
-   If the rules have different **priorities**, the rule with higher priority will be effective first, regardless the setting of **Authorization Policy** .

## Related topics {#section_pql_d11_ydb .section}

-   [Security Group FAQ](https://www.alibabacloud.com/help/faq-detail/40570.htm)
-   [Security groups](../../../../intl.en-US/Product Introduction/Network and security/Security groups.md#)
-   [Default security group rules](intl.en-US/User Guide/Security groups/Default security group rules.md#)
-   [Description of matching order for priority execution of rules in ECs security groups](https://www.alibabacloud.com/help/faq-detail/40642.htm)

