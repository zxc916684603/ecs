# SVN概览 {#concept_pqr_4bb_ffb .concept}

Subversion（简称SVN）是一个开源的版本控制系统，管理随时间改变的数据。本文介绍了SVN的概念和使用流程。

## SVN简介 {#section_esy_dcb_ffb .section}

SVN管理的数据存放在中央资料档案库（Repository）中。该档案库会记录文件的每一次变动，这样您就可以把数据恢复至旧版本或浏览文件的变动历史。SVN中常用的概念和操作如下：

-   Repository（源代码库）：源代码统一存放的地方。
-   Checkout（提取）：该操作用于从Repository中提取一份源代码到本地。
-   Commit（提交）：该操作用于将修改代码后的代码提交到Repository。
-   Update（更新）：该操作用于同步本地源代码与Repository中的源代码。

使用SVN管理代码的常见流程为：

1.  Checkout（您提取源代码到本地）。
2.  其他人修改并提交源代码到Repository。
3.  Update（您获得最新的代码）。
4.  您修改并调试成功源代码。
5.  Commit（提交修改后的代码到Repository，其他程序员即可看到您的修改）。

SVN管理源代码的单位为行。如果您与其他程序员同时修改了一个文件中的代码：

-   若修改的代码在不同行，SVN会自动合并两种修改。
-   若修改的代码在同一行，SVN会提示文件冲突（Conflict），需要手动确认。

## 使用流程 {#section_zpd_31d_vxl .section}

SVN服务支持svnserve和http访问模式，这两种访问模式的部署方法如下：

-   [部署svnserve访问SVN](intl.zh-CN/建站教程/搭建和使用SVN/部署svnserve访问SVN.md#)
-   [部署http访问SVN](intl.zh-CN/建站教程/搭建和使用SVN/部署http访问SVN.md#)

SVN部署完成后，您可以在SVN中执行提交修改、获取更新和还原文件等操作。详情请参见[使用SVN](intl.zh-CN/建站教程/搭建和使用SVN/使用SVN.md#)。

