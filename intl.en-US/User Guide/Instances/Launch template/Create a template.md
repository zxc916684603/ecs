# Create a template {#concept_pzl_ww5_xdb .concept}

You can create a template using the following methods:

-   If you do not want to create instances at this time, you can still [Create a template in the ECS console](#console) create templates using the ECS console, and then create instances using your required template in one click when needed.

-   If you want to create an instance and save its configuration information, [Create a template on the ECS buy page](#commonbuy) go to the ECS buy page to create templates.


**Note:** 

-   In each region, one user account can only create a maximum of 30 launch templates.
-   All parameters are optional when you create a template using the ECS console.  However, if the template that you want to use to create an instance does not have all required parameters \(such as an image\), then you must specify the required parameters at instance creation.
-   A template cannot be modified once you have created it.

## Create a template in the ECS console {#console .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, select **Launch Template**, and then click **Create Template**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13805/5347_en-US.png)

3.  Go to the Launch Template page and complete the basic configurations and advanced configurations.

    **Note:** During your first template creation, the **Clone Template** area is unavailable. If you have already created templates, you can select an existing template, and version, and then modify its configurations.

4.  On the Confirm Configuration page, enter a template name and description, and then click **Create Launch Template**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13805/5348_en-US.png)

    **Note:** All parameters are optional when you create a template. On the Confirm Configuration page, we recommend that you configure the required parameters so that you can create instances in one click later. You can also leave the parameter settings unchanged.

5.  In the Activated dialog box, click **View Template** to view the template you have created.

## Create a template on the ECS buy page {#commonbuy .section}

1.  Go to the [ECS product details page](https://www.alibabacloud.com/product/ecs), and then click **Buy Now**.
2.  On the ECS buy page, configure the parameters.
3.  On the Preview page, click **Save as launch template**.
4.  In the dialog box that appears, select **Create Template**, enter a template name and description, and then click **Save**.
5.  In the Activated dialog box, click **View Template** to view the template you have created.

