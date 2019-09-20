# ECS instance FAQ {#concept_gqy_fyx_wgb .concept}

This topic provides answers to frequently asked questions \(FAQ\) about ECS instances.

-   FAQ about purchasing instances
    -   [How do I check whether instances are available for sale in a specified region or zone?](#section_dxe_iha_q0o)
    -   [What can I do if no resources are available when I create an ECS instance?](#section_lxw_bwz_qgb)
    -   [How do I select an ECS instance that is suitable for my business?](#section_j8t_fwz_mjf)
    -   [How long does it take to create an ECS instance?](#section_ska_yf3_rvx)
    -   [I already paid for an ECS instance but no ECS instance was created. Why?](#section_gbw_acs_xwn)
-   FAQ about enterprise-level instances
    -   [What are enterprise-level instances? What are entry-level instances?](#section_2p8_osd_e5y)
    -   [What are the differences between enterprise-level and entry-level instances?](#section_cm4_dks_zu1)
    -   [Which instance families are enterprise-level instances? Which instance families are entry-level instances?](#section_y0w_qjj_s3o)
    -   [In what business scenarios do I need to purchase enterprise-level instances?](#section_8gs_zby_36p)
    -   [How is the network performance of enterprise-level instances?](#section_omt_o32_8lt)
    -   [What types of disks do enterprise-level instances support?](#section_9st_mh4_j3f)
    -   [What types of images do enterprise-level instances support?](#section_h1y_jjt_aer)
    -   [What are the limits on upgrading or downgrading enterprise-level instances?](#section_rxb_abg_ub7)
    -   [Can I upgrade an entry-level instance to an enterprise-level instance?](#section_90e_qq9_gmf)
-   FAQ about GPU instances
    -   [After the NVIDIA driver is installed, nvidia-smi does not work and an error message is returned indicating that the NVIDIA driver has not been installed. Why?](#section_6fo_f6k_wy9)
    -   [Why doesn't the Windows Graphics support graphics-related applications such as DirectX?](#section_5mx_en9_guy)
    -   [A ga1 Windows instance uses an Alibaba Cloud Marketplace image that has an AMD driver pre-installed. However, the Windows Device Manager window shows that the GPU driver is unable to load properly. Why?](#section_myh_mu2_r7g)
    -   [Why do I encounter a blue-screen error when starting an instance that uses an Alibaba Cloud Marketplace image pre-installed with an AMD driver?](#section_593_bs5_c1l)
    -   [Do GPU instances support Android emulators?](#section_vwn_31g_4fn)
    -   [Can I upgrade or downgrade GPU instances?](#section_sbj_dzq_gb1)
    -   [Do pay-as-you-go GPU instances support the No Fees for Stopped Instances \(VPC-Connected\) feature?](#section_pw6_mpa_a0f)
    -   [How do I view GPU monitoring data?](#section_lv4_gwl_r5e)
-   FAQ about ECS Bare Metal Instances
    -   [What are the differences between ECS Bare Metal Instances, traditional cloud hosts \(virtual machines\), and traditional physical machines?](#section_m7m_pvm_64b)
    -   [How is the network performance of ECS Bare Metal Instances?](#section_mtz_x6v_4v4)
    -   [What types of disks do ECS Bare Metal Instances support? How many data disks can be attached to an ECS Bare Metal Instance?](#section_gu1_xmv_r8f)
    -   [Can I upgrade, downgrade, or migrate ECS Bare Metal Instances?](#section_qzc_rb4_og4)
-   FAQ about SCC
    -   [How do I create an SCC instance?](#section_9as_2qf_ted)
    -   [How are SCC instances billed?](#section_lew_64d_19y)
    -   [How do I create an SCC by using E-HPC?](#section_pq2_wpe_y7q)
    -   [How is SCC RDMA used?](#section_i2x_rle_0ql)
-   FAQ about preemptible instances
    -   [My account has no overdue payments. Why are my preemptible instances released?](#section_0ns_pj7_dxg)
    -   [Will I be notified when my preemptible instance is released? And how?](#section_b3n_69r_ccj)
    -   [Can data be automatically retained after a preemptible instance is released?](#section_hqu_m54_1ac)
    -   [Can I cancel or reschedule the automatic release of my preemptible instance?](#section_4dz_4mk_utb)
    -   [Can preemptible instances be converted to subscription instances?](#section_4bx_hwo_gre)
    -   [To what resources are the preemptible instance prices applicable?](#section_ns2_1jv_mbr)
    -   [How do I bid for a preemptible instance?](#section_vv0_a6s_5zd)
    -   [What is the relationship between the highest bid for a preemptible instance and the current market price?](#section_67i_s25_aqc)
    -   [Will I be charged the same fees for all my preemptible instances that start at the same time?](#section_y3x_sk2_stu)
    -   [Will I be charged at a price that fluctuates with the market price within one hour after my preemptible instance starts?](#section_scn_g76_t1n)
    -   [Can I view the current market price of an instance type when I purchase a preemptible instance?](#section_jxg_3ko_6xo)
    -   [Can I view the historical prices of a preemptible instance type? And how?](#section_z9a_do7_ofi)
    -   [Will preemptible instances continue to be billed after they are stopped?](#section_8yt_11m_q7i)
    -   [How do I view the consumption details of my preemptible instance?](#section_jg4_24g_j0e)
    -   [How many preemptible instances can be purchased under one account?](#section_d2v_giu_8a4)
    -   [How do I increase the maximum number of vCPUs?](#section_u2j_bsw_7vd)
    -   [Can I change the instance type of my preemptible instance?](#section_yae_a2y_k7c)
    -   [Which instance families support preemptible instances?](#section_8ws_4pm_9cc)
    -   [In which regions can I create preemptible instances?](#section_0zt_ehb_pts)
-   FAQ about reserved instances
    -   [What is a reserved instance?](#section_et2_64u_fmh)
    -   [Will a reserved instance provide a resource reservation?](#section_5g6_eu4_b0f)
    -   [What operating systems do reserved instances support?](#section_xoy_vzx_szv)
    -   [Which instance families do reserved instances support?](#section_j7h_12a_tuy)
    -   [Can reserved instances match preemptible instances to apply a discounted rate?](#section_m9r_qk6_39q)
    -   [Can I change the instance families of reserved instances?](#section_uee_304_jt3)
    -   [To what scenarios are zonal reserved instances applicable?](#section_wcp_t5l_01b)
    -   [To what scenarios are regional reserved instances applicable?](#section_rym_4rw_cl5)
    -   [How is the zone flexibility of regional reserved instances applied?](#section_6vd_nvw_m73)
    -   [How is the instance size flexibility of regional reserved instances applied?](#section_i9g_3my_drv)
    -   [Do zonal reserved instances provide instance size flexibility?](#section_tpd_tx9_9ri)
    -   [Do zonal reserved instances provide zone flexibility?](#section_qdz_h5b_f91)
    -   [Can I change a zonal reserved instance to a regional one?](#section_wry_8lc_jj4)
    -   [Can I change the scope of a reserved instance from one region to another?](#section_m89_45m_v6k)
    -   [Can I use reserved instances across accounts?](#section_6ta_i2c_mga)
    -   [Can I use reserved instances to cover the storage and network charges of pay-as-you-go instances?](#section_prg_o9w_0de)
    -   [Can I configure a reserved instance to apply its discounted rate to a specific pay-as-you-go instance?](#section_30a_ovt_uhz)
    -   [How are reserved instances billed?](#section_whe_bza_0u2)
    -   [When does a reserved instance take effect after I purchase it?](#section_cdy_tt0_n68)
    -   [When do my reserved instances take effect after I modify, split, or merge them?](#section_kfw_q23_shl)
    -   [Why isn't the No Upfront payment option displayed on the purchase page?](#section_95a_y2p_hcl)
    -   [Can I modify the payment option of my reserved instance?](#section_1ps_ydr_o6o)
    -   [Can I request a refund for a reserved instance?](#section_vnd_a46_hbz)
    -   [Can I resell a reserved instance?](#section_j9e_1zq_35v)
    -   [Can I use reserved instances to cover the image costs of pay-as-you-go Windows instances?](#section_0w6_6mr_z27)
    -   [Can I use reserved instances to cover the image costs of pay-as-you-go Linux instances?](#section_wm8_tf8_rgx)
-   FAQ about connecting to instances
    -   [Can multiple users connect to the Management Terminal simultaneously?](#section_mdm_w4q_wgb)
    -   [What can I do if I forget the password for remote connection?](#section_tym_x4q_wgb)
    -   [Why can't I connect to the Management Terminal even after I reset my password for remote connection?](#section_huk_e8x_b38)
    -   [Authentication failed on the Management Terminal. What can I do?](#section_xl9_o6y_79k)
    -   [What can I do if a black screen appears when I am connected to the Management Terminal?](#section_xrm_6sm_10m)
    -   [What can I do when I am unable to access the Management Terminal?](#section_65w_3px_xpu)
    -   [Why can't I use Internet Explorer 8.0 to access the Management Terminal?](#section_82j_21b_xj0)
    -   [When I use Firefox to access the Management Terminal, an error message is returned indicating that the secure connection has failed. What can I do?](#section_l6t_kik_vmy)
    -   [How do I remotely log on to a Linux instance?](#section_tkz_v77_wbf)
    -   [What are the default username and password for remote logon to the operating system of an ECS instance?](#section_u82_ecw_928)
-   FAQ about upgrading and downgrading instances
    -   [Can I upgrade my subscription instances?](#section_5ap_zkp_361)
    -   [Can I upgrade my pay-as-you-go instances?](#section_472_rev_qvi)
    -   [How long does it take to upgrade an ECS instance?](#section_ju8_yai_0f9)
    -   [How is the fee for upgrading an ECS instance calculated?](#section_ckm_8hg_3uy)
    -   [Does upgrading my ECS instance affect my cloud service configurations?](#section_s9y_1yw_w5c)
    -   [How do I upgrade my ECS resources?](#section_grz_gr2_rve)
    -   [I have upgraded an instance but no changes have taken effect yet. Why?](#section_jsb_os8_bbb)
-   FAQ about managing instances
    -   [The ECS instance has been in the Starting state for an extended period of time, and AliyunService was disabled or deleted. What can I do?](#section_3kd_bat_4p4)
    -   [How do I use f1 instances?](#section_ug1_lb2_d7l)
    -   [How do I upload files by using the FTP tool in macOS?](#section_39c_w47_rds)
    -   [How do I apply for an ICP filing for my domain name after buying an ECS instance?](#section_br4_f3k_1jw)
    -   [Why can't I start an ECS instance by loading the kernel?](#section_o58_xbc_j1a)
    -   [How do I change the logon password within an instance?](#section_5dx_x72_cb8)
    -   [Why can't I add sound or video cards to ECS instances?](#section_lqe_uwn_har)
    -   [Can I transfer the remaining service time of an ECS instance to another ECS instance?](#section_nwm_uhx_s6y)
    -   [Do ECS instances provide database capabilities by default?](#section_h97_kf4_xjp)
    -   [Can I build a database on an ECS instance?](#section_jli_u2y_g3m)
    -   [Do ECS instances support Oracle databases?](#section_j1b_acd_1f7)
    -   [Are public IP addresses and private IP addresses independent? Can I specify or add IP addresses?](#section_dvt_enw_7gr)
    -   [Can an ECS instance be used for load balancing?](#section_g6s_x91_9m2)
    -   [Can I change the region of an ECS instance?](#section_wm7_rby_mij)
    -   [Can I modify the partition size of a purchased disk?](#section_nih_446_koq)
    -   [How do I replace the public IP address of my ECS instance with an Elastic IP Address \(EIP\)?](#section_grq_3gj_n2r)
    -   [How do I view my subscription instances in the same region?](#section_bud_chq_gek)
    -   [How do I view subscription instances in all regions under my account?](#section_s5o_w6z_95z)
    -   [When can I forcibly stop my ECS instance? What will the consequence be?](#section_nlp_9qg_6gq)
    -   [Why can't I reactivate my ECS instance?](#section_vk6_sjc_agd)
-   FAQ about instance security
    -   [What is the AliVulfix process in an ECS instance?](#section_4ek_d0m_191)
    -   [How do I defend ECS instances against attacks?](#section_t6g_7b5_165)
    -   [What security services does Alibaba Cloud provide?](#section_cxr_p7b_a9w)
-   FAQ about using Linux instances
    -   [After I renew a subscription ECS Linux instance that expires, I am still unable to access the website it hosts. What can I do?](#section_s8j_d1f_1u6)
    -   [How do I check, partition, and format the data disks of a Linux instance?](#section_csf_vvp_2z1)
    -   [How do I upload files to a Linux instance?](#section_861_wjj_km6)
    -   [How do I change the owner and owner group of directories and files on a Linux instance?](#section_kf0_kn1_74z)
    -   [How do I update the software source of Linux instances?](#section_8jc_uw1_mjn)
    -   [How do I install a VNC server to access a Linux system by using a GUI?](#section_m4o_mku_bj2)
-   FAQ about instance limits
    -   [What limits apply to the transfer and change of public IP addresses of ECS instances?](#section_y49_iww_fvq)
    -   [Can I access amazon.com from my ECS instance?](#section_q6i_bio_ba9)
    -   [Why can't I access a website hosted outside China after I log on to my ECS instance?](#section_ags_ovh_bde)
    -   [I cannot purchase any more pay-as-you-go instances. What can I do?](#section_xt4_ax4_x66)
-   FAQ about instance billing
    -   [Are fees still incurred after a pay-as-you-go ECS instance is automatically stopped due to an overdue payment or is manually stopped?](#section_bll_9fl_9qs)
    -   [The order fails to be placed when I change the billing method of my ECS instance from pay-as-you-go to subscription. What can I do?](#section_ye3_pyk_bzl)
    -   [How long does it take to change the billing method after you pay for the order?](#section_07w_jp4_rlu)
    -   [What can I do if the change from pay-as-you-go to subscription fails?](#section_ulz_fn2_oxb)
    -   [Will the bandwidth billing method change after I change from pay-as-you-go to subscription?](#section_4lm_u5o_2my)
    -   [I have an unpaid order for changing the billing method of an instance from pay-as-you-go to subscription. If I upgrade the instance, will the order still be valid?](#section_tih_umb_qaz)
    -   [What can I do if the change from subscription to pay-as-you-go fails?](#section_xqt_ua4_1cf)
    -   [When I try to change the billing method of a disk in an ECS instance, an error message appears indicating that I have already changed the billing method three times. What does this mean?](#section_bxy_dkr_1f9)
    -   [Why can't I change a pay-as-you-go instance to a subscription one?](#section_vlz_58s_9es)
    -   [How do I view the expiration time of my subscription instances?](#section_8hf_t8x_5n3)

## How do I check whether instances are available for sale in a specified region or zone? {#section_dxe_iha_q0o .section}

You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy4service.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.

## What can I do if no resources are available when I create an ECS instance? {#section_lxw_bwz_qgb .section}

If no resources are available when you create an ECS instance, take any of the following measures:

-   Select another region
-   Select another zone
-   Change resource configurations

If still no resources are available after you take all the preceding measures, try again after some time. Instance resources are dynamic. When resources are insufficient, Alibaba Cloud replenishes them as soon as it can.

You can also use the arrival notice feature to get notified when resources are available.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/130429/156896162648634_en-US.png)

## How do I select an ECS instance that is suitable for my business? {#section_j8t_fwz_mjf .section}

-   Select an ECS instance based on your business requirements.
-   Determine your website type.
-   Determine the average number of page views per day on your website.
-   Determine the size of your homepage.
-   Determine the data capacity.

## How long does it take to create an ECS instance? {#section_ska_yf3_rvx .section}

It takes one or two minutes to create an ECS instance. After the instance is created:

**Note:** If an error occurs when you create an ECS instance, submit a ticket.

## I already paid for an ECS instance but no ECS instance was created. Why? {#section_gbw_acs_xwn .section}

If the specified zone has insufficient resources to create the instance type that you specified, the ECS instance fails to be created. A refund will be automatically credited to your account by the system. If you do not receive a refund within half an hour, submit a ticket.

You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy4service.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.

## What are enterprise-level instances? What are entry-level instances? {#section_2p8_osd_e5y .section}

Enterprise-level instances are a series of instance families released by Alibaba Cloud in September 2016. Enterprise-level instances feature high performance, consistent computing power, and balanced network performance. These instances have exclusive and consistent computing, storage, and network resources, and are applicable to enterprise scenarios with high business stability requirements.

Entry-level instances are a series of instance families that are targeted at small and medium websites or individuals. Compared with enterprise-level instances that have exclusive resources, entry-level instances share resources. Therefore, entry-level instances do not provide consistent computing performance but they have a lower cost.

## What are the differences between enterprise-level and entry-level instances? {#section_cm4_dks_zu1 .section}

Enterprise-level instances use the CPU-bound scheduling scheme. Each vCPU is bound to a CPU hyperthread. Instances do not compete for CPU resources and provide consistent computing performance as guaranteed in the SLA.

Entry-level instances use the CPU-unbound scheduling scheme. Each vCPU is randomly allocated to an idle CPU hyperthread. vCPUs of different instances compete for CPU resources. This results in fluctuations of computing performance when traffic loads are heavy. Therefore, entry-level instances guarantee only availability but not performance in the SLA.

## Which instance families are enterprise-level instances? Which instance families are entry-level instances? {#section_y0w_qjj_s3o .section}

Among the [instance families](reseller.en-US/Instances/Instance families.md#) that are available for sale, n4, mn4, xn4, and e4 are entry-level instances, and the others are enterprise-level instances.

## In what business scenarios do I need to purchase enterprise-level instances? {#section_8gs_zby_36p .section}

For the business scenarios to which different enterprise-level instances are applied, see [Instance families](reseller.en-US/Instances/Instance families.md#).

## How is the network performance of enterprise-level instances? {#section_omt_o32_8lt .section}

The network performance of enterprise-level instances depends on their specifications. The larger specifications enterprise-level instances have, the stronger network performance they provide. For more information about the network performance of different instance types, see [Instance families](reseller.en-US/Instances/Instance families.md#).

## What types of disks do enterprise-level instances support? {#section_9st_mh4_j3f .section}

For the disk types that enterprise-level instances support, see [Cloud disk overview](../reseller.en-US/Block Storage/Block storage/Cloud disk overview.md#).

## What types of images do enterprise-level instances support? {#section_h1y_jjt_aer .section}

For the public images that enterprise-level instances support, see [Public image overview](../reseller.en-US/Images/Public image/Public image overview.md#).

You can also import custom images. For more information, see [Import custom images](../reseller.en-US/Images/Custom image/Import images/Import custom images.md#).

## What are the limits on upgrading or downgrading enterprise-level instances? {#section_rxb_abg_ub7 .section}

For information about the limits on upgrading or downgrading enterprise-level instances, see [Instance type families that support instance type upgrades](reseller.en-US/Instances/Change configurations/Instance type families that support instance type upgrades.md#).

## Can I upgrade an entry-level instance to an enterprise-level instance? {#section_90e_qq9_gmf .section}

For the instance families that support instance type upgrades, see [Instance type families that support instance type upgrades](reseller.en-US/Instances/Change configurations/Instance type families that support instance type upgrades.md#).

## After the NVIDIA driver is installed, nvidia-smi does not work and an error message is returned indicating that the NVIDIA driver has not been installed. Why? {#section_6fo_f6k_wy9 .section}

Cause: The kernel version is inconsistent with the kernel-devel package version. This results in a driver compilation error when the driver is installed from the .rpm file.

Solution: Check the kernel version and download the correct kernel-devel package version. Then, run the `rpm –qa | grep kernel` command on the instance to check whether the kernel-devel package version matches the kernel version. Make sure that they match and then reinstall the driver.

## Why doesn't the Windows Graphics support graphics-related applications such as DirectX? {#section_5mx_en9_guy .section}

Cause: On Windows instances where the installed GPU drivers have taken effect, the Windows Remote Desktop Protocol \(RDP\) does not support DirectX, OpenGL, or other graphics-related applications.

Solution: Install Virtual Network Computing \(VNC\) servers and clients or other protocols that support these applications, such as PC over IP \(PCoIP\) and XenDeskop HDX 3D.

## A ga1 Windows instance uses an Alibaba Cloud Marketplace image that has an AMD driver pre-installed. However, the Windows Device Manager window shows that the GPU driver is unable to load properly. Why? {#section_myh_mu2_r7g .section}

1.  Log on to the instance.
2.  Open the **Device Manager** window.
3.  Right-click the GPU device****.
4.  Select **Update Driver Software** from the shortcut menu.
5.  Then, select **Search automatically for updated driver software**.
6.  After the device driver is updated, restart the instance.

## Why do I encounter a blue-screen error when starting an instance that uses an Alibaba Cloud Marketplace image pre-installed with an AMD driver? {#section_593_bs5_c1l .section}

Alibaba Cloud will update the driver included in the Alibaba Cloud Marketplace image to solve this problem. If you are using an image of any earlier version, update the GPU driver to avoid this issue.

If you encounter a blue-screen error and cannot start an instance, you must enter Safe Mode. In Safe Mode, uninstall the existing driver, start Windows normally, and then install a GPU driver of the latest version.

## Do GPU instances support Android emulators? {#section_vwn_31g_4fn .section}

No, they do not support Android emulators.

## Can I upgrade or downgrade GPU instances? {#section_sbj_dzq_gb1 .section}

You cannot upgrade or downgrade GPU instances that are equipped with local disks, such as ga1 and gn5 instances. For the GPU instances that are not equipped with local disks and can be upgraded or downgraded, see [Instance type families that support instance type upgrades](reseller.en-US/Instances/Change configurations/Instance type families that support instance type upgrades.md#).

## Do pay-as-you-go GPU instances support the No Fees for Stopped Instances \(VPC-Connected\) feature? {#section_pw6_mpa_a0f .section}

GPU instances that are not equipped with local disks support the No Fees for Stopped Instances \(VPC-Connected\) feature. Such GPU instances include gn4 \(with NVIDIA M40 GPU processors\), gn5i \(with NVIDIA P4 GPU processors\), and gn6v \(with NVIDIA V100 GPU processors\) instances. For more information, see [No fees for stopped VPC instances](../reseller.en-US/Pricing/No fees for stopped VPC instances.md#).

## How do I view GPU monitoring data? {#section_lv4_gwl_r5e .section}

You can log on to the [CloudMonitor console](https://partners-intl.console.aliyun.com/#/cms) or call the [DescribeMetricList](../../../../../reseller.en-US/API Reference/Monitoring data on time series metrics of cloud services/DescribeMetricList.md#) operation to view GPU monitoring data. For more information, see [GPU monitoring](../../../../../reseller.en-US/User Guide/Host monitoring/GPU monitoring.md#).

## What are the differences between ECS Bare Metal Instances, traditional cloud hosts \(virtual machines\), and traditional physical machines? {#section_m7m_pvm_64b .section}

For the differences between ECS Bare Metal Instances, traditional cloud hosts \(virtual machines\), and traditional physical machines, see [What is an ECS Bare Metal Instance?](reseller.en-US/Instances/Instance type families/ECS bare metal instance type family/What is an ECS Bare Metal Instance?.md#).

## How is the network performance of ECS Bare Metal Instances? {#section_mtz_x6v_4v4 .section}

The network performance of ECS Bare Metal Instances depends on their specifications. The larger specifications ECS Bare Metal Instances have, the stronger network performance they provide. For more information about the network performance of different ECS Bare Metal Instance types, see [Instance families](reseller.en-US/Instances/Instance families.md#).

## What types of disks do ECS Bare Metal Instances support? How many data disks can be attached to an ECS Bare Metal Instance? {#section_gu1_xmv_r8f .section}

ECS Bare Metal Instances support ultra disks and standard SSDs. Up to 16 data disks can be attached to each ECS Bare Metal Instance.

## Can I upgrade, downgrade, or migrate ECS Bare Metal Instances? {#section_qzc_rb4_og4 .section}

You cannot upgrade or downgrade ECS Bare Metal Instances. When the hardware of the physical machine where an ECS Bare Metal Instance resides fails, you can migrate the ECS Bare Metal Instance to another physical machine. Data is stored in the data disks of the instance.

## How do I create an SCC instance? {#section_9as_2qf_ted .section}

You can create an SCC instance in either of the following ways:

-   If you only want to use RDMA, log on to the ECS console. [Create an SCC instance](reseller.en-US/Instances/Instance type families/Super Computing Cluster instance type family/Create an SCC instance.md#).
-   If you want to use the HPC scheduler and cluster resizing service in addition to RDMA, log on to the [E-HPC console](https://partners-intl.console.aliyun.com/#/ehpc). Create an SCC and then create an SCC instance.

## How are SCC instances billed? {#section_lew_64d_19y .section}

SCC instances support the weekly, monthly, and yearly subscription billing methods.

## How do I create an SCC by using E-HPC? {#section_pq2_wpe_y7q .section}

You can log on to the [E-HPC console](https://partners-intl.console.aliyun.com/#/ehpc) or call the CreateCluster operation to create an SCC.

## How is SCC RDMA used? {#section_i2x_rle_0ql .section}

When you create an SCC instance, select a custom image for SCC, which supports the RDMA RoCE driver and OFED stack. You can use SCC RDMA through the IB Verbs API or manage RDMA communication through the MPI.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/130429/156896162650536_en-US.png)

## My account has no overdue payments. Why are my preemptible instances released? {#section_0ns_pj7_dxg .section}

You can reserve a preemptible instance without interruptions for at least one hour. After one hour, your bid is compared with the market price. When the market price exceeds your bid or resources are insufficient, your preemptible instance is automatically released.

## Will I be notified when my preemptible instance is released? And how? {#section_b3n_69r_ccj .section}

Yes, you will be notified when your preemptible instance is released. When your preemptible instance needs to be released due to a change in market price or due to insufficient resources, the instance will first enter the To Be Released state. After 5 minutes, the instance will be automatically released. You can check whether the instance in the To Be Released state based on the [instance metadata](reseller.en-US/Instances/Manage instances/User-defined data and metadata/Metadata.md#) or OperationLocks information returned by the [DescribeInstances](../reseller.en-US/API Reference/Instances/DescribeInstances.md#) operation.

## Can data be automatically retained after a preemptible instance is released? {#section_hqu_m54_1ac .section}

No, data cannot be automatically retained. When you no longer need a preemptible instance, we recommend that you [create snapshots](../reseller.en-US/Snapshots/Use snapshots/Create a snapshot.md#) to back up your data and environment and then release the instance. You can purchase new preemptible instances at any time as needed.

## Can I cancel or reschedule the automatic release of my preemptible instance? {#section_4dz_4mk_utb .section}

Yes, you can cancel or reschedule the automatic release of your preemptible instance at any time.

## Can preemptible instances be converted to subscription instances? {#section_4bx_hwo_gre .section}

No, they cannot.

## To what resources are the preemptible instance prices applicable? {#section_ns2_1jv_mbr .section}

The preemptible instance prices apply to instance types only. Other resources of preemptible instances, such as system disks, data disks, and network bandwidth, are billed at the same rates as those of pay-as-you-go instances, without discounts.

## How do I bid for a preemptible instance? {#section_vv0_a6s_5zd .section}

To create a preemptible instance, you must set the highest hourly price you are willing to pay for an instance type. If your bid is higher than or equal to the current market price, your instance is created and billed based on the current market price. For more information, see [Create a preemptible instance](reseller.en-US/Instances/Instance purchasing options/Preemptible instances/Create a preemptible instance.md#).

## What is the relationship between the highest bid for a preemptible instance and the current market price? {#section_67i_s25_aqc .section}

The highest bid for a preemptible instance must be higher or equal to the current market price. If the highest bid is lower than the market price, no new preemptible instance is created or the running preemptible instances may be released. Your preemptible instance will be billed based on the market price regardless of your bid.

## Will I be charged the same fees for all my preemptible instances that start at the same time? {#section_y3x_sk2_stu .section}

Yes.

## Will I be charged at a price that fluctuates with the market price within one hour after my preemptible instance starts? {#section_scn_g76_t1n .section}

No, the hourly price of your preemptible instance is set at the beginning of each hour and applies to the instance within the whole hour.

## Can I view the current market price of an instance type when I purchase a preemptible instance? {#section_jxg_3ko_6xo .section}

Yes. When you create a preemptible instance in the ECS console, you can view the current market price and historical prices of an instance type after you select it. The total price that includes the fees for the instance type, storage, and bandwidth is displayed at the lower-left corner of the instance creation page. The instance type price is the current market price of the specified instance type.

## Can I view the historical prices of a preemptible instance type? And how? {#section_z9a_do7_ofi .section}

Yes. You can view the historical prices of a preemptible instance type by selecting it in the ECS console. You can also call the [DescribeSpotPriceHistory](../reseller.en-US/API Reference/Instances/DescribeSpotPriceHistory.md#) operation to view the historical prices of an instance type.

## Will preemptible instances continue to be billed after they are stopped? {#section_8yt_11m_q7i .section}

Yes. When you no longer need a preemptible instance, we recommend that you [create snapshots](../reseller.en-US/Snapshots/Use snapshots/Create a snapshot.md#) to back up your data and environment and then release the instance. You can purchase new preemptible instances at any time as needed.

**Note:** Preemptible instances will continue to be billed after you stop them in the ECS console or by calling the StopInstance operation.

## How do I view the consumption details of my preemptible instance? {#section_jg4_24g_j0e .section}

See [View bills of a preemptible instance](reseller.en-US/Instances/Instance purchasing options/Preemptible instances/Create a preemptible instance.md#section_pkj_3qt_qgb).

**Note:** The total cost displayed when you create a pay-as-you-go instance is the hourly price to be charged for actual usage. However, the total cost displayed when you create a preemptible instance is the actual transaction price.

## How many preemptible instances can be purchased under one account? {#section_d2v_giu_8a4 .section}

There is a limit on the maximum number of vCPUs that can be allocated to preemptible instances for each account. When you create a preemptible instance, you can view the number of available vCPUs after you select an instance type. For more information, see [Limits](../reseller.en-US/Product Introduction/Limits.md#section_tbg_zdx_wdb).

## How do I increase the maximum number of vCPUs? {#section_u2j_bsw_7vd .section}

Submit a ticket.

## Can I change the instance type of my preemptible instance? {#section_yae_a2y_k7c .section}

No, you cannot change the instance type of your preemptible instance.

## Which instance families support preemptible instances? {#section_8ws_4pm_9cc .section}

The instance families that support the pay-as-you-go billing method also support preemptible instances. If you cannot create preemptible instances of an instance type due to insufficient resources, try a different instance type.

## In which regions can I create preemptible instances? {#section_0zt_ehb_pts .section}

You can create preemptible instances in all regions. If you cannot create preemptible instances in a region due to insufficient resources, try a different region.

## What is a reserved instance? {#section_et2_64u_fmh .section}

Reserved instances automatically match pay-as-you-go instances \(not including preemptible instances\) in your account to provide a billing discount. Reserved instances can also be used to reserve resources for pay-as-you-go instances. Compared with subscription instances, the combination of reserved instances and pay-as-you-go instances provides similar cost-effectiveness and higher flexibility.

## Will a reserved instance provide a resource reservation? {#section_5g6_eu4_b0f .section}

Zonal reserved instances provide resource reservations, but regional reserved instances do not.

## What operating systems do reserved instances support? {#section_xoy_vzx_szv .section}

Reserved instances support both Windows and Linux. For example, a Linux reserved instance can be applied to pay-as-you-go Linux instances that match its attributes, regardless of the image types \(public images, custom images, shared images, and Alibaba Cloud Marketplace images\) these instances use.

If your pay-as-you-go instance uses a BYOL image and you want to apply the discounted rate provided by a reserved instance to your instance, submit a ticket.

## Which instance families do reserved instances support? {#section_j7h_12a_tuy .section}

The following instance families support reserved instances: sn1ne, sn2ne, se1ne, ic5, c5, g5, r5, c6, g6, r6, i2, i2g, hfc5, hfg5, and t5.

Reserved instances matching [t5 burstable instances](reseller.en-US/Instances/Instance type families/Burstable performance instances/Overview.md#) are only available at the zone level. These reserved instances cannot be merged or split, and their scopes cannot be modified.

## Can reserved instances match preemptible instances to apply a discounted rate? {#section_m9r_qk6_39q .section}

No.

## Can I change the instance families of reserved instances? {#section_uee_304_jt3 .section}

No.

## To what scenarios are zonal reserved instances applicable? {#section_wcp_t5l_01b .section}

We recommend that you purchase zonal reserved instances when you have clear requirements to reserve resources.

## To what scenarios are regional reserved instances applicable? {#section_rym_4rw_cl5 .section}

We recommend that you purchase regional reserved instances if you want to enjoy better zone and instance size flexibility.

## How is the zone flexibility of regional reserved instances applied? {#section_6vd_nvw_m73 .section}

Only regional reserved instances provide zone flexibility. Example:

You have the following pay-as-you-go instance running:

One ecs.c5.xlarge Linux instance in Qingdao Zone B. The instance name is C5PAYG-b.

You have purchased the following reserved instance:

One regional ecs.c5.xlarge reserved instance in the China \(Qingdao\) region. The name of the reserved instance is C5RI.

C5RI matches C5PAYG-b to apply a discounted rate.

You release C5PAYG-b and start another Linux instance named C5PAYG-c, which is of the same instance type as C5PAYG-b. C5RI then matches C5PAYG-c.

## How is the instance size flexibility of regional reserved instances applied? {#section_i9g_3my_drv .section}

Only regional reserved instances provide instance size flexibility. Example:

You have one regional ecs.g5.4xlarge reserved instance. It can match one ecs.g5.4xlarge pay-as-you-go instance, two ecs.g5.2xlarge pay-as-you-go instances, or four ecs.g5.xlarge pay-as-you-go instances.

You have a one-year regional ecs.g5.xlarge reserved instance. It can match one ecs.g5.xlarge instance running for one year, or one ecs.g5.2xlarge instance running for six months.

## Do zonal reserved instances provide instance size flexibility? {#section_tpd_tx9_9ri .section}

No. A zonal reserved instance can only match pay-as-you-go instances of the same instance type as it.

## Do zonal reserved instances provide zone flexibility? {#section_qdz_h5b_f91 .section}

No. A zonal reserved instance can only match pay-as-you-go instances in the same zone as it.

## Can I change a zonal reserved instance to a regional one? {#section_wry_8lc_jj4 .section}

Yes. You can change the scope of a reserved instance you purchased as follows:

-   From a zone to a region
-   From a region to a zone
-   From one zone to another within the same region for a zonal reserved instance.

## Can I change the scope of a reserved instance from one region to another? {#section_m89_45m_v6k .section}

No. For example, if you have a zonal reserved instance in Hangzhou Zone B, you can change the instance scope to another zone or change the instance to a regional reserved instance in the China \(Hangzhou\) region. However, you cannot change it to a regional or zonal reserved instance in another region.

## Can I use reserved instances across accounts? {#section_6ta_i2c_mga .section}

No.

## Can I use reserved instances to cover the storage and network charges of pay-as-you-go instances? {#section_prg_o9w_0de .section}

No. Reserved instances cover the compute \(vCPU and memory\) costs of pay-as-you-go instances. For pay-as-you-go Windows instances, reserved instances also cover the image costs.

## Can I configure a reserved instance to apply its discounted rate to a specific pay-as-you-go instance? {#section_30a_ovt_uhz .section}

No. When you have multiple pay-as-you-go instances that match the attributes of a reserved instance, the discounted rate is applied automatically to pay-as-you-go instances based on the optimized matching scheme.

## How are reserved instances billed? {#section_whe_bza_0u2 .section}

Reserved instances are billed separately and support the All Upfront, Partial Upfront, and No Upfront payment options.

The term of a reserved instance starts immediately after you purchase it. You are charged based on your selected payment option regardless of whether pay-as-you-go instances are matched. The All Upfront option is the most cost-effective.

## When does a reserved instance take effect after I purchase it? {#section_cdy_tt0_n68 .section}

The reserved instance takes effect and starts to be billed on the hour \(zero minutes and zero seconds past the hour\) of your purchase. It expires at 00:00:00 the day after the term end date. For example, if you purchase a one-year reserved instance at 2019-02-26 13:45:00, the reserved instance takes effect and starts to be billed at 2019-02-26 13:00:00 and will expire at 2020-02-27 00:00:00. If you purchase a reserved instance that matches your existing pay-as-you-go instances, the discounted rate is applied to bills generated for the pay-as-you-go instances starting from 13:00 to 14:00 on February 26, 2019 until the reserved instance expires.

## When do my reserved instances take effect after I modify, split, or merge them? {#section_kfw_q23_shl .section}

After reserved instances are modified, split, or merged, new reserved instances are generated, and the original ones become invalid. The new reserved instances take effect on the hour, and the original reserved instance become invalid at the same time. For example, you split an ecs.g5.2xlarge zonal reserved instance RI1 into two zonal ecs.g5.xlarge reserved instances RI2 and RI3 at 2019-02-26 13:45:00. RI1 becomes invalid and RI 2 and RI 3 take effect at 2019-02-26 13:00:00. As of 2019-02-26 13:00:00, the eligible reserved instance type also changes from ecs.g5.2xlarge to ecs.g5.xlarge. If RI2 and RI3 match pay-as-you-go instances immediately after they take effect, the discounted rates provided by RI2 and RI3 are applied to the hourly bills of ecs.g5.xlarge pay-as-you-go instances as of 2019-02-26 13:00:00.

## Why isn't the No Upfront payment option displayed on the purchase page? {#section_95a_y2p_hcl .section}

The availability of this option depends on your ECS usage.

## Can I modify the payment option of my reserved instance? {#section_1ps_ydr_o6o .section}

No.

## Can I request a refund for a reserved instance? {#section_vnd_a46_hbz .section}

In the following cases, you can open a ticket to claim a refund:

-   The instance resources are in short supply in the target region or zone after you have purchased RIs.
-   The instance resources are in short supply in the target region or zone after you have split or merged RIs, or adjusted the RI scope.

## Can I resell a reserved instance? {#section_j9e_1zq_35v .section}

No.

## Can I use reserved instances to cover the image costs of pay-as-you-go Windows instances? {#section_0w6_6mr_z27 .section}

Yes. Windows reserved instances already include Windows image costs. Therefore, you can use them to cover the image costs of your pay-as-you-go Windows instances.

## Can I use reserved instances to cover the image costs of pay-as-you-go Linux instances? {#section_wm8_tf8_rgx .section}

No.

## Can multiple users connect to the Management Terminal simultaneously? {#section_mdm_w4q_wgb .section}

No, only one user can connect to the Management Terminal at a time.

## What can I do if I forget the password for remote connection? {#section_tym_x4q_wgb .section}

You can reset your password for remote connection. For more information, see [Connect to a Linux instance by using the Management Terminal](reseller.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using the Management Terminal.md#).

## Why can't I connect to the Management Terminal even after I reset my password for remote connection? {#section_huk_e8x_b38 .section}

If the ECS instance to which you are connecting is not I/O optimized, you must restart the instance in the ECS console for the new password to take effect. For more information, see [Restart an instance](reseller.en-US/Instances/Manage instances/Restart an instance.md#).

**Note:** If the ECS instance is restarted from within the instance itself, the new password will not take effect.

## Authentication failed on the Management Terminal. What can I do? {#section_xl9_o6y_79k .section}

If you enter an incorrect password, authentication fails on the Management Terminal. Perform the following steps to troubleshoot the problem:

1.  Enter the correct password.
2.  If you forget your password, [reset your password for remote connection](reseller.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using the Management Terminal.md#section_nmj_5mx_wdb) and try again.
3.  If the ECS instance that you are connecting to is not I/O optimized, you must [restart the instance](reseller.en-US/Instances/Manage instances/Restart an instance.md#) in the ECS console for the new password to take effect.

## What can I do if a black screen appears when I am connected to the Management Terminal? {#section_xrm_6sm_10m .section}

A black screen indicates that the instance is in sleep mode. Perform the following operations based on your operating system:

-   For a Linux instance, click your mouse or press any key to activate the instance.
-   For a Windows instance, in the upper-left corner of the Management Terminal page, choose **Send Remote Call** \> **CTRL+ALT+DELETE** to open the logon dialog box.

## What can I do when I am unable to access the Management Terminal? {#section_65w_3px_xpu .section}

Use Google Chrome to connect to the Management Terminal, and press F12 to open the developer tools pane. Then click the **Console** tab and analyze the information displayed to find errors.

## Why can't I use Internet Explorer 8.0 to access the Management Terminal? {#section_82j_21b_xj0 .section}

The Management Terminal supports Internet Explorer 10 and later.

We recommend that you use Google Chrome, which is the most compatible with the Management Terminal.

## When I use Firefox to access the Management Terminal, an error message is returned indicating that the secure connection has failed. What can I do? {#section_l6t_kik_vmy .section}

This problem occurs if the encryption algorithm of your Firefox version is different from that of the Management Terminal.

We recommend that you use Google Chrome, which is the most compatible with the Management Terminal.

## How do I remotely log on to a Linux instance? {#section_tkz_v77_wbf .section}

Linux instances use SSH for remote connection. You can use any of the following methods to remotely log on to a Linux instance:

-   [Connect to a Linux instance by using the Management Terminal](reseller.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using the Management Terminal.md#).
-   [Connect to a Linux instance by using a password](reseller.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using a password.md#).
-   [Connect to a Linux instance by using an SSH key pair](reseller.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using an SSH key pair.md#).
-   [Connect to an instance on a mobile device](reseller.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to an instance on a mobile device.md#).

## What are the default username and password for remote logon to the operating system of an ECS instance? {#section_u82_ecw_928 .section}

The default username depends on the operating system.

-   For a Windows instance, the default username is `administrator`.
-   For a Linux instance, the default username is `root`.

The password for remote logon to the operating system is set by you when you create the instance. For more information, see [Create an instance by using the wizard](reseller.en-US/Instances/Create an instance/Create an instance by using the wizard.md#). If you forget your password, you can reset the password. For more information, see [Reset an instance logon password](reseller.en-US/Instances/Manage instances/Reset an instance logon password.md#).

**Note:** This password is used to remotely log on to the operating system of an ECS instance, not to the Management Terminal.

## Can I upgrade my subscription instances? {#section_5ap_zkp_361 .section}

Yes, you can upgrade your subscription instances. For more information, see [Upgrade configurations of Subscription instances](reseller.en-US/Instances/Change configurations/Upgrade configurations/Upgrade configurations of Subscription instances.md#).

## Can I upgrade my pay-as-you-go instances? {#section_472_rev_qvi .section}

Yes, but you must stop your pay-as-you-go instances before you can upgrade them. You can upgrade your pay-as-you-go instances by following the instructions in [Change configurations of Pay-As-You-Go instances](reseller.en-US/Instances/Change configurations/Change configurations of Pay-As-You-Go instances/Change configurations of Pay-As-You-Go instances.md#) or calling the [ModifyInstanceSpec](../reseller.en-US/API Reference/Instances/ModifyInstanceSpec.md#) operation.

## How long does it take to upgrade an ECS instance? {#section_ju8_yai_0f9 .section}

-   To upgrade a subscription instance, you do not need to stop it. The upgrade process takes about 15 minutes.
-   To upgrade a pay-as-you-go instance, you must stop it first. The upgrade process takes about 15 minutes.
-   To upgrade the bandwidth of an instance, you do not need to stop the instance. The upgrade process takes about 5 minutes.

## How is the fee for upgrading an ECS instance calculated? {#section_ckm_8hg_3uy .section}

The upgrade fee and its calculation are displayed when you upgrade the instance. You can also view the details of the fee on the [Account Overview](https://expense.console.aliyun.com/) page.

## Does upgrading my ECS instance affect my cloud service configurations? {#section_s9y_1yw_w5c .section}

You must stop a pay-as-you-go instance before you can upgrade it. After you upgrade a subscription instance, you must restart it for the new specifications to take effect. The upgrade operation will interrupt your services for a short period of time. We recommend that you upgrade your instance during off-peak hours. Instances can seamlessly resume services after upgrades without server environment reconfiguration.

## How do I upgrade my ECS resources? {#section_grz_gr2_rve .section}

For details about how to upgrade ECS resources, see [Overview of configuration changes](reseller.en-US/Instances/Change configurations/Overview of configuration changes.md#).

-   Except for ECS instances that use local storage, ECS instances support online CPU scaling, online memory scaling, and online bandwidth upgrades.
-   A maximum of 16 data disks can be attached to an ECS instance. You cannot reduce the size of a data disk after you expand it.
-   The ECS bandwidth is measured in megabits per second \(Mbit/s\) and ranges from 0 Mbit/s to 200 Mbit/s. You can also temporarily upgrade the bandwidth of your ECS instance, or downgrade the instance when you renew it.

## I have upgraded an instance but no changes have taken effect yet. Why? {#section_jsb_os8_bbb .section}

To make the new specifications take effect, you need to [restart the instance](reseller.en-US/Instances/Manage instances/Restart an instance.md#).

## The ECS instance has been in the Starting state for an extended period of time, and AliyunService was disabled or deleted. What can I do? {#section_3kd_bat_4p4 .section}

Problem description: After you start an ECS instance, it remains in the Starting state for an extended period of time before automatically shutting down. You log on to the instance and find that AliyunService was deleted or disabled in the system services.

Solution:

-   If AliyunService is disabled:
    1.  Change the state of AliyunService to Automatic.
    2.  Restart the instance.
-   If AliyunService is deleted:
    1.  Run the following command to add AliyunService to the instance:

        ``` {#codeblock_z9n_oe1_dty}
        sc create AliyunService type= "own" start= "auto" binPath= "C:\Program Files\AliyunService\AliyunService.exe -d" tag= "no" DisplayName= "AliyunService"
        ```

        **Note:** Make sure you leave a space after the equal signs `(=)`.

    2.  Find the registry key HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\services\\AliyunService, and change `c:\Program Files\AliyunService\AliyunService.exe -d` to `"c:\Program Files\AliyunService\AliyunService.exe" -d`.
    3.  Restart the instance.

## How do I use f1 instances? {#section_ug1_lb2_d7l .section}

After your application for an f1 instance trial is approved, Alibaba Cloud will share an FPGA development image with you. Only CentOS 7u2 images are available at this time. The image includes the complete Intel Quartus development suite and the constraint files for the f1 instance to provide a complete cloud development environment.

**Note:** You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy4service.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.

The basic workflow for using f1 instances is as follows:

1.  After development, generate an intermediate QAR file during the compilation stage, and upload the file to an OSS bucket. You can upload this file only to an OSS bucket in the China \(Hangzhou\) region. Then, register the QAR file information with Alibaba Cloud by calling an API operation.

    We recommend that you use the free Intel Quartus development suite to perform development, compilation, and simulation operations on the cloud.

2.  Alibaba Cloud verifies the registration request for the QAR file. After the verification succeeds, Alibaba Cloud sends you an email that includes an FPGA image ID.
3.  When you deploy the image, call an API operation with the f1 instance ID and FPGA image ID specified to associate the instance with the image.

    You can initiate the association operation in any scenario where ECS API is available.

    -   If no FPGA image has ever been associated with the f1 instance, directly initiate the association operation.
    -   If the f1 instance was previously associated with an FPGA image and had the image loaded, erase the FPGA image from the f1 instance before initiating the association operation.
4.  After the association, call an API operation to load the FPGA image.

    You must initiate the load operation from the f1 instance. Then the underlying service of Alibaba Cloud burns the associated FPGA image to the corresponding FPGA on the instance.


If you want to restore the f1 instance to its initial state, call an API operation to erase the burned FPGA image from the f1 instance.

For more instructions on f1 instances, see:

-   [Create an f1 instance](reseller.en-US/Instances/Instance type families/Compute optimized type family with FPGA/Create an f1 instance.md#)
-   [Use OpenCL on an f1 instance](../reseller.en-US/Best Practices/FaaS instances best practices/Use OpenCL on an f1 instance.md#)
-   [Use RTL compiler on an f1 instance](../reseller.en-US/Best Practices/FaaS instances best practices/Use RTL compiler on an f1 instance.md#)

## How do I upload files by using the FTP tool in macOS? {#section_39c_w47_rds .section}

Upload files by using the Terminal in macOS

Open the Terminal in macOS or iTerm2 for Mac \(click [here](https://www.iterm2.com/) to download iTerm2\). Make sure that you select the correct destination path.

1.  Connect to the FTP server.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/130429/156896162643224_en-US.png)

2.  Enter the destination directory. If the directory is on a Windows instance, use the directory directly. If it is on a Linux instance, change the directory to htdocs.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/130429/156896162649119_en-US.png)

3.  Run the put command to upload files.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/130429/156896162649120_en-US.png)


Upload files by using a third-party tool

1.  Click [here](https://www.yummysoftware.com/) to download Yummy FTP.
2.  Install Yummy FTP.
3.  Enter the server IP address, username, and password. Set Protocol to Standard \(FTP\) and Port to 21 or a port number you are using, and leave the SSH key field unselected.
4.  Click **Connect**.
5.  In the right section, select the destination directory. If the directory is on a Windows instance, use the directory directly. If it is on a Linux instance, change the directory to htdocs. In the left section, select the files and click the Upload icon to upload files.

    **Note:** If you are prompted with a message similar to "Your security preferences only allow the installation of applications from the Mac App Store and authorized developers" when you try to install Yummy FTP, perform these steps:

    1.  Choose **System Preference** \> **Security and Privacy**.
    2.  Click the security lock in the lower-left corner of the window, and enter the administrator password.
    3.  Select **Anywhere** for **Allow apps download from**.
    Then, you can upload files by using Yummy FTP.


If you have further questions, submit a ticket.

## How do I apply for an ICP filing for my domain name after buying an ECS instance? {#section_br4_f3k_1jw .section}

You can apply for a limited number of ICP filing service numbers for an ECS instance. For more information, see [Prepare and check the instance](../../../../../reseller.en-US/Before ICP Filing/Host instances and service providers/Prepare and check the instance.md#).

For information about how to apply for an ICP filing, see [Quick Start](../../../../../reseller.en-US/ICP Quick Start/Quick Start.md#).

## Why can't I start an ECS instance by loading the kernel? {#section_o58_xbc_j1a .section}

Problem description: When the system starts, it does not respond when I select an option from the GRUB menu. After the LiveCD image is loaded on the ECS instance, verify that file system privileges are correct and there are no exceptions in the message logs.

Cause: The system is attacked by ransomware.

Solution: Back up your data and reinitialize the system.

For more information, see [Recover from ransomware attacks](https://help.aliyun.com/knowledge_detail/50358.html).

## How do I change the logon password within an instance? {#section_5dx_x72_cb8 .section}

For details, see [Change the instance logon password by connecting to the instance](reseller.en-US/Instances/Manage instances/Change the instance logon password by connecting to the instance.md#).

## Why can't I add sound or video cards to ECS instances? {#section_lqe_uwn_har .section}

This is because the servers that Alibaba Cloud provides are not multimedia servers. These servers do not provide sound card and video card components.

## Can I transfer the remaining service time of an ECS instance to another ECS instance? {#section_nwm_uhx_s6y .section}

No. If you want both higher flexibility and cost-effectiveness, we recommend that you use a combination of reserved instances and pay-as-you-go instances. For more information, see [Reserved instance overview](reseller.en-US/Instances/Instance purchasing options/Reserved Instances/Reserved instance overview.md#).

## Do ECS instances provide database capabilities by default? {#section_h97_kf4_xjp .section}

No, ECS instances do not provide database capabilities by default. To use database services, perform the following operations:

-   Deploy your database. For more information about how to deploy a database on an ECS instance, see [在ECS上部署数据库](../reseller.en-US/Tutorials/Deploy databases based on ECS/在ECS上部署数据库.md#).
-   Purchase [ApsaraDB for RDS](https://rdsnext.console.aliyun.com/) provided by Alibaba Cloud.
-   Use a database image provided in Alibaba Cloud Marketplace.

## Can I build a database on an ECS instance? {#section_jli_u2y_g3m .section}

Yes, you can install database software and configure a database environment on an ECS instance as needed. You can also separately purchase [ApsaraDB for RDS](https://rdsnext.console.aliyun.com/) provided by Alibaba Cloud.

## Do ECS instances support Oracle databases? {#section_j1b_acd_1f7 .section}

Yes. We recommend that before installing an Oracle database, you perform a performance stress test on an ECS instance to ensure that the instance can satisfy the read/write requirements of the database.

## Are public IP addresses and private IP addresses independent? Can I specify or add IP addresses? {#section_dvt_enw_7gr .section}

In classic networks, public and private IP addresses are independent of each other. Private IP addresses in classic networks are used for communication between ECS instances and communication between ECS instances and OSS or RDS instances. When the 0 Mbit/s bandwidth is selected for an ECS instance, no public IP address is allocated to the instance. Typically, public and private IP addresses in classic networks do not change. You cannot specify, select, or add IP addresses.

In VPCs, NAT gateways map public IP addresses to private IP addresses. You can specify secondary private IP addresses or add multiple IP addresses.

## Can an ECS instance be used for load balancing? {#section_g6s_x91_9m2 .section}

ECS Linux and Windows instances can be used for load balancing. You must ensure that the configurations of ECS instances serving as Web servers meet the requirements for website code to run. Load balancing can be implemented with as few as one ECS instance under an account. However, we recommend you use two or more ECS instances for load balancing to ensure the load balancing effect.

## Can I change the region of an ECS instance? {#section_wm7_rby_mij .section}

No, you cannot change the region of an ECS instance.

## Can I modify the partition size of a purchased disk? {#section_nih_446_koq .section}

For system security and stability purposes, system disks do not support secondary partitioning on either Windows or Linux instances. If you use a third-party tool to perform secondary partitioning, unknown exceptions such as system failure and data loss might occur.

Secondary partitioning of data disks may cause data loss. We do not recommend that you perform secondary partitioning on data disks.

## How do I replace the public IP address of my ECS instance with an Elastic IP Address \(EIP\)? {#section_grq_3gj_n2r .section}

To replace the public IP address of your ECS instance with an EIP, ensure that you have selected pay-by-bandwidth as the bandwidth billing method for your ECS instance and that you have purchased a new EIP. Then, perform the following steps:

1.  Change the bandwidth billing method from pay-by-bandwidth to pay-by-traffic.
2.  [Convert the public IP address of the ECS instance to an EIP](../../../../../reseller.en-US/User Guide/Create an EIP/Convert an ECS public IP address to an EIP.md#).
3.  [Disassociate the EIP obtained in the previous step from the ECS instance](../../../../../reseller.en-US/User Guide/Disassociate an EIP from a cloud instance.md#).
4.  [Associate the EIP you purchased with the ECS instance](../../../../../reseller.en-US/User Guide/Associate an EIP with a cloud instance/Associate an EIP with an ECS instance.md#).

## How do I view my subscription instances in the same region? {#section_bud_chq_gek .section}

You can use the resource overview feature to view your subscription instances in the same region. For more information, see [View resource overview](../reseller.en-US/Tags & Resource Management /View resource overview.md#).

## How do I view subscription instances in all regions under my account? {#section_s5o_w6z_95z .section}

You can go to the renewal page to view subscription instances in all regions under your account.

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the top navigation bar, choose **Billing Management** \> **Renew**.

## When can I forcibly stop my ECS instance? What will the consequence be? {#section_nlp_9qg_6gq .section}

If you cannot stop an instance by shutting it down properly, you can forcibly stop it. Forcible stop is equivalent to a physical shutdown, and may cause data loss if data in the instance is not yet written to disks.

## Why can't I reactivate my ECS instance? {#section_vk6_sjc_agd .section}

You may fail to reactivate your ECS instance due to any of the following reasons:

-   Your account has overdue payments. Pay the outstanding bills and try again.
-   System is busy. Try again later.
-   Resources are sold out.

    **Note:** You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy4service.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.


## What is the AliVulfix process in an ECS instance? {#section_4ek_d0m_191 .section}

The AliVulfix process is an Alibaba Cloud Security program that detects vulnerabilities in ECS instances.

## How do I defend ECS instances against attacks? {#section_t6g_7b5_165 .section}

ECS instances use Alibaba Cloud Security to defend against DDoS attacks. CloudMonitor deployed on ECS instances can automatically detect attacks and scrub suspicious traffic. For high-volume attacks, Alibaba Cloud implements black hole filtering to protect your instances. To strengthen security protection, we recommend that you install security software and disable ports that are not commonly used.

## What security services does Alibaba Cloud provide? {#section_cxr_p7b_a9w .section}

Alibaba Cloud Security is powered by the robust data analysis capability of the Alibaba Cloud cloud computing platform to provide you with a comprehensive set of security services, such as security vulnerability detection, webpage trojan detection, host intrusion detection, and DDoS protection.

## After I renew a subscription ECS Linux instance that expires, I am still unable to access the website it hosts. What can I do? {#section_s8j_d1f_1u6 .section}

Problem description: The ECS instance is in the Stopped state after it expires. After you renew and start the instance, the website it hosts cannot be accessed.

Cause: This may be because the website service has not been started.

Solution:

1.  Connect to the ECS instance remotely and run the following command to check whether the website service has been started:

    ``` {#codeblock_72x_ahr_4k6}
    #netstat -nltp //Check whether port 80 on the ECS instance is being listened on.
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/130429/156896162641861_en-US.png)

2.  If no information about port 80 is displayed in the command output, the website service has not been started. Run a command to manually start the website service and relevant services.

    In Linux, websites are typically developed based on PHP and MySQL.

    -   In Apache, you only need to start the website service and MySQL.

        ``` {#codeblock_y5p_uic_anm}
        #/etc/init.d/httpd start          //Start the website service. This command is applicable to Apache.
        #/etc/init.d/mysqld start            //Start MySQL.
        ```

    -   In NGINX, you need to start the website service, PHP, and MySQL.

        ``` {#codeblock_jng_pj1_5zz}
        #/etc/init.d/nginx start          //Start the website service. This command is applicable to NGINX.
        #/etc/init.d/php-fpm start       //Start PHP.
        #/etc/init.d/mysqld start            //Start MySQL.
        ```

3.  Re-check whether the website service has been started.

    ``` {#codeblock_248_ghb_rjh}
    #netstat -nltp //Check whether port 80 on the ECS instance is being listened on.
    ```

4.  After the website service has been started, access the website again.

If the problem persists, submit a ticket.

## How do I check, partition, and format the data disks of a Linux instance? {#section_csf_vvp_2z1 .section}

You can run the df –h command to check the capacity and usage of disks, and run the fdisk –l command to view disk information. For details about how to partition and format disks in Linux instances, see [Format a data disk of a Linux instance](../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk of a Linux instance.md#).

## How do I upload files to a Linux instance? {#section_861_wjj_km6 .section}

You can use the FTP service to upload files to a Linux instance.

## How do I change the owner and owner group of directories and files on a Linux instance? {#section_kf0_kn1_74z .section}

If the file or directory permissions are not correctly configured on the Web server, a 403 error will occur when you access websites hosted on the instance. Therefore, before you adjust a file or directory, you must identify the identity under which the file or directory process is running.

You can run the ps and grep commands to query the identities under which processes are running.

You can run the ls –l command to query the owners and owner groups of files and directories.

To modify the permissions, run the chown command. For example, you can run the chown -R www.www /alidata/www/phpwind/ command to change the owner and owner group of all files and directories under directory /alidata/www/phpwind to account www.

## How do I update the software source of Linux instances? {#section_8jc_uw1_mjn .section}

You can use an automatic software source updating tool. For more information, see [Automatic source updating tool for Linux ECS](https://partners-intl.aliyun.com/help/faq-detail/41177.htm).

## How do I install a VNC server to access a Linux system by using a GUI? {#section_m4o_mku_bj2 .section}

For details, see [Install and run VNC Server on a Linux instance](https://partners-intl.aliyun.com/help/faq-detail/41181.htm).

## What limits apply to the transfer and change of public IP addresses of ECS instances? {#section_y49_iww_fvq .section}

The following limits apply to the transfer and change of public IP addresses of ECS instances:

-   In classic networks:
    -   You cannot transfer public IP addresses across accounts.
    -   The public IP address of an ECS instance is mutable only within 6 hours after the instance is created, and can be changed a maximum of 3 times. For more information, see [Change the public IP address of an ECS instance](../reseller.en-US/Network/Change IPv4 addresses/Change the public IP address of an ECS instance.md#).
    -   If Anti-DDoS Pro is deployed on your instance, you can change the IP address of an ECS instance a maximum of 10 times in the Anti-DDoS Pro console. For more information, see [Change ECS IP](../../../../../reseller.en-US/Anti-DDoS Pro Service/User Guide/Instance management/Change ECS IP.md#) of the Anti-DDoS Pro User Guide.
-   In VPCs:
    -   You cannot transfer public IP addresses or EIPs across accounts.
    -   If no public IP address is allocated to your instance, you can bind an EIP to the instance. You can replace the public IP address of your instance with an EIP.
    -   If a public IP address is allocated to your instance:
        -   This public IP address is mutable within 6 hours after the instance is created, and can be changed a maximum of 3 times. For more information, see [Change the public IP address of an ECS instance](../reseller.en-US/Network/Change IPv4 addresses/Change the public IP address of an ECS instance.md#).
        -   You can replace this public IP address by converting it to an EIP. For more information, see [Convert an ECS public IP address in a VPC to an Elastic IP Address](../reseller.en-US/Network/Change IPv4 addresses/Convert an ECS public IP address in a VPC to an Elastic IP Address.md#).

If you have further questions, submit a ticket.

## Can I access amazon.com from my ECS instance? {#section_q6i_bio_ba9 .section}

You can access amazon.com from your ECS instance if your ECS instance can connect to the public network properly.

## Why can't I access a website hosted outside China after I log on to my ECS instance? {#section_ags_ovh_bde .section}

You can access a website hosted outside China from your ECS instance only when the website complies with the local regulatory policies of the country or region where your instance is located. Make sure that your ECS instance can connect to the public network properly and that the website is compliant with the preceding local regulatory policies.

## I cannot purchase any more pay-as-you-go instances. What can I do? {#section_xt4_ax4_x66 .section}

If you have reached the maximum number of pay-as-you-go instances that you can purchase, you cannot purchase any more pay-as-you-go instances. For more information, see [Limits](../reseller.en-US/Product Introduction/Limits.md#section_tbg_zdx_wdb). You can log on to the ECS console and view your resource quotas on the Privileges & Quotas page. For more information, see [Manage privileges and quotas](../reseller.en-US/Tags & Resource Management /Manage privileges and quotas.md#).

## Are fees still incurred after a pay-as-you-go ECS instance is automatically stopped due to an overdue payment or is manually stopped? {#section_bll_9fl_9qs .section}

When the payment for a pay-as-you-go instance is overdue, the instance is automatically stopped and taken out of service.

You can stop a running pay-as-you-go instance in the ECS console or by calling the StopInstance operation. When the instance is stopped, its status changes to **Stopped**. Billing of a pay-as-you-go instance in the Stopped state depends on the instance network type.

-   VPC: You can enable the No Fees for Stopped Instances \(VPC-Connected\) feature. After the feature is enabled, pay-as-you-go instances in VPCs start being billed when they are created, stop being billed when they enter the **Stopped** state, and resume being billed when they are started again. With the No Fees for Stopped Instances \(VPC-Connected\) feature enabled, the vCPUs, memory resources, and public IP addresses of pay-as-you-go instances in VPCs will not incur any additional costs after the instances are stopped, but the disks will continue to be billed. For more information, see [No fees for stopped VPC instances](../reseller.en-US/Pricing/No fees for stopped VPC instances.md#).
-   Classic network: Pay-as-you-go instances in classic networks will continue to be billed even when they are in the **Stopped** state.

## The order fails to be placed when I change the billing method of my ECS instance from pay-as-you-go to subscription. What can I do? {#section_ye3_pyk_bzl .section}

Your order may fail to be placed due to any of the following reasons:

-   The instance is in a state that does not support changing billing methods.
-   The instance is scheduled for an automatic release at a specific point in time and does not support changing billing methods.
-   The instance is in the **Expired** state.
-   The instance information has changed.
-   A change order is not yet paid for the instance.

If you are prompted with any of the preceding error messages, adjust the instance accordingly.

## How long does it take to change the billing method after you pay for the order? {#section_07w_jp4_rlu .section}

After you pay for the order, it takes 1 to 4 seconds to change the billing method of up to 20 instances at a time. After the change, the billing method of the instance is changed to **Subscription** in the console.

## What can I do if the change from pay-as-you-go to subscription fails? {#section_ulz_fn2_oxb .section}

Submit a ticket.

## Will the bandwidth billing method change after I change from pay-as-you-go to subscription? {#section_4lm_u5o_2my .section}

No. You can only change the billing method of instances and disks. For information about how to change the bandwidth billing method, see [EN-US\_TP\_9642.md\#ChangeBilling](reseller.en-US/Instances/Change configurations/Overview of configuration changes.md#ChangeBilling).

## I have an unpaid order for changing the billing method of an instance from pay-as-you-go to subscription. If I upgrade the instance, will the order still be valid? {#section_tih_umb_qaz .section}

An order is created when you change the billing method of your instance from pay-as-you-go to subscription. You must complete the payment for this order for the change to take effect. If you upgrade the instance before the order is paid for, the order payment cannot be completed because the instance components change and the original order amount does not meet the requirements of the new billing method. If you still want to change the billing method, you must cancel the unpaid order and place a new order.

## What can I do if the change from subscription to pay-as-you-go fails? {#section_xqt_ua4_1cf .section}

The change from subscription to pay-as-you-go may fail due to any of the following reasons:

-   The instance is in a state that does not support changing billing methods.
-   The instance is in the **Expired** state.
-   The instance information has changed.

If you are prompted with any of the preceding error messages, adjust the instance accordingly. If this problem persists, submit a ticket.

## When I try to change the billing method of a disk in an ECS instance, an error message appears indicating that I have already changed the billing method three times. What does this mean? {#section_bxy_dkr_1f9 .section}

Each ECS instance can be downgraded a maximum of three times. Downgrade operations include instance specifications downgrades, bandwidth configuration downgrades, and the change of the disk billing method from subscription to pay-as-you-go.

## Why can't I change a pay-as-you-go instance to a subscription one? {#section_vlz_58s_9es .section}

To change the billing method for an ECS instance, ensure that the instance meet the following conditions:

## How do I view the expiration time of my subscription instances? {#section_8hf_t8x_5n3 .section}

You can log on to the ECS console and go to the Instances page. View the expiration time of your subscription instances in the **Billing Method** column.

**Note:** If the **Billing Method** column is not displayed, click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/130429/156896162753726_en-US.png) in the upper-right corner. In the dialog box that appears, select **Billing Method** and click **OK**.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/130429/156896162753728_en-US.png)

