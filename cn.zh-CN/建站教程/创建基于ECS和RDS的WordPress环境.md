# 创建基于ECS和RDS的WordPress环境 {#concept_51137_zh .concept}

您可以在资源编排服务ROS \(Resource Orchestration Service\)中通过模版创建一组阿里云资源。ROS 控制台已经提供一些常用的模版样例。本文将使用一个 ROS 模版创建基于 ECS 和 RDS 的 WordPress 环境。

ROS 模版是一个 JSON 格式文本文件，您可以在这个文本中定义自己的阿里云资源。

## 前提条件 {#section_eqb_n4l_2fb .section}

阿里云规定创建资源时，账号需要有超过 100 元的现金、可用信用额度或者可用于开通产品的代金券。

## 操作步骤 { .section}

1.  登录 [ROS 管理控制台](https://ros.console.aliyun.com)。

    **说明：** 如果您是首次使用 ROS ，那么需要接受 ROS 的协议，同意开通 ROS 服务。ROS 服务是免费，开通服务不会产生任何费用。

2.  在控制台左侧导航栏中，单击 **模版样例**，页面显示 ROS 提供的常用模版。
3.  从模版示例中找到 **wordpress\_instance**，通过这个模版将创建基于 ECS 和 RDS 的 WordPress 环境。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9767/153796025712140_zh-CN.png)

4.  每个模版样例下方都有一个 **预览** 和 **创建** 按钮，单击 **预览** 将显示 JSON 模版，单击 **创建 stack** 。

    这个 JSON 文本包含五个顶级字段：

    -   定义模版版本版本：`"ROSTemplateFormatVersion" : "2015-09-01"`。
    -   定义对模版的解释说明：`"Description": "一个简配的ecs实例，包括一个安全组，用户只需要指定imageId"`。
    -   定义模版的一些参数，本例中定义了镜像ID的参数，实例规格的参数，并指定了默认值： `"Parameters" : { }`。
    -   定义这个模版将要创建的阿里云资源，本例中申明将要创建一个 ECS 实例和一个安全组；这里申明的资源属性可以引用 `Parameters` 中定义的参数：`"Resources" : { }`。
    -   定义资源创建完成后，通过 ROS 的栈输出资源信息。本例中，将输出 ECS 实例的 ID ，公网 IP 和安全组 ID：`"Outputs": { }` 
    **说明：** 您可以在线编写模板，也可以通过 URL 地址获取模板。

5.  在 创建 Stack 的页面中，**所在region** 的下拉框中选择具体地域，本例选择 **华东1**，在页面右下角单击 **下一步**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9767/153796025712141_zh-CN.png)

6.  填写所有带 **\*** 的选项，完成后单击 **创建**，页面将提示 **创建请求提交成功**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9767/153796025712142_zh-CN.png)

7.  单击左侧导航栏的 **资源栈管理** 查看 stack 的状态。当栈创建成功后，`Outputs`中定义的那些值，就会输出。

    **说明：** 通过 **资源** 可以查看 stack 中的所有资源；通过 **事件** 可以查看 ROS 创建这个资源栈时的操作记录。任何涉及资源栈的操作失败了，会显示具体操作哪个资源失败的原因；通过 **模版** 可以查看资源栈的原始模版。


以上示例只是通过 ROS 的文本模版快速创建资源， ROS 也可以通过用户指定的模版 URL 地址创建资源。除此之外，ROS 同时有管理资源的能力。用户可以删除自己的资源组，或者只删除 stack 而保留资源，还能根据自己的需求更新一个资源栈，重新检查资源栈的状态等等。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9767/153796025712143_zh-CN.png)

若您想了解 ROS 中资源创建的其它操作，详情请参见 [快速入门](https://help.aliyun.com/document_detail/48749.html?spm=5176.doc28852.6.545.zToBRn) 。

