# Use the Eclipse plug-in to deploy applications {#concept_ak3_zpd_sfb .task}

Alibaba Cloud Toolkit for Eclipse \(Cloud Toolkit\) is a free plug-in used for integrated development environment \(IDE\). After you develop, debug, and test an application on the premises, you can use this plug-in to deploy the application to an ECS instance. This topic describes how to use the Eclipse plug-in to deploy a Java application on an ECS instance.

-   You have downloaded and installed [Java Development Kit \(JDK\) 1.8 or later](https://java.com/en/download/).
-   You have downloaded and installed [Eclipse IDE 4.5.0 or later](http://www.eclipse.org/downloads/). The program must be suitable for Java Enterprise Edition \(Java EE\) developers.
-   You must have an Alibaba Cloud account before you follow the instructions provided in the tutorial. To create an Alibaba Cloud account, click [Create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).

This topic describes how to install Cloud Toolkit in Eclipse on Windows, and efficiently deploy an application by using Cloud Toolkit.

## Procedure {#section_bi1_x2j_v96 .section}

To deploy a Java application by using the Eclipse plug-in on an ECS instance, follow these steps:

1.  [Install Cloud Toolkit](#section_swe_tkc_2ir)
2.  [Set the AccessKey pair](#section_qb9_4j0_0r9)
3.  [Download and upload the JDK installation package](#section_aux_qrq_9ny)
4.  [Prepare for installation](#section_942_mtv_3nn)
5.  [Install JDK Install Apache Tomc](#section_crs_eb3_tkq)
6.  [Install Apache Tomcat](#section_u3u_gdp_kuc)
7.  [Deploy a Java application to the ECS instance](#section_pwr_rqr_y6f)

## Step 1: Install Cloud Toolkit {#section_swe_tkc_2ir .section}

To install Cloud Toolkit, follow these steps:

1.  Start Eclipse.
2.  On the menu, choose **Help** \> **Install New Software...**. 

    ![Install new software](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/41804/156750405721799_en-US.png)

3.  Click **Add...** in the window that appears. 

    ![Add](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/41804/156750405730980_en-US.png)

4.  Enter a name such as Cloud Toolkit for Eclipse and the software location http://toolkit.aliyun.com/eclipse, and click **Add**. 

    ![Edit site information](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/41804/156750405731037_en-US.png)

5.  In the Name column, select **Alibaba Cloud Toolkit Core** and **Alibaba Cloud Toolkit Deployment Tools**, and clear **Contact all update sites during install to find required software** in the **Details** section, and then click **Next**. 

    ![Select components](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/41804/156750405731038_en-US.png)

6.  Click **Next**.
7.  Select **I accept the terms of the license agreement**, and click **Finish**.
8.  Click **Install anyway**. 

    ![Install anyway](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/41804/156750405730612_en-US.png)

9.  Click **Restart Now** to restart Eclipse. 

    ![Restart Eclipse](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/41804/156750405821860_en-US.png)


## Step 2: Set the AccessKey pair {#section_qb9_4j0_0r9 .section}

The AccessKey ID and AccessKey Secret are issued to users by Alibaba Cloud. An AccessKey ID is used to identify a user. An AccessKey Secret is used to encrypt the signature string and is the key that the server uses to authenticate the signature string. The AccessKey pair must be kept confidential.

To set the AccessKey ID and AccessKey Secret, follow these steps:

1.  On the toolbar, choose **Window** \> **Preferences**. 

    ![Preferences](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/41804/156750405830995_en-US.png)

2.  In the left-side navigation pane, choose **Alibaba Cloud Toolkit** \> **Accounts**.
3.  Enter the **AccessKey ID** and **AccessKey Secret**, and click **Apply and Close**. 

    **Note:** 

    -   If you have an account but have not generated any AccessKey pair, click **Get existing AK/SK**, and log on to the Alibaba Cloud console to generate an AccessKey pair. For more information, see [Create an AccessKey pair](../../../../../intl.en-US/General Reference/Create an AccessKey.md#).
    -   If you have not created any account, click **Sign up**.
    ![Set the account](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/41804/156750405830215_en-US.png)


## Step 3: Download and upload the JDK installation package {#section_aux_qrq_9ny .section}

To download and upload the JDK installation package, follow these steps:

1.  Download [Apache Tomcat](https://mirrors.aliyun.com/apache/tomcat/tomcat-8/v8.5.34/bin/apache-tomcat-8.5.34.tar.gz). 

    **Note:** The source code is constantly upgraded. You can click [here](https://mirrors.aliyun.com/apache/tomcat/tomcat-8/) to obtain the required installation package address.

2.  Download the [JDK installation package](https://www.oracle.com/technetwork/java/javase/downloads/index.html). 

    **Note:** If you download the JDK package on an ECS instance, an error occurs during decompression. You can download the JDK installation package to your local directory and upload the package to the ECS instance.

3.  Log on to the [ECS console](https://ecs.console.aliyun.com).
4.  In the left-side navigation pane, choose **Instances & Images** \> **Images**.
5.  In the top navigation bar, select a region.
6.  Find the ECS instance, and obtain the public IP address of the instance from the **IP Address** column.
7.  Start Windows Secure Copy \(WinSCP\), use the public IP address to connect to the Linux ECS instance, and then upload the JDK installation package to the root directory of the Linux ECS instance.

## Step 4: Prepare for installation {#section_942_mtv_3nn .section}

To prepare for installation, follow these steps:

1.  [Connect to a Linux instance by using the Management Terminal](../intl.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using the Management Terminal.md#).
2.  Add inbound rules to support the required ports. For more information, see [Add security group rules](../intl.en-US/Security/Security groups/Add security group rules.md#).
3.  Disable the firewall. 
    1.  Run the command `systemctl status firewalld` to check the state of the firewall. 

        ![Check the state of the firewall](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64105/156750405832172_en-US.png)

        -   If the firewall stays in the inactive state, the firewall is disabled.
        -   If the firewall stays in the active state, the firewall is enabled. In this example, the firewall is in the active state, so you must disable the firewall.
    2.  Disable the firewall. Skip this step if the firewall is in the inactive state. 
        -   To temporarily disable the firewall, run the command `systemctl stop firewalld`.

            **Note:** Therefore, the firewall is temporarily disabled, and will remain in the active state when you restart Linux next time.

        -   To permanently disable the firewall, run the command `systemctl disable firewalld`.

            **Note:** You can enable the firewall again. For more information, see [Firewalld documentation](https://firewalld.org/).

4.  Disable Security-Enhanced Linux \(SELinux\). 
    1.  Run the `getenforce` command to check the state of SELinux. 

        ![Check the state of SELinux](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9763/156750405821065_en-US.png)

        -   If SELinux stays in the Disabled state, SELinux is disabled.
        -   If SELinux stays in the Enforcing state, SELinux is enabled. In this example, SELinux is in the Enforcing state, so you must disable SELinux.
    2.  Disable SELinux. Skip this step if SELinux is in the Disabled state. 
        -   To temporarily disable SELinux, run the command `setenforce 0`.

            **Note:** Therefore, SELinux is temporarily disabled, and will remain in the Enforcing state when you restart Linux next time.

        -   To permanently disable SELinux, follow these steps: Run the command `vi /etc/selinux/config`, and press the Enter key. Move the pointer to the line of `SELINUX=enforcing`, and press the `i` key to enter the edit mode. Edit the SELinux state in this way: `SELINUX=disabled`. Afterward, press the `Esc` key, type `:wq`, and then press the `Enter` key to save and close the SELinux configuration file.

            **Note:** You can enable SELinux again. For more information, see [SELinux documentation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/ch-selinux#s1-SELinux-resources).

    3.  Restart the system to make the changes take effect.
5.  Create a user named www to run Tomcat. 

    ``` {#codeblock_jz5_np6_ehx}
    useradd www
    ```

6.  Creates a root directory for the Java Web project. 

    ``` {#codeblock_ok7_o0f_arv}
    mkdir -p /data/wwwroot/default
    ```

7.  Assign the file permission under the root directory of the website to www. 

    ``` {#codeblock_jfu_ub4_abe}
    chown -R www.www /data/wwwroot
    ```


## Step 5: Install JDK {#section_crs_eb3_tkq .section}

To install JDK, follow these steps:

1.  Run mkdir /usr/java to create a directory. 

    ``` {#codeblock_wvp_0v9_z1e}
    mkdir /usr/java
    ```

2.  Decompress the JDK installation package jdk-8u191-linux-x64.tar.gz in this example to /usr/java. 

    ``` {#codeblock_47o_ywc_jw3}
    chmod +x jdk-8u191-linux-x64.tar.gz
    tar xzf jdk-8u191-linux-x64.tar.gz -C /usr/java
    ```

3.  Set environment variables. 
    1.  Run the command `vi /etc/profile` to open the /etc/profile file.
    2.  Press the `i` key to enter the edit mode.
    3.  Add the following lines into the /etc/profile file. 

        ``` {#codeblock_hg1_omf_i94}
        # set java environment
        export JAVA_HOME=/usr/java/jdk1.8.0_191
        export CLASSPATH=$JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib
        export PATH=$JAVA_HOME/bin:$PATH
        ```

    4.  Press the `Esc` key to exit the edit mode, and type `:wq` to save and close the file.
4.  Run the command `source /etc/profile` to load environment variables.
5.  Run the `java -version` command to check the JDK version. 

    The following response indicates that JDK has been installed.

    ![JDK installed](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9766/156750405830641_en-US.png)


## Step 6: Install Apache Tomcat {#section_u3u_gdp_kuc .section}

To install Apache Tomcat, follow these steps:

1.  Run the following commands in sequence to decompress the package apache-tomcat-8.5.34.tar.gz, rename the Tomcat directory, and then set user permissions. 

    ``` {#codeblock_p1m_hd2_6xt}
    tar xzf apache-tomcat-8.5.34.tar.gz
    mv apache-tomcat-8.5.34 /usr/local/tomcat/
    chown -R www.www /usr/local/tomcat/
    ```

    The directory /usr/local/tomcat/ contains the following files:

    -   The bin directory stores some Tomcat script files, including scripts for enabling and disabling the Tomcat service.
    -   The conf directory stores various global configuration files for the Tomcat server, including the important files server.xml and web.xml.
    -   The webapps directory is the main Web publishing directory of Tomcat to store Web application files by default.
    -   The logs directory stores Tomcat log files.
2.  Configure the server.xml file. 
    1.  Run the command `cd /usr/local/tomcat/conf/` to switch to the directory /usr/local/tomcat/conf/.
    2.  Run the command `mv server.xml server.xml_bk` to rename the server.xml file.
    3.  Run the `vi server.xml` command.
    4.  Press the `i` key to enter the edit mode.
    5.  Add the following code: 

        ``` {#codeblock_0ee_tc5_2mn}
        <? xml version="1.0" encoding="UTF-8"? >
        <Server port="8006" shutdown="SHUTDOWN">
        <Listener className="org.apache.catalina.core.JreMemoryLeakPreventionListener"/>
        <Listener className="org.apache.catalina.mbeans.GlobalResourcesLifecycleListener"/>
        <Listener className="org.apache.catalina.core.ThreadLocalLeakPreventionListener"/>
        <Listener className="org.apache.catalina.core.AprLifecycleListener"/>
        <GlobalNamingResources>
        <Resource name="UserDatabase" auth="Container"
         type="org.apache.catalina.UserDatabase"
         description="User database that can be updated and saved"
         factory="org.apache.catalina.users.MemoryUserDatabaseFactory"
         pathname="conf/tomcat-users.xml"/>
        </GlobalNamingResources>
        <Service name="Catalina">
        <Connector port="8080"
         protocol="HTTP/1.1"
         connectionTimeout="20000"
         redirectPort="8443"
         maxThreads="1000"
         minSpareThreads="20"
         acceptCount="1000"
         maxHttpHeaderSize="65536"
         debug="0"
         disableUploadTimeout="true"
         useBodyEncodingForURI="true"
         enableLookups="false"
         URIEncoding="UTF-8"/>
        <Engine name="Catalina" defaultHost="localhost">
        <Realm className="org.apache.catalina.realm.LockOutRealm">
        <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
          resourceName="UserDatabase"/>
        </Realm>
        <Host name="localhost" appBase="/data/wwwroot/default" unpackWARs="true" autoDeploy="true">
        <Context path="" docBase="/data/wwwroot/default" debug="0" reloadable="false" crossContext="true"/>
        <Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
        prefix="localhost_access_log." suffix=".txt" pattern="%h %l %u %t &quot;%r&quot; %s %b" />
        </Host>
        </Engine>
        </Service>
        </Server>
        ```

    6.  Press the `Esc` key to exit the edit mode, and type `:wq` to save and close the file.
3.  Set Java virtual machine \(JVM\) memory parameters. 
    1.  Run the command `vi /usr/local/tomcat/bin/setenv.sh` to create a file named /usr/local/tomcat/bin/setenv.sh.
    2.  Press the `i` key to enter the edit mode.
    3.  Add the following code: 

        ``` {#codeblock_wjo_fbk_fig}
        JAVA_OPTS='-Djava.security.egd=file:/dev/./urandom -server -Xms256m -Xmx496m -Dfile.encoding=UTF-8'
        ```

    4.  Press the `Esc` key to exit the edit mode, and type `:wq` to save and close the file.
4.  Set a script to enable Tomcat to run at startup. 
    1.  Run the command `wget https://github.com/lj2007331/oneinstack/raw/master/init.d/Tomcat-init` to download the script.
    2.  Run the command `mv Tomcat-init /etc/init.d/tomcat` to rename the Tomcat-init file.
    3.  Run the command `chmod +x /etc/init.d/tomcat` to assign the execute permission to the script file.
    4.  Run the following code to set the JAVA\_HOME script for automatic startup. 

        ``` {#codeblock_680_9j0_apu}
        sed -i 's@^export JAVA_HOME=.*@export JAVA_HOME=/usr/java/jdk1.8.0_191@' /etc/init.d/tomcat
        								
        ```

5.  Set automatic startup. 

    ``` {#codeblock_5dn_xpw_o6r}
    chkconfig --add tomcat
    chkconfig tomcat on
    ```

6.  Start Tomcat. 

    ``` {#codeblock_9br_91d_hod}
    service tomcat start
    ```


## Step 7: Deploy a Java application to the ECS instance {#section_pwr_rqr_y6f .section}

You can use Cloud Toolkit to deploy a Java application to the ECS instance. Then, you connect to http://Public IP address of the ECS instance:8080 to view `Tomcat test`. Follow these steps:

1.  In Eclipse, right-click the name of the application project that you want to deploy, and choose **Alibaba Cloud** \> **Deploy to ECS...**. 

    ![Deploy to ECS](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/41804/156750405830615_en-US.png)

2.  In the window Deploy to Alibaba Cloud that appears, follow these settings: 

    -   **Deploy File**: the deployment method, such as **Upload File** in this example. If you build the application project by using Maven, select **Maven Build**.
    -   **Choose File**: the file that you want to deploy.
    -   **Target Deploy ECS**: specifies the region where your instance is located and the target instance.
    -   **Deploy Location**: the directory that you deploy on the ECS instance, such as /data/wwwroot/default in this example.
    -   **Command**: Click **Select...**, and in the dialog box that appears, click **Add...**. Enter a command in the text box. The ECS instance runs the command automatically after the Cloud Toolkit plug-in deploys the Java application to the directory on the ECS instance. In this example, enter the `service tomcat restart` command to restart Tomcat. You can also enter another command as needed.
    ![Enter a command](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/41804/156750405830623_en-US.png)

3.  Click **Deploy** to start deploying the Java application to the ECS instance.
4.  In the **Console** section of Eclipse, you can view the progress of the deployment. 

    ![View the progress](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/41804/156750405830632_en-US.png)

5.  Open your browser, and in the address bar, enter the URL `http://Public IP address of the ECS instance:8080` to connect to the ECS instance. 

    The following response indicates that the Java application has been deployed to the ECS instance by using the Alibaba Cloud Toolkit for Eclipse plug-in.

    ![Java application deployed](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9766/156750405812137_en-US.png)


You can modify the Java application in Eclipse, save the code, and then use the Cloud Toolkit plug-in again to deploy the modified file to the ECS instance.

