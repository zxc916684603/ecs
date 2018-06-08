# Change configurations of Pay-As-You-Go instances {#concept_fzw_gbf_5db .concept}

If you find that the instance specifications exceed or are insufficient for your application requirements, you can change the instance type, that is, the specification of the memory and the CPU.  Different operations are allowed based on the billing method of an instance: Note: You must stop your instance to change the instance type, 

**Note:** which may lead to interruptions in your service.  We recommend that you perform this operation during non-peak hours.

## Limits {#section_hxl_fc2_xdb .section}

Pay-As-You-Go instances are subject to the following limits for configuration change:

-   The interval between two configuration change operations must be more than five minutes.
-   You cannot change the instance type across instance generations. For example, instance types of Generation I are not allowed to be changed to those of Generation II or Generation III.
-   For instance types of Generation III, you cannot change the configuration within or between the following instance type families:
    -   GPU-based instance type families, including gn5 and gn4.
    -   FPGA-based instance type families, including f1.
    -   Big data instance type families, including d1 and d1ne.
    -   Local SSD instance type families, including i1 and i2.
-   For instance types of Generation III, you can change the instance types according to the following table.

    |Instance type families|ecs.sn1ne|ecs.sn2ne|ecs.mn4|ecs.se1ne|ecs.cm4|ecs.c4|ecs.se1|ecs.ce4|ecs.xn4|ecs.e4|ecs.n4|
    |----------------------|---------|---------|-------|---------|-------|------|-------|-------|-------|------|------|
    |ecs.sn1ne|Y|Y|—|Y|Y|Y|Y|Y|—|—|—|
    |ecs.sn2ne|Y|Y|—|Y|Y|Y|Y|Y|—|—|—|
    |ecs.mn4|—|—|Y|—|—|—|—|—|Y|Y|Y|
    |ecs.se1ne|Y|Y|—|Y|Y|Y|Y|Y|—|—|-|
    |ecs.cm4|Y|Y|—|Y|Y|Y|Y|Y|—|—|—|
    |ecs.c4|Y|Y|—|Y|Y|Y|Y|Y|—|—|—|
    |ecs.se1|Y|Y|—|Y|Y|Y|Y|Y|—|—|—|
    |ecs.ce4|Y|Y|—|Y|Y|Y|Y|Y|-|—|—|
    |ecs.xn4|—|—|Y|—|—|—|—|—|Y|Y|Y|
    |ecs.e4|-|—|Y|—|—|—|—|—|Y|Y|Y|
    |ecs.n4|—|—|Y|—|—|—|—|—|Y|Y|Y|

-   For instance types of Generation II, you can change the instance type according to the following table.

    |Instance type families|ecs.n2|ecs.e3|ecs.n1|ecs.sn2|ecs.sn1|
    |----------------------|------|------|------|-------|-------|
    |ecs.n2|Y|Y|Y|—|—|
    |ecs.e3|Y|Y|Y|—|—|
    |ecs.n1|Y|Y|Y|—|—|
    |ecs.sn2|—|—|—|Y|Y|
    |ecs.sn1|—|—|—|Y|Y|

-   You can change the configuration of all instance types within Generation I.

**Note:** In the preceding table, “Y” indicates that you can change the configuration between the instance type families, and “-“ indicates that you are not allowed to change the configuration between the instance type families.

## Prerequisites {#section_jyl_fc2_xdb .section}

You must stop the instance.

## Procedure {#section_kyl_fc2_xdb .section}

To change the memory and vCPU configurations of a Pay-As-You-Go instance, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Find the Pay-As-You-Go instance you want to change the configuration, and in the **Actions** column, click  **Change Instance Type**.
5.  In the Change Instance Type dialog box, select an instance type and click OK. **OK**.

    **Note:** You can enter the instance type information in the search box to filter instance types in real time.


The change is immediately effective after you complete the operation.  You can view the instance type information  in the **Basic Information** area of  the Instance Details page.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9644/5424_en-US.png)

Then, start the instance to provide services again.

