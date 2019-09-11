# Scenarios {#concept_j5s_nwq_ydb .concept}

ECS is a highly flexible solution that can be used independently as a simple web server or an application server, or used with other Alibaba Cloud products to deliver advanced solutions.

**Note:** Typical scenarios of ECS are included but not limited to the applications described in this topic.

## Official websites and simple web applications {#section_ur2_4wq_ydb .section}

A new website has low traffic and requires only low-configuration ECS instances to run applications, databases, storage files, and other resources. As your business expands, you can upgrade the ECS configuration or add ECS instances at any time without worrying about resource insufficiency during peak traffic.

## Multimedia and high-traffic apps or websites {#section_vr2_4wq_ydb .section}

ECS can be used with [OSS](OSS../../SP_21/DNOSS11893958/EN-US_TP_4313.dita#concept_ybr_fg1_tdb) to store static images, videos, and downloaded packages, reducing the storage fees. In addition, it can work with [CDN](CDN../../SP_19/DNCDN11857410/EN-US_TP_5098.dita#concept_aml_tlg_tdb) and [Load Balancer](../../SP_23/DNSLB11825295/EN-US_TP_4091.dita#concept_whs_lp4_tdb) to significantly reduce your waiting time, cut down public bandwidth costs, and improve service availability.

## Databases with high I/O requirements {#section_aii_l2e_61t .section}

ECS supports databases with high I/O requirements, such as OLTP and NoSQL databases. A high-configuration I/O-optimized ECS instance can be used with the [ESSD cloud disk](../../../../reseller.en-US/Block Storage/Block storage/ESSD cloud disk.md#) to achieve high level of I/O concurrency with higher data reliability. Alternatively, multiple lower-configuration I/O-optimized ECS instances can be used with Server Load Balancer \(SLB\) to deliver a high availability architecture.

## Apps and websites with sharp traffic fluctuations {#section_qfw_nmv_0ty .section}

Some applications may experience sharp traffic fluctuations within a short period. When ECS is used with [Auto Scaling](Auto Scaling../../SP_9/DNess1897847/EN-US_TP_40535.dita#concept_25857_zh), the number of ECS instances is automatically adjusted based on traffic. This way, you can meet the changing resource requirements at a low cost. ECS can also work with SLB to deliver a high availability architecture.

## Big data and real-time online and offline analysis {#section_ubl_qye_8zt .section}

ECS allows you to use [big data instance type families](big data instance type families../DNECS19100341/EN-US_TP_130449.dita#concept_wsn_pcz_wgb) to support Hadoop distributed computing, log processing, and large data warehouses. By adopting the local storage architecture, the big data instance type families can deliver better network performance for Hadoop and Spark clusters while providing abundant storage space with higher storage performance.

## AI applications {#section_dbn_qc0_32x .section}

ECS allows you to use [compute optimized and GPU-equipped instance type families](compute optimized and GPU-equipped instance type families../DNECS19100341/EN-US_TP_130452.dita#concept_fgq_sdz_wgb) to build AI applications with TensorFlow. Such instance type families have lower requirements on the computing capacity of clients and are suitable for image processing, and real-time online rendering for cloud gaming and AR/VR applications.

