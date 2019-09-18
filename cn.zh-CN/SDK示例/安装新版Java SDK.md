# 安装新版Java SDK {#concept_34917_zh .task}

相较于旧版Java SDK直接开放下载，阿里云新版Java SDK采用了Maven的方式分发。为方便统一管理，阿里云所有的Java SDK 均统一在同一个Maven项目中。

## 下载Maven软件 {#section_rf9_nim_962 .section}

访问[Maven 官方下载页面](http://maven.apache.org/download.cgi)下载对应操作系统的Maven软件。Checksum文件可供您校验下载文件是否正确无误。以下截图来自于Windows 7 64位操作系统，使用环境是Eclipse Luna。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10054/156879352613402_zh-CN.png)

## 安装Java SDK {#section_d80_mon_1qd .section}

完成以下操作，安装Java SDK：

1.  打开[Java SDK下载页面](http://develop.aliyun.com/sdk/java)，将阿里云的SDK存放的Maven库加入到Maven软件中。
2.  找到之前下载的Maven压缩包并解压，将下列Maven库信息添加到conf文件夹下的settings.xml文件中。 

    ``` {#codeblock_yeb_xi1_e5x}
    <repositories>
        <repository>
            <id>sonatype-nexus-staging</id>
            <name>Sonatype Nexus Staging</name>
            <url>https://oss.sonatype.org/service/local/staging/deploy/maven2/</url>
            <releases>
                <enabled>true</enabled>
            </releases>
            <snapshots>
                <enabled>true</enabled>
            <snapshots>
        </repository>
    </repositories>
    ```

3.  通过以下任一方式创建Maven项目： 
    -   方式一：在Eclipse添加一个Maven项目。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10054/156879352613404_zh-CN.png)

    -   方式二：将已有的项目转换为Maven项目。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10054/156879352613405_zh-CN.jpg)

4.  通过以下任一方式将dependency加入Maven项目中： 
    -   方式一：通过图形化界面选择性添加。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10054/156879352613406_zh-CN.jpg)

    -   方式二：打开Maven项目下的pom.xml文件，添加类似以下内容。您可以根据自身需要添加不同的依赖。

        ``` {#codeblock_8lk_aj1_ysd}
        <dependencies>
            <dependency>
                <groupId>com.aliyun</groupId>
                <artifactId>aliyun-java-sdk-core</artifactId>
                <version>2.1.6</version>
            </dependency>
            <dependency>
                <groupId>com.aliyun</groupId>
                <artifactId>aliyun-java-sdk-sts</artifactId>
                <version>2.1.0</version>
            </dependency>
            <dependency>
                <groupId>com.aliyun</groupId>
                <artifactId>aliyun-java-sdk-yundun</artifactId>
                <version>2.1.3</version>
            </dependency>
            <dependency>
                <groupId>com.aliyun</groupId>
                <artifactId>aliyun-java-sdk-slb</artifactId>
                <version>2.0.0-rc1</version>
            </dependency>
        </dependencies>
        ```

5.  保存更改。 Maven Dependencies中会自动下载并加入.jar后缀的相应阿里云SDK。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10054/156879352613408_zh-CN.jpg)


## 区分旧版SDK与新版SDK {#section_bww_hgv_j5l .section}

若您使用的是旧版SDK，建议您切换为新版SDK，获取最新功能。通过下表中的SDK参数，可以识别 SDK版本。

|对比项|旧版SDK|新版SDK|
|:--|:----|:----|
|如何提交请求|execute\(\)|getAcsResponse\(\)|
|如何存放AccessKey和AccessKeySecret的类|AliyunClient|IClientProfile|
|如何存放凭据对象|new DefaultAliyunClient\(APIUrl, Access Key, Access Key Secret\)|DefaultProfile.getProfile\(RegionId, Access Key, Access Key Secret\)|
|包名前缀|com.aliyun.api|com.aliyuncs|

