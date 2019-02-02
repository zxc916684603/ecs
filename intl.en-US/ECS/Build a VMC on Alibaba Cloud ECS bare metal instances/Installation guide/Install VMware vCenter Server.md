# Install VMware vCenter Server {#task_abz_v5s_ggb .task}

This topic describes how to install VMware vCenter Server. By using VMware vCenter Server, you can manage multiple hosts from a physical or virtual Windows machine and use several advanced features.

1.  You have remotely connected to a Windows instance.

    **Note:** When you connect to the Windows instance, an identity authentication error may occur due to Windows patch updates. For more information, see [How to solve authentication errors caused by CredSSP encryption oracle remediation when connecting to Windows instances](https://www.alibabacloud.com/help/faq-detail/71931.htm).

2.  You have disabled the security enhancement configuration. Otherwise, a confirmation dialog box will be displayed repeatedly and interrupt the installation when you access a URL.

    **Note:** For more information, see [Internet Explorer Enhanced Security Configuration changes the browsing experience](https://support.microsoft.com/en-us/help/815141/internet-explorer-enhanced-security-configuration-changes-the-browsing).

3.  You have installed the Adobe Flash Player plugin.
4.  You have purchased and downloaded VMware vCenter Server.

1.   Double-click the VMware vCenter Server installation file, read the **End User License Agreement** and agree to the terms by selecting **I accept the terms of the license agreement**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83717/154886297535724_en-US.png)

 
2.   Select **Embedded Deployment**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83717/154886297635726_en-US.png)

 
3.   Set the user name and password, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83717/154886297635727_en-US.png)

 
4.  In the **System Name** text box, enter the IP address of the Windows instance, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83717/154886297635728_en-US.png) 
5.   Select **Use Windows Local System Account**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83717/154886297635729_en-US.png)

 
6.   Select **Use an embedded database \(VMware Postgres\)**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83717/154886297635730_en-US.png)

 
7.   In the **Configure Ports** dialog box, set the ports, as shown in the following figure, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83717/154886297635731_en-US.png)

 
8.   Set the **Destination Directory**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83717/154886297635732_en-US.png)

 
9.   Select **Join the VMware Customer Experience Improvement Program**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83717/154886297635733_en-US.png)

 
10.  In the **Ready to install** dialog box, confirm your settings, and then click **Install**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83717/154886297635734_en-US.png)

 
11.  Click **Launch vSphere Web Client**, or enter the IP address of the Windows instance in the browser to open the vSphere Web Client logon page.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83717/154886297635735_en-US.png)

 
12.  Enter the user name and password that you set for VMware vCenter Server, and then click **Login** to log on to VMware vCenter Server by using vSphere Web Client.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83717/154886297635963_en-US.png)

 Note: Log on to the vCenter Server from the Windows instance where vCenter Server is installed, otherwise the logon will fail.

