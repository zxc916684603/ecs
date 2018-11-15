# 一键部署LNMP环境 {#concept_53077_zh .concept}

LNMP分别代表Linux、Nginx、MySQL、PHP。本文介绍如何使用阿里云资源编排服务（ROS）一键在ECS实例搭建LNMP环境。

ROS是阿里云官网提供的免费服务，无需下载安装。您可以使用ROS创建JSON格式的资源栈模板文件，或者使用ROS提供的 [模板样例](https://ros.console.aliyun.com/#/template/list) 创建一组阿里云资源。在本教程中，我们会使用ROS控制台提供的 **LNMP\_basic** 模板，自动创建一台ECS实例，并在实例上部署LNMP环境。

## 前提条件 {#section_k3s_4p2_2fb .section}

创建按量付费资源时，账号余额不能低于100.00元，可以是现金、可用信用额度或者可用于开通产品的代金券。

## 操作步骤 { .section}

1.  登录 [ROS管理控制台](https://ros.console.aliyun.com/)。

    **说明：** 如果您是首次使用ROS，必须先开通ROS服务。ROS服务免费，开通服务不会产生任何费用。

2.  在左侧导航栏中，选择 **关键帮助** \> **ECS实例相关信息**，获取您需要的ECS实例规格、可用区ID（ZoneId）和镜像ID（ImageId）。
3.  在左侧导航栏中，单击 **模板样例**。
4.  从模板样例中，找到 **LNMP\_basic**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9761/154115239212071_zh-CN.png)

5.  单击 **预览** 按钮查看模板的JSON文件。JSON文件各个顶级字段的解释如下表所示。

    |顶级字段|解释|
    |`"ROSTemplateFormatVersion" : "2015-09-01"`|定义模板版本。|
    |     ```
"Description": "Deploy LNMP(Linux+Nginx+MySQL+PHP) stack on 1 ECS instance. ***
              WARNING *** Only support CentOS-7."
    ```

 |解释说明模板。|
    |`"Parameters" : { }`|定义模板的一些参数。本示例中，模板定义的参数包括：镜像ID、实例规格等，并指定了默认值。|
    |`"Resources" : { }`|定义这个模板将要创建的阿里云资源。本示例中，申明将要创建一个ECS实例和一个安全组，这里申明的资源属性可以引用`Parameters`中定义的参数。|
    |`"Outputs": { }`|定义资源创建完成后，栈需要输出的资源信息。本示例中，资源创建完成后将输出ECS实例ID、公网IP地址和安全组ID。|

    **说明：** 关于ROS资源栈模板的更多信息，请参见资源编排的 [模板结构说明](../../../../cn.zh-CN/.md#)。

6.  单击 **创建Stack**。
7.  在 **直接输入** 部分，在 **所在region** 的下拉框中选择具体地域，并在页面右下角单击 **下一步**。本例选择 **华东2**。
8.  在 **启动栈** 部分，设置参数：

    -   **栈名**：设置一个栈名，不可重复，而且创建之后不能修改。
    -   **创建超时**：设置一个时间。如果在设置的时间段内资源未创建成功，则判断超时。您可以选择是否 **失败回滚**。如果选择失败回滚，那么创建过程中发生任何失败（包括创建超时），ROS都会删除已经创建成功的资源。
    -   **NginxDownloadUrl**：使用默认的Nginx下载地址。
    -   **DBPassword** 和 **Please Confirm DBPassword**：设置并确认访问MySQL数据库的密码。根据模板定义，密码只能包括英文字母和数字。
    -   **ZoneId**：填写您需要创建资源的可用区ID。详见第2步。
    -   **ImageId**：填写创建ECS实例时使用的镜像ID。详见第2步。
    -   **DBName**：填写MySQL数据库名。
    -   **DBUser**：填写MySQL数据库的用户名。
    -   **DBRootPassword** 和 **Please Confirm DBRootPassword**：设置并确认MySQL root账号的密码。根据模板定义，密码只能包括英文字母和数字。
    -   **InstanceType**：填写您需要的ECS实例规格。详见第2步。
    -   **SystemDiskCategory**：选择云盘类型，作为系统盘。
    -   **InstancePassword** 和 **Please Confirm InstancePassword**：设置并确认实例的登录密码。根据模板定义，密码只能包括大写或小写英文字母和数字。
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9761/154115239212072_zh-CN.png)

9.  单击 **创建**，页面将提示 **请求提交成功**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9761/154115239214330_zh-CN.png)

10. 在左侧导航栏中，单击 **资源栈管理** 查看栈的状态。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9761/154115239214331_zh-CN.png)

11. 点击新创建的栈的名称，在打开的**栈概况**页面的**输出**部分查看`Outputs`中定义的`NginxWebsiteURL`。您能通过这个地址访问创建好的LNMP环境。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9761/154115239214341_zh-CN.png)

    **说明：** 

    -   在**资源**列表中查看栈中所有资源。
    -   在**事件**列表中查看ROS创建这个资源栈过程中产生的操作记录。任何涉及资源栈的操作失败了，列表中都会显示资源操作失败的原因。
    -   在**模板**列表中查看资源栈的原始模板。

## 参考信息 {#section_rzz_xs2_2fb .section}

您还可以使用ROS提供的其他模板样例搭建环境，比如Java Web测试环境、Node.js测试开发环境、Ruby Web开发测试环境或Hadoop/Spark分布式系统。

更多模板，请参见 [模板样例](https://ros.console.aliyun.com/#/template/list)。

更多ROS信息，请参见 [ROS帮助中心](../../../../cn.zh-CN/.md#) 和 [ROS云栖博客](https://yq.aliyun.com/articles/57553)。

