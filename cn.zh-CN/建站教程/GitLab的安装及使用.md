# GitLab的安装及使用 {#concept_myh_s5s_2fb .concept}

## 前言 {#section_hjs_55s_2fb .section}

GitLab是利用 Ruby on Rails 一个开源的版本管理系统，实现一个自托管的Git项目仓库，可通过Web界面进行访问公开的或者私人项目。

它拥有与Github类似的功能，能够浏览源代码，管理缺陷和注释。可以管理团队对仓库的访问，它非常易于浏览提交过的版本并提供一个文件历史库。

团队成员可以利用内置的简单聊天程序\(Wall\)进行交流。

它还提供一个代码片段收集功能可以轻松实现代码复用，便于日后有需要的时候进行查找。

**Git的家族成员**

Git：是一种版本控制系统，是一个命令，是一种工具。

Gitlib：是用于实现Git功能的开发库。

Github：是一个基于Git实现的在线代码托管仓库，包含一个网站界面，向互联网开放。

GitLab：是一个基于Git实现的在线代码仓库托管软件，你可以用gitlab自己搭建一个类似于Github一样的系统，一般用于在企业、学校等内部网络搭建git私服。

**Gitlab的服务构成**

Nginx：静态web服务器。

gitlab-shell：用于处理Git命令和修改authorized keys列表。

gitlab-workhorse:轻量级的反向代理服务器。

logrotate：日志文件管理工具。

postgresql：数据库。

redis：缓存数据库。

sidekiq：用于在后台执行队列任务（异步执行）。

unicorn：An HTTP server for Rack applications，GitLab Rails应用是托管在这个服务器上面的。

**GitLab工作流程**

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443812255_zh-CN.png)

**GitLab Shell**

GitLab Shell有两个作用：为GitLab处理Git命令、修改authorized keys列表。

当通过SSH访问GitLab Server时，GitLab Shell会：

限制执行预定义好的Git命令（git push, git pull, git annex）

调用GitLab Rails API 检查权限

执行pre-receive钩子（在GitLab企业版中叫做Git钩子）

执行你请求的动作 处理GitLab的post-receive动作

处理自定义的post-receive动作

当通过http\(s\)访问GitLab Server时，工作流程取决于你是从Git仓库拉取\(pull\)代码还是向git仓库推送\(push\)代码。

如果你是从Git仓库拉取\(pull\)代码，GitLab Rails应用会全权负责处理用户鉴权和执行Git命令的工作；

如果你是向Git仓库推送\(push\)代码，GitLab Rails应用既不会进行用户鉴权也不会执行Git命令，它会把以下工作交由GitLab Shell进行处理：

```
调用GitLab Rails API 检查权限
执行pre-receive钩子（在GitLab企业版中叫做Git钩子）
执行你请求的动作
处理GitLab的post-receive动作
处理自定义的post-receive动作
```

**GitLab Workhorse**

GitLab Workhorse是一个敏捷的反向代理。它会处理一些大的HTTP请求，比如文件上传、文件下载、Git push/pull和Git包下载。其它请求会反向代理到GitLab Rails应用，即反向代理给后端的unicorn。

## Gitlab环境部署 {#section_lbj_kws_2fb .section}

ECS配置要求：内存2G以上

**方法一：镜像部署**

镜像名称：[GitLab代码管理（Centos 64位 | GitLab）](https://market.aliyun.com/products/55530001/jxsc000067.html?spm=5176.730005.0.0.LuTu) | [镜像帮助文档](http://zy-res.oss-cn-hangzhou.aliyuncs.com/aliyun_Market_files/gitlab%E4%BB%A3%E7%A0%81%E7%AE%A1%E7%90%86%EF%BC%88centos%2064%E4%BD%8D%20%20gitlab%EF%BC%89.pdf?spm=5176.730006-jxsc000067.102.9.J5BUL1&file=gitlab%E4%BB%A3%E7%A0%81%E7%AE%A1%E7%90%86%EF%BC%88centos%2064%E4%BD%8D%20%20gitlab%EF%BC%89.pdf)

进入镜像详情页面，单击 **立即购买**，按提示步骤购买 ECS 实例。

购买完成之后，登录ECS 管理控制台，在左边导航栏里，单击 **实例**，进入 ECS 实例列表页,选择所购 ECS 实例所在的地域，并找到所购 ECS 实例，在 **IP 地址** 列获取该实例的公网 IP 地址。

**说明：** 镜像部署好后默认是禁止远端访问的，所以直接访问ECS服务器的公网IP是不能访问到GitLab的登录界面的，请先运行/alidata目录下的gitlab\_opennet.sh脚本，开启远程访问，然后再通过浏览器访问公网IP来访问GitLab的主页。

**方法二：手动部署**

1.  配置yum源。

    ```
    vim /etc/yum.repos.d/gitlab-ce.repo
    ```

    复制以下内容：

    ```
    [gitlab-ce]
    name=gitlab-ce
    baseurl=http://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/yum/el6
    Repo_gpgcheck=0
    Enabled=1
    Gpgkey=https://packages.gitlab.com/gpg.key
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443812256_zh-CN.png)

2.  更新本地yum缓存。

    ```
    sudo yum makecache
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443812257_zh-CN.png)

3.  安装GitLab社区版。

    ```
    sudo yum install gitlab-ce        #自动安装最新版
    sudo yum install gitlab-ce-x.x.x    #安装指定版本
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443812258_zh-CN.png)

    GitLab常用命令：

    ```
    sudo gitlab-ctl start    # 启动所有 gitlab 组件；
    sudo gitlab-ctl stop        # 停止所有 gitlab 组件；
    sudo gitlab-ctl restart        # 重启所有 gitlab 组件；
    sudo gitlab-ctl status        # 查看服务状态；
    sudo gitlab-ctl reconfigure        # 启动服务；
    sudo vim /etc/gitlab/gitlab.rb        # 修改默认的配置文件；
    gitlab-rake gitlab:check SANITIZE=true --trace    # 检查gitlab；
    sudo gitlab-ctl tail        # 查看日志；
    ```


## GitLab使用 {#section_hmj_gxs_2fb .section}

**登录GitLab**

1.  在浏览器的地址栏中输入ECS服务器的公网IP即可登录GitLab的界面，第一次登录使用的用户名和密码为 root 和 5iveL!fe。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443812259_zh-CN.png)

2.  首次登录会强制用户修改密码。密码修改成功后，输入新密码进行登录。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443812260_zh-CN.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443812261_zh-CN.png)


**创建Project**

1.  安装Git工具linux：安装Git，使用自带的源安装。

    ```
    yum install git
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443812262_zh-CN.png)

2.  生成密钥文件。

    使用ssh-keygen生成密钥文件.ssh/id\_rsa.pub。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443812263_zh-CN.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443812264_zh-CN.png)

3.  在GitLab的主页中新建一个Project。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443912265_zh-CN.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443912274_zh-CN.png)

4.  添加ssh key导入步骤2中生成的密钥文件内容：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443912266_zh-CN.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443912275_zh-CN.png)

    ssh key添加完成：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443912267_zh-CN.png)

    项目地址，该地址在进行clone操作时需要用到：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443912268_zh-CN.png)


**简单配置**

1.  配置使用Git仓库的人员姓名。

    ```
    git config --global user.name "上海驻云" 
    ```

2.  配置使用Git仓库的人员email，填写自己的公司邮箱。

    ```
    git config --global user.email "support@jiagouyun.com" 
    ```

3.  克隆项目，在本地生成同名目录，并且目录中会有所有的项目文件。

    ```
    git clone git@iZbp1h7fx16gkr9u4gk8v3Z:root/test.git
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443912269_zh-CN.png)


**上传文件**

1.  进入到项目目录。

    ```
    cd test/ 
    ```

2.  创建需要上传到GitLab中的目标文件。

    ```
    echo “test” > /root/test.sh
    ```

3.  将目标文件或者目录拷贝到项目目录下。

    ```
    cp /root/test.sh ./ 
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443912270_zh-CN.png)

4.  将test.sh文件加入到索引中。

    ```
    git add test.sh
    ```

5.  将test.sh提交到本地仓库。

    ```
    git commit -m “test.sh”
    ```

6.  将文件同步到GitLab服务器上。

    ```
    git push -u origin master
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443912271_zh-CN.png)

7.  在网页中查看上传的test.sh文件已经同步到GitLab中。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9777/153804443912272_zh-CN.png)


## 相关链接 {#section_rqd_4zs_2fb .section}

更多开源软件尽在云市场：[https://market.aliyun.com/software](https://market.aliyun.com/software)

