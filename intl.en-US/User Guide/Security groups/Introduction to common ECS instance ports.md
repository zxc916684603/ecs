# Introduction to common ECS instance ports {#concept_gbt_s21_ydb .concept}

The following table lists commonly used ECS instance ports.

|Port|Service|Description|
|21|FTP|A port opened by the FTP service is used for uploading and downloading files.|
|22|SSH|An SSH port is used to [connect to a Linux instance by using a password](reseller.en-US/User Guide/Connect to instances/Connect to a Linux instance by using a password.md#) in command-line mode.|
|23|Telnet|The Telnet port is used for Telnet to log on to the ECS instance.|
|25|SMTP|The port that is open to the SMTP service is used for sending mails.Based on security concerns, ECS instance 25 Port is restricted by default. Open a ticket to open it. See [apply to open TCP port 25](https://partners-intl.aliyun.com/help/doc-detail/56130.htm).

|
|80|HTTP|Provides access to HTTP services, such as IIS, Apache, and Nginx.You can [verify if TCP port 80 works properly](https://partners-intl.aliyun.com/help/faq-detail/59367.htm) for port troubleshooting.

|
|110|POP3|Used for the POP3 protocol, which is the protocol for sending and receiving emails.|
|143|IMAP|Used for IMAP \(Internet Message Access Protocol\), which is the protocol for receiving emails.|
|443|HTTPS|Used to provide access to the HTTPS service. HTTPS is a protocol that provides encryption and transmission through secure ports.|
|1433|SQL Server|The TCP port of the SQL Server is used for external service by SQL Server.|
|1434|SQL Server|SQL Server UDP port is used to return which TCP/IP port SQL Server uses.|
|1521|Oracle|Oracle communications port. The port which needs to be released by Oracle SQL is deployed on the ECS instance.|
|3306|MySQL|The port through which the MySQL database provides external service.|
|3389|Windows Server Remote Desktop Services|Windows Server Remote Desktop Services port can be used to [connect to a Windows instance](reseller.en-US/User Guide/Connect to instances/Connect to a Windows instance.md#).|
|8080|Proxy port|As with 80 port, port 8080 is commonly used in WWW agent service to achieve web browsing. If you are using port 8080, when you visit a Web site or use a proxy server, you must add `:8080` after the IP Address: 8080. After you install the Apache Tomcat service, the default service port is 8080.|
|137, 138, 139|NetBIOS protocol|-   137 and 138 are UDP ports that are used to transfer files through the network neighbor.
-   The connection entering through the port 139 attempts to obtain the NetBIOS/smb service.

NetBIOS protocols are often used for Windows files, printer sharing, and samba.|

## Some ports cannot be accessed {#section_whp_ff1_ydb .section}

Problem: The ECS instance listens for the corresponding port, but the port is not accessible in some areas, while other ports can be accessed normally.

Analysis: Some operators judge ports 135, 139, 444, 445, 5800, 5900, and so on as high-risk ports, so they are blocked by default.

Solution: We recommend that you change the port to other non-high-risk ports for business operation.

## Related topic {#section_b1p_qf1_ydb .section}

For more information on how to release a service port through a security group, see [add security group rules](reseller.en-US/User Guide/Security groups/Add security group rules.md#).

