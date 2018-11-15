# Delete a tag {#concept_oqq_ztd_zdb .concept}

You can unbind a tag from the resource if the tag is no longer applicable to resource management. After a tag is unbound and is no longer bound to any other resource, the tag will be automatically deleted.

-   The Delete Tags function unbinds one or more tags from an instance at a time.

    **Note:** Currently, this function is only available for instances. It is unavailable for other resource types.

-   The Edit Tags function unbinds tags one by one.

    **Note:**  You can unbind 20 tags from a resource each time.


## Unbind tags from instances using the tag deletion function {#section_amn_vfj_zdb .section}

Currently, the Delete Tags function is only available for instances.

See the following steps to delete tags:

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  Click Instance in the left-side navigation pane.
3.  Select a region.
4.  Select the instance\(s\) from which you want to unbind tags in the instance list.

    **Note:** You can also filter instances by tag and select the expected instance.

5.  Choose** More** \> **Delete Tags**.
6.  In the Delete Tags dialog box, enter the **Tag Key** of the tags you want to unbind.
7.  Click **OK** to complete tag unbinding.

To check whether the tags are successfully unbound, use the Edit Tags function of the instance or click Tags in the left-side navigation pane of the ECS console.

## Unbind tags from resources using the tag edit function {#section_fmn_vfj_zdb .section}

The Edit Tags function unbinds one or more tags from a resource.

See the following steps to unbind tags:

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, select the resource type for the unbinding operation, such as Instance, Cloud Disks, Snapshots, Images, or Security Groups.

    **Note:** The block storage function is now in beta. For more information, see [Access to block storage FAQ](https://partners-intl.aliyun.com/help/faq-detail/53820.htm)Learn more.

3.  Select a region.
4.  In the resource list, select the resource from which you want to unbind tags.

    **Note:** You can also filter resources by tag and select the expected resource.

5.  Click **Edit Tags** at the bottom of the resource list.
6.  In the Edit Tags dialog box, click the deletion icon next to a tag.
7.  Click **Confirm** to complete tag unbinding.

To check whether the tags are successfully unbound, use the Edit Tags function of the resource or click **Tags** in the left-side navigation pane of the ECS console.

