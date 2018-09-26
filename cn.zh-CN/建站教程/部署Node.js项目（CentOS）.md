# 部署Node.js项目（CentOS） {#concept_50775_zh .concept}

Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境，用来方便地搭建快速的易于扩展的网络应用。Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效，非常适合运行在分布式设备的数据密集型的实时应用。Node.js 的包管理器 npm，是全球最大的开源库生态系统。 典型的应用场景包括：

-   实时应用：如在线聊天，实时通知推送等等（如socket.io）
-   分布式应用：通过高效的并行I/O使用已有的数据
-   工具类应用：海量的工具，小到前端压缩部署（如grunt），大到桌面图形界面应用程序
-   游戏类应用：游戏领域对实时和并发有很高的要求（如网易的pomelo框架）
-   利用稳定接口提升Web渲染能力
-   前后端编程语言环境统一：前端开发人员可以非常快速地切入到服务器端的开发（如著名的纯Javascript全栈式MEAN架构）

## 适用对象 {#section_tss_tpl_2fb .section}

本文档介绍如何在阿里云CentOS系统的云服务器ECS实例上，安装Nodejs并部署项目。

## 准备工作 { .section}

部署之前，请做如下准备工作：

-   购买ECS实例
-   您的实例运行的镜像是CentOS7.2
-   您的实例可以连接公网
-   本地已经安装用于连接 Linux 实例的工具，如 [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/)。

## 基本流程 { .section}

使用云服务器ECS安装Nodejs并部署项目的操作步骤如下：

1.  购买ECS实例，并连接实例。
2.  选择以下任一种方法部署Node.js环境：
    -   使用二进制文件。
    -   使用NVM安装多版本。
3.  部署测试项目。

## 操作步骤 { .section}

**步骤 1：创建ECS实例**

[创建ECS实例](../../../../cn.zh-CN/个人版快速入门/步骤 2：创建ECS实例.md#)。选择操作系统为公共镜像CentOS7.2。使用root用户 [连接实例](../../../../cn.zh-CN/用户指南/连接实例/使用用户名密码验证连接Linux实例.md#)。

**步骤2：部署Node.js环境**

使用以下任一种方法部署Node.js环境。

-   使用二进制文件安装

    该部署过程使用的安装包是已编译好的二进制文件，解压之后，在bin文件夹中就已存在node和npm，无需手工编译。

    安装步骤：

    1.  wget命令下载Node.js安装包。该安装包是编译好的文件，解压之后，在bin文件夹中就已存在node和npm，无需重复编译。

        ```
        wget https://nodejs.org/dist/v6.9.5/node-v6.9.5-linux-x64.tar.xz
        ```

    2.  解压文件。

        ```
        tar xvf node-v6.9.5-linux-x64.tar.xz
        ```

    3.  创建软链接，使node和npm命令全局有效。通过创建软链接的方法，使得在任意目录下都可以直接使用node和npm命令：

        ```
        
        ln -s /root/node-v6.9.5-linux-x64/bin/node /usr/local/bin/node
        ln -s /root/node-v6.9.5-linux-x64/bin/npm /usr/local/bin/npm
        ```

    4.  查看node、npm版本。

        ```
        
        node -v
        npm -v
        ```

    5.  至此，Node.js环境已安装完毕。软件默认安装在/root/node-v6.9.5-linux-x64/目录下。如果需要将该软件安装到其他目录（如：/opt/node/）下，请进行如下操作：

        ```
        
        mkdir -p /opt/node/
        mv /root/node-v6.9.5-linux-x64/* /opt/node/
        rm -f /usr/local/bin/node
        rm -f /usr/local/bin/npm
        ln -s /opt/node/bin/node /usr/local/bin/node
        ln -s /opt/node/bin/npm /usr/local/bin/npm
        ```

-   使用NVM安装多版本

    NVM（Node version manager）是Node.js的版本管理软件，使用户可以轻松在Node.js各个版本间进行切换。适用于长期做 node 开发的人员或有快速更新node版本、快速切换node版本这一需求的用户。

    安装步骤：

    1.  直接使用git将源码克隆到本地的~/.nvm目录下，并检查最新版本。

        ```
        
        yum install git
        git clone https://github.com/cnpm/nvm.git ~/.nvm && cd ~/.nvm && git checkout `git describe --abbrev=0 --tags`
        ```

    2.  激活NVM。

        ```
        
        echo ". ~/.nvm/nvm.sh" >> /etc/profile
        source /etc/profile
        ```

    3.  列出Node.js的所有版本。

        ```
        nvm list-remote
        ```

    4.  安装多个Node.js版本。

        ```
        
        nvm install v6.9.5
        nvm install v7.4.0
        ```

    5.  运行 `nvm ls` 查看已安装Node.js版本，当前使用的版本为v6.9.5。返回结果如下所示。

        ```
        
        [root@iZXXXXZ .nvm]# nvm ls
        v6.9.5
        -> v7.4.0
        system
        stable -> 7.4 (-> v7.4.0) (default)
        unstable -> 6.9 (-> v6.9.5) (default)
        ```

    6.  运行 `nvm use v7.4.0` 切换Node.js版本至v7.4.0。返回结果如下所示。

        ```
        
        [root@iZXXXXZ .nvm]# nvm use v7.4.0
        Now using node v7.4.0
        ```

    NVM的更多操作请参考帮助文档：

    ```
    nvm help
    ```


**步骤3：部署测试项目**

1.  新建项目文件example.js。

    ```
    
    cd ~
    touch example.js
    ```

2.  使用vim编辑器打开项目文件example.js。

    ```
    
    yum install vim
    vim example.js
    ```

    输入 `i`，进入编辑模式，将以下项目文件内容粘贴到文件中。使用 `Esc` 按钮，退出编辑模式，输入 `:wq`，回车，保存文件内容并退出。

    项目文件内容：

    ```
    
    const http = require('http');
    const hostname = '0.0.0.0';
    const port = 3000;
    const server = http.createServer((req, res) => {
    res.statusCode = 200;
    res.setHeader('Content-Type', 'text/plain');
    res.end('Hello World\n');
    });
    server.listen(port, hostname, () => {
    console.log(`Server running at http://${hostname}:${port}/`);
    });
    ```

    **说明：** 项目文件内容中的3000为端口号，可以自行定义。

3.  运行项目。

    ```
    node ~/example.js
    ```

    **说明：** 您也可以使用命令 `node ~/example.js &` 将项目置于后台运行。

4.  使用命令查看项目端口是否存在。

    ```
    netstat -tpln
    ```

5.  [登录ECS管理控制台](https://ecs.console.aliyun.com/#/home)，并在安全组中 [添加安全组规则](http://help.aliyun.com/document_detail/25471.html) 放行端口（如本示例中为TCP 3000端口）。
6.  （可选）如果您的实例中开启了防火墙，必须添加端口的入站规则（如本示例中为TCP 3000端口）。
7.  在本地机器的浏览器中输入 `http://实例公网IP地址:端口号` 访问项目。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9770/153796073712144_zh-CN.png)


## 相关链接 { .section}

用户可通过云中沙箱平台体验上述文档中的操作，[点击此处。](https://edu.cloudcare.cn/courses/646394e08b66441ab43f7a5e037a318e/detail)

更多开源软件尽在云市场，[点击此处](https://market.aliyun.com/software)。

