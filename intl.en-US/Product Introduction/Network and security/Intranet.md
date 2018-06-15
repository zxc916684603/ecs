# Intranet {#concept_qrd_2z2_5db .concept}

Currently, Alibaba Cloud servers communicate over intranet. They use a gigabit of shared bandwidth for non I/O optimized instances, and 10 gigabits of shared bandwidth for I/O optimized instances, with no special restrictions. However, because this is a shared network, the bandwidth may fluctuate.

If you have to transmit data between two ECS instances in the same region, use an intranet connection. Intranet connections can also be used to connect RDS, Server Load Balancer, and OSS. The Internet speed of these products is based on a gigabit shared bandwidth environment. These products can be connected with each other through the internal connection.

Now, you can also use a direct intranet connection to link RDS, Server Load Balancer, and OSS with ECS instances in the same region.

The network types, owners, regions, and security groups have effect on

-   the intranet communication of ECS instances. See the following table for details.

    |Network type|Owners|Regions|Security groups|How to enable intranet communication|
    |:-----------|:-----|:------|:--------------|:-----------------------------------|
    |VPC, same VPC|One account or different accounts|Same|Same|Enabled by default.|
    |Different|Authorize security groups for each other.|
    |VPC, different VPCs|One account or different accounts|Same|Either same or different|Use Express Connect. For more information, see Application scenarios from Product Introduction to Express Connect.|
    |Different|Different|
    |Classic|One account|Same|Same|Enabled by default.|
    |Different accounts|Either same or different|Authorize security groups for each other. For more information, see Scenarios of security groups.|

-   You can [change the private IP address](../intl.en-US/User Guide/Instances/Change IP addresses/Change the private IP of an ECS instance.md#) of a VPC-Connected ECS instance. You cannot change the private IP address of an instance of the Classic network type,

-   Private and public addresses of ECS instances do not support virtual IP \(VIP\) configuration.

-   By default, instances of different network types cannot communicate with one another in one intranet. VPC provides the ClassicLink function, which allows you to link an ECS instance in the classic network to cloud resources in a VPC through the intranet.


