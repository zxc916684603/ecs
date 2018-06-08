# SSH 密钥对 {#concept_j33_vqw_ydb .concept}

## 什么是 SSH 密钥对 {#section_shx_vqw_ydb .section}

SSH 密钥对，常简称为密钥对，是阿里云为您提供的新的远程登录 ECS 实例的认证方式，是一种区别于传统的用户名加密码模式的认证方式。

SSH 密钥对通过加密算法生成一对密钥，一个对外界公开，称为 **公钥**，另一个您自己保留，称为 **私钥**。

如果您将公钥配置在 Linux 实例中，那么，在本地或者另外一个 ECS 实例中，您可以使用私钥通过 SSH 命令或相关工具登录实例，而不需要输入密码。如果使用 SSH 密钥对登录 Linux 实例，默认禁用密码登录，以提高安全性。

## 功能优势 {#section_thx_vqw_ydb .section}

相较于传统的用户名和密码认证方式，使用 SSH 密钥对有以下优势：

**安全性**

SSH 密钥对登录认证更为安全可靠：

-   密钥对安全强度远高于常规用户口令，可以杜绝暴力破解威胁。

-   不可能通过公钥推导出私钥。


**便捷性**

-   只需在控制台和本地客户端做简单配置即可 远程登录实例，再次登录时无需再输入密码。

-   便于远程登录大量 Linux 实例，方便管理。如果您需要批量维护多个 ECS 实例，推荐使用这种方式登录。


## 使用限制 {#section_xhx_vqw_ydb .section}

使用 SSH 密钥对有如下限制：

-   仅支持 Linux 实例。
-   目前，阿里云只支持创建 2048 位的 RSA 密钥对。
    -   阿里云会保存密钥对的公钥部分。
    -   密钥对创建成功后，您需要妥善保管私钥。
    -   私钥使用未加密的 PEM（Privacy-enhanced Electronic Mail） 编码的 `PKCS#8` 格式。
-   一个云账号在一个地域最多可以拥有 500 个密钥对。
-   一个 Linux 实例只能绑定一个 SSH 密钥对。如果您的实例已绑定密钥对，绑定新的密钥对会替换原来的密钥对。
-   基于数据安全考虑，在 ECS 实例状态为 **运行中 （Running）** 绑定或者解绑密钥对时，您需要 重启实例 使操作生效。
-   除了系列 I 的非 I/O 优化实例外，所有 实例规格族 均支持 SSH 密钥对登录。

## 阿里云的 SSH 密钥对 {#section_a3x_vqw_ydb .section}

SSH 密钥对的生成方式包括：

-   由阿里云生成，默认采用 RSA 2048 位的加密方式。
-   使用其他方式生成后再导入阿里云，导入的密钥对必须支持下列任一种加密方式：
    -   rsa
    -   dsa
    -   ssh-rsa
    -   ssh-dss
    -   ecdsa
    -   ssh-rsa-cert-v00@openssh.com
    -   ssh-dss-cert-v00@openssh.com
    -   ssh-rsa-cert-v01@openssh.com
    -   ssh-dss-cert-v01@openssh.com
    -   ecdsa-sha2-nistp256-cert-v01@openssh.com
    -   ecdsa-sha2-nistp384-cert-v01@openssh.com
    -   ecdsa-sha2-nistp521-cert-v01@openssh.com

如果您的密钥对由阿里云生成，那么，在首次生成密钥对时，您必须下载并妥善保存私钥。当该密钥对绑定某个 ECS 实例时，如果没有私钥，您将再也不能登录该 ECS 实例。

## 相关操作 {#section_v3y_1rw_ydb .section}

-   如果您没有 SSH 密钥对，可以在 ECS 控制台 [创建 SSH 密钥对](../cn.zh-CN/用户指南/密钥对/创建 SSH 密钥对.md#)。
-   如果您使用其它工具生成了密钥对，可以在 ECS 控制台 [导入 SSH 密钥对](../cn.zh-CN/用户指南/密钥对/导入 SSH 密钥对.md#)。
-   如果您不再需要某个密钥对，可以在 ECS 控制台 [删除 SSH 密钥对](../cn.zh-CN/用户指南/密钥对/删除 SSH 密钥对.md#)。
-   如果您想使用或者禁用 SSH 密钥对访问已经创建好的 ECS 实例，可以在 ECS 控制台 [绑定 / 解绑 SSH 密钥对](../cn.zh-CN/用户指南/密钥对/绑定 / 解绑 SSH 密钥对.md#)。
-   您可以在 [创建实例](../cn.zh-CN/个人版快速入门/步骤 2：创建ECS实例.md#) 时指定 SSH 密钥对。
-   您可以 [使用SSH密钥对连接Linux实例](../cn.zh-CN/用户指南/连接实例/使用SSH密钥对连接Linux实例.md#)。

