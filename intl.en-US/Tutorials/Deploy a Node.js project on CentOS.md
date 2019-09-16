# Deploy a Node.js project on CentOS {#concept_50775_zh .task}

This topic describes how to install Node.js and deploy a project on an ECS instance that runs CentOS 7.2.

-   You have installed PuTTY on the computer that you use for connecting to the ECS instance. You can click [here](https://www.chiark.greenend.org.uk/~sgtatham/putty/) to download PuTTY.
-   You must have an Alibaba Cloud account before you follow the instructions provided in the tutorial. To create an Alibaba Cloud account, click [Create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).

Node.js is a JavaScript runtime built on Chrome V8 engine. You can use Node.js to efficiently build an online application that supports easy extension. Node.js uses an event-driven and non-blocking I/O model. This lightweight and efficient model is suitable for data-intensive real-time applications that run on distributed devices. The Node.js package manager \(npm\) is the largest ecosystem of open source libraries in the world. Node.js is applicable to the following typical scenarios:

-   Real-time applications: instant messaging and real-time notifications, such as Socket.IO.
-   Distributed applications: efficient parallel I/O to consume existing data.
-   Utilities: a variety of utilities from front-end compression and deployment applications such as grunt to desktop graphical user interface applications.
-   Game applications: real-time and high-concurrency applications in the game field, such as the Pomelo framework of NetEase.
-   Stable functions to improve the performance of rendering Web pages.
-   Consistent front-end and back-end programming environments: applications that allow front-end developers to easily take on server-side development, such as the full-stack Javascript MongoDB, Express.js, AngularJS, and Node.js. \(MEAN\) framework.

## Procedure {#section_z74_yzt_kll .section}

To install Node.js on an ECS instance and deploy a project, follow these steps:

1.  [Step 1: Create and connect to an ECS instance](#section_e0r_tml_c8k)
2.  [Step 2: Deploy the Node.js environment](#section_tug_p3l_h9l)
3.  [Step 3: Deploy a test project](#section_igz_e58_4zq)

## Step 1: Create and connect to an ECS instance {#section_e0r_tml_c8k .section}

To create and connect to an ECS instance, follow these steps:

1.  Use the public image 64-bit CentOS 7.2 to create an ECS instance. For more information, see [Create an ECS instance](../intl.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#).
2.  Use the root user to connect to the ECS instance. For more information, see [Connect to a Linux instance by using a password](../intl.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using a password.md#).

## Step 2: Deploy the Node.js environment {#section_tug_p3l_h9l .section}

Deploy the Node.js environment in any of the following ways:

-   Use a binary file to install the Node.js environment

    The installation package used in the deployment is a compiled binary file. After you decompress the package, the node and npm files already exist in the bin folder, so you do not need to recompile the binary file.

    To deploy the Node.js environment by using the binary file, follow these steps:

    1.  Download the Node.js installation package.

        ``` {#codeblock_0o8_a0p_pun}
        wget https://nodejs.org/dist/v6.9.5/node-v6.9.5-linux-x64.tar.xz
        ```

    2.  Decompress the file.

        ``` {#codeblock_m0m_pg8_8wt}
        tar xvf node-v6.9.5-linux-x64.tar.xz
        ```

    3.  After you create a soft link, you can run node and npm commands directly in any directory.

        ``` {#codeblock_16q_41z_hy9}
        ln -s /root/node-v6.9.5-linux-x64/bin/node /usr/local/bin/node
        ln -s /root/node-v6.9.5-linux-x64/bin/npm /usr/local/bin/npm
        ```

    4.  Check the versions of node and npm.

        ``` {#codeblock_et3_yb7_8ad}
        node -v
        npm -v
        ```

        Then, the Node.js environment has been installed. By default, the software is installed in the directory /root/node-v6.9.5-linux-x64/.

    5.  To install the software in another directory such as /opt/node/, run the following commands in sequence:

        ``` {#codeblock_x2z_8or_g8u}
        mkdir -p /opt/node/
        mv /root/node-v6.9.5-linux-x64/* /opt/node/
        rm -f /usr/local/bin/node
        rm -f /usr/local/bin/npm
        ln -s /opt/node/bin/node /usr/local/bin/node
        ln -s /opt/node/bin/npm /usr/local/bin/npm
        ```

-   Use NVM to install multiple versions

    Node Version Manager \(NVM\) is the software used to manage Node.js versions. You can use NVM to easily switch Node.js versions. NVM is suitable for developers that are dedicated to Node.js or that need to efficiently update or switch Node.js versions.

    To install multiple Node.js versions by using NVM, follow these steps:

    1.  Use Git to clone source code to the local directory ~/.nvm, and check the latest update.

        ``` {#codeblock_bj7_a56_9ap}
        yum install git
        git clone https://github.com/cnpm/nvm.git ~/.nvm && cd ~/.nvm && git checkout `git describe --abbrev=0 --tags`
        ```

    2.  Activate NVM.

        ``` {#codeblock_j5u_7na_61m}
        echo ". ~/.nvm/nvm.sh" >> /etc/profile
        source /etc/profile
        ```

    3.  Retrieve a list of all Node.js versions.

        ``` {#codeblock_9u1_0bv_vow}
        nvm list-remote
        ```

    4.  Install multiple Node.js versions.

        ``` {#codeblock_63q_ur0_1s0}
        nvm install v6.9.5
        nvm install v7.4.0
        ```

    5.  Run the `nvm ls` command to check the version of the installed Node.js environment. Node.js v7.4.0 is installed in this example. The response is as follows:

        ``` {#codeblock_nq4_vhh_8fa}
        [root@iZXXXXZ .nvm]# nvm ls
              v6.9.5
        ->       v7.4.0
              system
        stable -> 7.4 (-> v7.4.0) (default)
        unstable -> 6.9 (-> v6.9.5) (default)
        ```

    6.  Run the command `nvm use v7.4.0` to switch to Node.js v7.4.0. The response is as follows:

        ``` {#codeblock_gvw_6im_zax}
        [root@iZXXXXZ .nvm]# nvm use v7.4.0
        Now using node v7.4.0
        ```


## Step 3: Deploy a test project {#section_igz_e58_4zq .section}

To deploy a test project, follow these steps:

1.  Create the example.js project file. 

    ``` {#codeblock_9zl_b7a_mna}
    cd ~
    touch example.js
    ```

2.  Use the vim editor to open the example.js project file. 

    ``` {#codeblock_pms_cvv_uov}
    yum install vim
    vim example.js
    ```

    Press the `i` key to enter the edit mode, and copy the following code to the project file. Afterward, press the Esc key to exit the edit mode. Type `:wq` and press the Enter key to save and close the file.

    The code that you copy to the project file is as follows:

    ``` {#codeblock_isa_tmi_q1x}
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

    **Note:** In this example, you specify Port 3000 as the service port. You can also specify another port in your actual running environment. However, you must add an inbound rule to the security group of the ECS instance to support the specified port.

3.  Run the project. 

    ``` {#codeblock_90o_q0j_lem}
    node ~/example.js &
    ```

4.  Run the following command to check whether the deployed application is listening on the specified port. 

    ``` {#codeblock_9t9_jpx_49t}
    netstat -tpln
    ```

    In this example, the response contains Port 3000, indicating that the application is listening on the port.

5.  Log on to the [ECS console](https://ecs.console.aliyun.com), and add an inbound rule to the security group of the ECS instance to support the specified port, such as Port 3000 in this example. For more information about how to add security group rules, see [Add security group rules](../intl.en-US/Security/Security groups/Add security group rules.md#).
6.  Open your local browser, and in the address bar, enter the URL `http://<Public IP address of the ECS instance>:Port number` to access the project. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9770/156862610712144_en-US.png)


**More information**  


[Alibaba Cloud sandbox platform](https://edu.cloudcare.cn/courses/646394e08b66441ab43f7a5e037a318e/detail)

[Alibaba Cloud Marketplace](https://market.aliyun.com/software)

