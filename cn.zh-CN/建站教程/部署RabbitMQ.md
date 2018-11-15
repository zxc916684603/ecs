# 部署RabbitMQ {#concept_th4_cr1_ffb .concept}

RabbitMQ 是一个开源的 AMQP 实现，服务器端用 Erlang 语言编写，支持多种客户端，如：Python、Ruby、.NET、Java、JMS、C、PHP、ActionScript、XMPP、STOMP 等，支持 AJAX。用于在分布式系统中存储转发消息，在易用性、扩展性、高可用性等方面表现不俗。

## 部署方式 {#section_oth_vs1_ffb .section}

在阿里云服务器下部署 RabbitMQ 提供两种部署方式：

-   [RabbitMQ 镜像部署](https://market.aliyun.com/products/55530001/cmjj017527.html)
-   手动部署（源码编译安装）

一般推荐镜像部署适合新手使用更加快捷方便，安装包部署以及手动部署适合对 Linux 命令有基本了解的用户，可以满足用户个性化部署的要求。本教程主要介绍镜像和手工部署的方式。

## 镜像部署 {#section_hvf_bt1_ffb .section}

1.  单击 [RabbitMQ 环境 \( CentOS7.3 Erlang19.3 \)](https://market.aliyun.com/products/55530001/cmjj017527.html) 进入镜像详情页。
2.  单击 **立即购买**，按提示步骤购买 ECS 实例。
3.  登录 [ECS 管理控制台](https://ecs.console.aliyun.com/#/home)。
4.  在左侧导航栏中，单击 **实例**，进入 ECS 实例列表页。
5.  选择所购 ECS 实例所在的地域，并找到所购 ECS 实例，在 **IP 地址** 列获取该实例的公网 IP 地址。
6.  在浏览器地址栏中输入公网 IP 地址，下载操作文档。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9776/153804707812515_zh-CN.png)

7.  使用 putty 登录 Linux 服务器，请参考 [连接Linux实例](https://help.aliyun.com/document_detail/25425.html)；忘记 root 密码，请参考 [重置实例密码](https://help.aliyun.com/document_detail/25439.html)。
8.  初始化 rabbitmq。

    ```
    cd /root/oneinstack
     ./init_rabbitmq.sh
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9776/153804707812516_zh-CN.png)

9.  进入管理页面，浏览器访问 `http://公网IP:15672`。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9776/153804707812517_zh-CN.png)


## 手工部署 {#section_gr4_zy1_ffb .section}

-   系统平台：CentOS 7.3
-   rabbitmq版本：rabbitmq-server -3.6.9
-   erlang版本：erlang19.3
-   JDK版本：JDK1.8.0\_121

**前提准备**

1.  创建一般用户 rabbitmq，运行 rabbitmq。

    ```
    useradd rabbitmq
    ```

2.  设置 Linux 主机名。

    CentOS 7 修改 /etc/hostname，CentOS 6 修改 /etc/sysconfig/network，下面以 CentOS 7 为例。

    ```
    echo rabbit1 > /etc/hostname
    hostname rabbit1
    exit  #退出重新登录
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9776/153804707812518_zh-CN.png)


**安装依赖包**

```
yum -y install make gcc gcc-c++ m4 ncurses-devel openssl-devel unixODBC-devel
```

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9776/153804707812519_zh-CN.png)

**源代码下载**

-   下载 Erlang：`wget http://erlang.org/download/otp_src_19.3.tar.gz`。
-   下载 rabbitmq：`wget https://www.rabbitmq.com/releases/rabbitmq-server/v3.6.9/rabbitmq-server-generic-unix-3.6.9.tar.xz`

**安装 Erlang**

```
tar xzf otp_src_19.3.tar.gz #解压
cd otp_src_19.3
./configure --prefix=/usr/local/erlang --enable-shared-zlib --with-ssl --enable-threads --enable-smp-support --enable-kernel-poll --enable-hipe --without-javac
make && make install
```

**解压 RabbitMQ**

1.  解压 rabbitmq-server-generic-unix-3.6.9.tar.xz 。

    ```
    tar xvJf rabbitmq-server-generic-unix-3.6.9.tar.xz
    mv rabbitmq_server-3.6.9  /usr/local/rabbitmq
    ```

2.  rabbitmq 环境变量配置。

    ```
    sed -i 's@^ERL_DIR=.*@ERL_DIR=/usr/local/erlang/bin/@' /usr/local/rabbitmq/sbin/rabbitmq-defaults
    sed -i 's@^LOG_BASE=.*@LOG_BASE=/usr/local/rabbitmq/var/log/rabbitmq@' /usr/local/rabbitmq/sbin/rabbitmq-defaults
    mkdir -p /usr/local/rabbitmq/var/{lib，log}/rabbitmq
    ```

3.  一般用户（rabbitmq）运行 RabbitMQ。

    ```
    wget http://pkgs.fedoraproject.org/cgit/rpms/rabbitmq-server.git/plain/rabbitmq-script-wrapper
    sed -i 's@cd /var/lib/rabbitmq@cd /usr/local/rabbitmq/var/lib/rabbitmq@g' rabbitmq-script-wrapper  #更改rabbitmq数据存储目录
    sed -i 's@/usr/lib/rabbitmq/bin/@/usr/local/rabbitmq/sbin/@g' rabbitmq-script-wrapper
    chmod +x rabbitmq-script-wrapper
    cp rabbitmq-script-wrapper /usr/sbin/rabbitmqctl
    cp rabbitmq-script-wrapper /usr/sbin/rabbitmq-server
    cp rabbitmq-script-wrapper /usr/sbin/rabbitmq-plugins
    chown -R rabbitmq.rabbitmq /usr/local/rabbitmq/var
    ```

4.  rabbitmq 日志割接。

    ```
    cat >> /etc/logrotate.d/rabbitmq-server << EOF
    /usr/local/rabbitmq/var/log/rabbitmq/*.log {
    weekly
    missingok
    rotate 20
    compress
    delaycompress
    notifempty
    sharedscripts
    postrotate
     /sbin/service rabbitmq-server rotate-logs > /dev/null
    endscript
    }
    EOF
    ```

5.  rabbitmq 启动脚本。

    ```
    vi /etc/init.d/rabbitmq-server
    #!/bin/sh
    #
    # rabbitmq-server RabbitMQ broker
    #
    # chkconfig: - 80 05
    # description: Enable AMQP service provided by RabbitMQ
    #
    ### BEGIN INIT INFO
    # Provides:          rabbitmq-server
    # Required-Start:    $remote_fs $network
    # Required-Stop:     $remote_fs $network
    # Description:       RabbitMQ broker
    # Short-Description: Enable AMQP service provided by RabbitMQ broker
    ### END INIT INFO
    # Source function library.
    . /etc/init.d/functions
    PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/local/erlang/bin
    NAME=rabbitmq-server
    DAEMON=/usr/sbin/${NAME}
    CONTROL=/usr/sbin/rabbitmqctl
    DESC=rabbitmq-server
    USER=rabbitmq
    ROTATE_SUFFIX=
    INIT_LOG_DIR=/usr/local/rabbitmq/var/log/rabbitmq
    PID_FILE=/var/run/rabbitmq/pid
    START_PROG="daemon"
    LOCK_FILE=/var/lock/subsys/$NAME
    test -x $DAEMON || exit 0
    test -x $CONTROL || exit 0
    RETVAL=0
    set -e
    [ -f /etc/default/${NAME} ] && . /etc/default/${NAME}
    [ -f /etc/sysconfig/${NAME} ] && . /etc/sysconfig/${NAME}
    ensure_pid_dir () {
     PID_DIR=`dirname ${PID_FILE}`
     if [ ! -d ${PID_DIR} ] ; then
         mkdir -p ${PID_DIR}
         chown -R ${USER}:${USER} ${PID_DIR}
         chmod 755 ${PID_DIR}
     fi
    }
    remove_pid () {
     rm -f ${PID_FILE}
     rmdir `dirname ${PID_FILE}` || :
    }
    start_rabbitmq () {
     status_rabbitmq quiet
     if [ $RETVAL = 0 ] ; then
         echo RabbitMQ is currently running
     else
         RETVAL=0
         # RABBIT_NOFILES_LIMIT from /etc/sysconfig/rabbitmq-server is not handled
         # automatically
         if [ "$RABBITMQ_NOFILES_LIMIT" ]; then
                 ulimit -n $RABBITMQ_NOFILES_LIMIT
         fi
         ensure_pid_dir
         set +e
         RABBITMQ_PID_FILE=$PID_FILE $START_PROG $DAEMON \
             > "${INIT_LOG_DIR}/startup_log" \
             2> "${INIT_LOG_DIR}/startup_err" \
             0<&- &
         $CONTROL wait $PID_FILE >/dev/null 2>&1
         RETVAL=$?
         set -e
         case "$RETVAL" in
             0)
                 echo SUCCESS
                 if [ -n "$LOCK_FILE" ] ; then
                     touch $LOCK_FILE
                 fi
                 ;;
             *)
                 remove_pid
                 echo FAILED - check ${INIT_LOG_DIR}/startup_\{log， _err\}
                 RETVAL=1
                 ;;
         esac
     fi
    }
    stop_rabbitmq () {
     status_rabbitmq quiet
     if [ $RETVAL = 0 ] ; then
         set +e
         $CONTROL stop ${PID_FILE} > ${INIT_LOG_DIR}/shutdown_log 2> ${INIT_LOG_DIR}/shutdown_err
         RETVAL=$?
         set -e
         if [ $RETVAL = 0 ] ; then
             remove_pid
             if [ -n "$LOCK_FILE" ] ; then
                 rm -f $LOCK_FILE
             fi
         else
             echo FAILED - check ${INIT_LOG_DIR}/shutdown_log， _err
         fi
     else
         echo RabbitMQ is not running
         RETVAL=0
     fi
    }
    status_rabbitmq() {
     set +e
     if [ "$1" != "quiet" ] ; then
         $CONTROL status 2>&1
     else
         $CONTROL status > /dev/null 2>&1
     fi
     if [ $? != 0 ] ; then
         RETVAL=3
     fi
     set -e
    }
    rotate_logs_rabbitmq() {
     set +e
     $CONTROL rotate_logs ${ROTATE_SUFFIX}
     if [ $? != 0 ] ; then
         RETVAL=1
     fi
     set -e
    }
    restart_running_rabbitmq () {
     status_rabbitmq quiet
     if [ $RETVAL = 0 ] ; then
         restart_rabbitmq
     else
         echo RabbitMQ is not runnning
         RETVAL=0
     fi
    }
    restart_rabbitmq() {
     stop_rabbitmq
     start_rabbitmq
    }
    case "$1" in
     start)
         echo -n "Starting $DESC: "
         start_rabbitmq
         echo "$NAME."
         ;;
     stop)
         echo -n "Stopping $DESC: "
         stop_rabbitmq
         echo "$NAME."
         ;;
     status)
         status_rabbitmq
         ;;
     rotate-logs)
         echo -n "Rotating log files for $DESC: "
         rotate_logs_rabbitmq
         ;;
     force-reload|reload|restart)
         echo -n "Restarting $DESC: "
         restart_rabbitmq
         echo "$NAME."
         ;;
     try-restart)
         echo -n "Restarting $DESC: "
         restart_running_rabbitmq
         echo "$NAME."
         ;;
     *)
         echo "Usage: $0 {start|stop|status|rotate-logs|restart|condrestart|try-restart|reload|force-reload}" >&2
         RETVAL=1
         ;;
    esac
    exit $RETVAL
    ```

    保存后，添加执行权限，并设置自启动。

    ```
    chmod +x /etc/init.d/rabbitmq-server
    chkconfig --add rabbitmq-server
    chkconfig rabbitmq-server on
    ```

6.  修改 rabbitmq.config。

    特别注意默认用户名密码，请自行修改 default\_user，default\_pass，loopback\_users。

    ```
    cat > /usr/local/rabbitmq/etc/rabbitmq/rabbitmq.config << EOF
    [
    {rabbit， [
     {tcp_listeners，[{"0.0.0.0"，5672}]}，
     {tcp_listen_options， [binary， {packet，raw}，
                                   {reuseaddr，true}，
                                   {backlog，128}，
                                   {nodelay，true}，
                                   {exit_on_close，false}，
                                   {keepalive，true}]}，
     {default_vhost，       <<"/">>}，
     {default_user，        <<"guest">>}，
     {default_pass，        <<"guest">>}，
     {loopback_users， ["guest"]}，
     {default_permissions， [<<".*">>， <<".*">>， <<".*">>]}
    ]}
    ].
    EOF
    ```

7.  开启 rabbitmq manager。

    ```
    cat > /usr/local/rabbitmq/etc/rabbitmq/enabled_plugins << EOF
    [rabbitmq_management].
    EOF
    ```

8.  启动 rabbitmq。

    ```
    service rabbitmq-server start
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9776/153804707812520_zh-CN.png)

9.  进入管理页面。

    浏览器访问 [http://公网IP:15672。](http://xn--ip-xz4cq45o:15672%E3%80%82/)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9776/153804707812521_zh-CN.png)


更多开源软件尽在云市场：[https://market.aliyun.com/software](https://market.aliyun.com/software) 。

