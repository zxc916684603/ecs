# Increase data throughput through read/write split {#concept_bp5_qw5_hfb .concept}

System performance decreases when reads and writes occur in the same database server. To improve overall system performance and optimize user experience, you can reduce the load of your primary database through read/write split. This topic describes how to split read operations and write operations at the application layer and at the system layer.

## Split read and write at the application layer {#section_ndg_sw5_hfb .section}

At the application layer, read/write split is implemented through coding. Before the Service method is called, AOP is used to decide whether to use the read database or the write database. The method names can be used to implement the target action. For example, the read database is used for method names starting with “query”, “find” or “get”, and the write database is used for others.

**Advantages**

1. The program easily switches between multiple data sources automatically.

2. Middleware is not required.

3. Currently, any databases are supported.

**Disadvantages**

1. Manual operations are not supported.

2. Data sources cannot be added dynamically.

## Split read and write at the system layer {#section_qdg_sw5_hfb .section}

The following procedure describes how to implement read/write split by using MySQL Proxy.

## MySQL Proxy overview {#section_rdg_sw5_hfb .section}

MySQL Proxy is a simple program that is situated between your client and MySQL server and that can monitor, analyze, or transform their communication. Its flexibility allows for a wide variety of uses, including load balancing, failover, query analysis, and query filtering and modification.

**MySQL Proxy Principle**

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9808/155055326113249_en-US.png)

MySQL Proxy is an intermediate-layer proxy that acts as a connection pool to forward connection requests from the front-end application to the back-end database. By using the lua script, MySQL Proxy can perform complex connection control and filtering to implement read/write split and load balancing. MySQL Proxy is transparent to the application, which only needs to be connected to the listening port of MySQL Proxy. In this case, the proxy server may be considered as a Single Point of Failure \(SPOF\), but the use of multiple proxy servers implements redundancy. Therefore, you only need to configure multiple proxy connections in the connection pool of the application server.

Advantages:

-   Read/write split can be implemented without modifying the source program.

-   Data sources can be added dynamically without restarting the program.


Disadvantages:

-   The program relies on the middleware, making it difficult to switch databases.

-   Performance decreases because the middleware serves as a forwarding proxy.


## Procedure {#section_udg_sw5_hfb .section}

**Environment:**

-   Master database IP address: 121.40.18.26

-   Slave database IP address: 101.37.36.20

-   MySQL Proxy IP address: 116.62.101.76


**Preparations:**

-   1. Create three ECS instances and install MySQL.

-   2. Build master/slave databases and ensure data consistency.


**Primary environment**

1. Modify the MySQL configuration file.

```
vim /etc/my.cnf
[mysqld]
server-id=202                  # Set the unique ID of the server. The default ID is 1.
log-bin=mysql-bin              # Enable binary logs.
```

**Secondary environment**

```
[mysqld]
server-id=203
```

2. Restart the MySQL service on the master/slave servers.

```
/etc/init.d/mysqld restart
```

3. Create an account on the master server and grant permissions to the slave server.

```
mysql -uroot -p95c7586783
grant replication slave on *.* to 'syncms'@'Enter slave-IP' identified by '123456';
flush privileges;
```

4. View the primary database status.

```
mysql> show master status;
```

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9808/155055326113250_en-US.png)

5. Configure the secondary database.

```
change master to master_host='Enter master-IP', master_user='syncms',      master_password='123456', master_log_file='mysql-bin. 000005', master_log_pos=602;
```

6. Start the slave synchronization process and view the status.

```
start slave;
show slave status\G
```

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9808/155055326113251_en-US.png)

7. Verify master/slave synchronization.

**Operations on the primary database:**

```
mysql> create database testproxy;
mysql> create table testproxy.test1(ID int primary key,name char(10) not null);
mysql> insert into testproxy.test1 values(1,'one');
mysql> insert into testproxy.test1 values(2,'two');
mysql> select * from testproxy.test1;
```

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9808/155055326113252_en-US.png)

**Operations on the secondary database:**

Search the secondary database for the data of the testproxy.test1 table. If the data matches that in the primary database, master/slave synchronization is successful.

```
select * from testproxy.test1;
```

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9808/155055326113253_en-US.png)

## Configure read/write split {#section_o2g_sw5_hfb .section}

1. Install MySQL Proxy.

```
wget https://cdn.mysql.com/archives/mysql-proxy/mysql-proxy-0.8.5-linux-glibc2.3-x86-64bit.tar.gz
mkdir /alidata
tar xvf mysql-proxy-0.8.5-linux-glibc2.3-x86-64bit.tar.gz 
mv mysql-proxy-0.8.5-linux-glibc2.3-x86-64bit/  /alidata/mysql-proxy-0.8.5
```

2. Set environment variables.

```
vim /etc/profile                     # Add the following  information:
PATH=$PATH:/alidata/mysql-proxy-0.8.5/bin
export $PATH
source /etc/profile                  # Validate the environment variables.
mysql-proxy -V
```

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9808/155055326113254_en-US.png)

3. Set the read-write split parameters.

```
cd /alidata/mysql-proxy-0.8.5/share/doc/mysql-proxy/
vim  rw-splitting.lua
```

MySQL Proxy will detect client connections. If the number of connections does not exceed the preset value of min\_idle\_connections, read/write split will not be performed. By default, read/write split will be performed for at least four connections and at most eight connections. To simplify testing read/write split, the number of connections is modified to one at least and two at most, and can be adjusted in real application environments based on your specific needs.

Before the modification

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9808/155055326113255_en-US.png)

After the modification

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9808/155055326113256_en-US.png)

4. Copy the lua administration script \(admin.lua\) to the directory where the read-write split script \(rw-splitting.lua\) is located.

```
cp /alidata/mysql-proxy-0.8.5/lib/mysql-proxy/lua/admin.lua /alidata/mysql-proxy-0.8.5/share/doc/mysql-proxy/
```

## Grant permissions {#section_x2g_sw5_hfb .section}

1. Grant permissions in the master database. The permissions will also be granted in the slave database due to master/slave synchronization.

```
mysql -uroot -p95c7586783
grant all on *.* to 'mysql-proxy'@'Enter MySQL Proxy IP' identified by '123456';
flush privileges;
```

2. Start MySQL Proxy.

```
mysql-proxy --daemon --log-level=debug --log-file=/var/log/mysql-proxy.log --plugins=proxy -b Enter master-IP:3306 -r Enter slave-IP:3306 --proxy-lua-script="/alidata/mysql-proxy-0.8.5/share/doc/mysql-proxy/rw-splitting.lua" --plugins=admin --admin-username="admin" --admin-password="admin" --admin-lua-script="/alidata/mysql-proxy-0.8.5/share/doc/mysql-proxy/admin.lua"
```

3. View the port and relevant processes.

```
netstat -tpln
```

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9808/155055326213257_en-US.png)

```
ps -ef | grep mysql
```

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9808/155055326213258_en-US.png)

## Test read/write split {#section_ffg_sw5_hfb .section}

1. Disable slave replication.

```
stop slave;
```

2. Log on to the back end of MySQL Proxy.

```
mysql  -u  admin -padmin -P 4041 -h MySQL-Proxy-IP
select * from backends;                # View the status.
```

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9808/155055326213259_en-US.png)

The first connection will access the master database.

```
mysql -umysql-proxy -p123456 -h 116.62.101.76 -P 4040
insert into testproxy.test1 values(3,'three');             # Add a data record. Slave replication is disabled. Therefore, the record exists in the primary database but does not exist in the secondary database.
```

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9808/155055326213260_en-US.png)

Create additional test connections. If the data displayed in the testproxy.test1 table is the same as that in the secondary database, read/write split is successful.

```
mysql -umysql-proxy -p123456 -h 116.62.101.76 -P 4040
select * from testproxy.test1;
```

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9808/155055326213261_en-US.png)

