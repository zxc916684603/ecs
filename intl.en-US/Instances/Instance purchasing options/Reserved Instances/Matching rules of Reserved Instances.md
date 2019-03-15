# Matching rules of Reserved Instances {#concept_af1_zxq_dgb .concept}

Reserved Instances \(RIs\) provide a billing benefit only when they match Pay-As-You-Go instances. This topic describes the matching rules of RIs and provides some examples.

## Matching rules of RIs {#section_pqc_yyq_dgb .section}

The matching status between an RI and a Pay-As-You-Go instance cannot be manually managed. After you purchase an RI, the RI automatically matches one or more Pay-As-You-Go instances that have certain attributes within its term. The matching elements include operating system, instance type, and scope.

If you do not have any Pay-As-You-Go instances under your account, the RI will be idle. After you purchase one or more applicable Pay-As-You-Go instances, the RI will automatically match with the instances immediately.

**Note:** After you purchase an RI, you pay for the entire term regardless of whether the RI matches a Pay-As-You-Go instance. For more information, see [Reserved Instance billing](reseller.en-US/Pricing/Reserved Instance billing.md#).

The following table describes the features of regional RIs and zonal RIs.

|Feature|Regional RI|Zonal RI|Example|
|-------|-----------|--------|-------|
|Instance size flexibility|Supported. A regional RI can match different sizes of Pay-As-You-Go instances that are of the same instance type family.|Not supported. A zonal RI must match one or more Pay-As-You-Go instances of a specified size.|You have the following running Pay-As-You-Go instances:Two ecs.c5.xlarge Linux instances in China \(Qingdao\). The instance names are C5PAYG-1 and C5PAYG-2 respectively.

You purchase the following RI:

One regional ecs.c5.2xlarge RI in China \(Qingdao\). The RI name is C5RI.

After the purchase, C5RI matches C5PAYG1 and C5PAYG2 simultaneously to provide a billing discount.|
|Zone flexibility|Supported. A regional RI can match all Pay-As-You-Go instances in the same region.|Not supported. A zonal RI must match one or more Pay-As-You-Go instances in a specified zone.|You have the following running Pay-As-You-Go instance:One ecs.c5.xlarge Linux instance in zone B, China \(Qingdao\). The instance name is C5PAYG-b.

You purchase the following RI:

One regional ecs.c5.xlarge RI in China \(Qingdao\). The RI name is C5RI.

After the purchase, C5RI matches C5PAYG-b to provide a billing discount.You release C5PAYG-b, and then start another Linux instance named C5PAYG-c, which is of the same instance type as C5PAYG-b, in zone C. C5RI then matches C5PAYG-c to provide the same billing discount.

|
|Resource Reservation|Not supported. If there is a shortage of available instances, you may need to wait for instances to become available.|Supported. A specified number of Pay-As-You-Go instances are reserved so that these instances can be created successfully.|You purchase the following RIs:Five zonal ecs.c5.xlarge RIs in China \(Qingdao\). The term is 1 year and the instance count is 2.

Ten ecs.c5.xlarge instances will be reserved in zone B, China \(Qingdao\) for one year.|

## RI matching example {#section_dhb_rcw_fgb .section}

In this example, you have a Pay-As-You-Go instance, a regional RI, and a zonal RI. You then purchase another two Pay-As-You-Go instances.

You have the following Pay-As-You-Go instance:

-   One ecs.g5.2xlarge Linux instance in zone B, China \(Qingdao\). The instance name is G5PAYG-b.

You purchase the following RIs:

-   One regional ecs.g5.xlarge RI in China \(Qingdao\). The term is 1 year and the instance count is 1. The RI name is G5RI.
-   One zonal ecs.c5.xlarge RI in zone C, China \(Qingdao\). The term is 3 years and the instance count is 2. The RI name is C5RI-c.

After the purchase, G5RI and C5RI-c immediately calculate the term, and are billed regardless of whether they match any running Pay-As-You-Go instances.

G5RI can be applied to Pay-As-You-Go instances of different sizes or in different zones. It successfully matches G5PAYG-b, and the billing discount is immediately applied to G5PAYG-b on an hourly basis. However, G5RI cannot provide enough computing power. Therefore, the billing discount can be applied to only 50% of the hours for which G5PAYG-b is used.

C5RI-c does not match any running Pay-As-You-Go instances and remains in an idle state. However, it supports resource reservation, so two ecs.c5.xlarge instances are reserved in zone C, China \(Qingdao\).

Next, you purchase the following Pay-As-You-Go instances:

-   One ecs.c5.xlarge Linux instance in zone C, China \(Qingdao\). The instance name is C5PAYG-c.
-   One ecs.c5.xlarge Linux instance in zone B, China \(Qingdao\). The instance name is C5PAYG-b.

After the purchase, C5RI-c and C5PAYG-c match successfully, and the billing benefit is immediately applied to C5PAYG-c. However, C5PAYG-b and C5RI-c do not match in the zone attribute. Therefore, C5PAYG-b cannot benefit from the billing discount.

After the 1-year term expires, G5RI becomes invalid. G5PAYG-b can still run normally, but cannot benefit from the billing discount. After the 3-year term expires, C5RI-c becomes invalid, and C5PAYG-c is billed at the Pay-As-You-Go rate. C5PAYG-b does not match any RIs and is always billed at the Pay-A-You-Go rate.

**Note:** After your instances return to being charged by the Pay-As-You-Go rate, you must make sure that the account associated with the instances has sufficient funds for the bill. Otherwise, your Pay-As-You-Go instances cannot run normally.

We recommend that you purchase RIs that can match your Pay-As-You-Go instances according to your service scenarios. RIs can be flexibly managed to meet dynamic service scenarios. This allows you to change your RIs according to your specific service scenarios so that you can benefit from billing discounts.

