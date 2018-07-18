# Introduction to common ECS instance ports {#concept_gbt_s21_ydb .concept}

The following is a list of commonly used ECS instance ports:

|Port|Service|Description|
|21|FTP|A port opened by the FTP service is used for uploading and downloading files.|
|22|SSH|An SSH port is used to pass through command-line mode [Connect to a Linux instance by using a password](intl.en-US/User Guide/Connect/Connect to a Linux instance by using a password.md#).|
|23|Telnet|The telnet port is used for telnet to log on to the ECS instance.|
|25|SMTP|The port that is open to the SMTP service is used for sending mail.Based on security concerns, ECS instance 25 Port is restricted by default. Please submit a job request to unseal. See [request to unseal TCP 25 Port](https://www.alibabacloud.com/help/doc-detail/56130.htm).

|
|80|HTTP|Provides access to HTTP services, such as IIS, Apache, and Nginx.You can see [Check if the TCP 80 port is working](https://www.alibabacloud.com/help/faq-detail/59367.htm)  for port troubleshooting.

|
|110|POP3|Used for the POP3 protocol, POP3 is the protocol for sending and receiving emails.|
|143|IMAP|Used for IMAP \(Internet Message Access Protocol\) protocol, IMAP is the protocol for receiving emails.|
|443|HTTPS|Used to provide access to the HTTPS service. HTTPS is a protocol that provides encryption and transmission through secure ports.|
|1433|SQL Server|The TCP port of the SQL Server is used to serve the SQL Server out-of-the-box.|
|1434|SQL Server|SQL Server's UDP port used to return which TCP/IP port SQL Server uses|
|1521|Oracle|Oracle communications port, the port on the ECS instance where Oracle SQL needs to be released.|
|3306|MySQL|The port on which the MySQL database provides services to the outside world.|
|3389|Windows Server Remote Desktop Services|Windows Server Remote Desktop Services port can be used through [Connect to a Windows instance](intl.en-US/User Guide/Connect/Connect to a Windows instance.md#).|
|8080|Proxy port|As with 80 port, port 8080 is commonly used in WWW agent service to achieve web browsing. If you are using port 8080, when you visit a Web site or use a proxy server, you need to add  `:8080` after the IP Address: 8080. After you install the Apache Tomcat service, the default service port is 8080.|
|137, 138, 139|NetBIOS protocol|-   137 and 138 are UDP ports that are used when transferring files through a network neighbor.
-   139 the connection entered through this port attempts to obtain the NetBIOS/smb service.

NetBIOS protocols are often used for Windows files, printer sharing, and samba.|

## Some ports cannot be accessed {#section_whp_ff1_ydb .section}

Phenomenon: the ECS instance listens for the corresponding port, but the port is not accessible in some areas, while other ports access normal conditions.

Analysis: some operators judge ports 135, 139, 444, 445, 5800, 5900, and so on as high-risk ports, the default is blocked.

Workaround: It is recommended that you modify the sensitive port to host the business for other non-high-risk ports.

## Reference Links {#section_b1p_qf1_ydb .section}

-   More about Windows instance service port instructions, refer to the  [Microsoft documentation Windows Server System Service overview and network port requirements](https://support.microsoft.com/zh-cn/kb/832017).
-   About how to release a service port through a security group, see [Add security group rules](intl.en-US/User Guide/Security groups/Add security group rules.md#).

