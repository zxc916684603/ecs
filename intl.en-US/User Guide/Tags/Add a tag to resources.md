# Add a tag to resources {#concept_a5f_p2j_zdb .concept}

If your account maintains various types of resources that are associated with each other in different ways, you can bind tags to the resources to categorize and manage the resources in a unified manner.

You can bind 20 tags to a resource at most. You can bind/unbind 20 tags at most for the resource each time.

Take the following steps to bind resources with tags:

1.  Log on to the[ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  Select the resource type in the left-side navigation bar for the binding operation, such as Instance, Cloud Disks, Snapshot, Image, and Security Groups.
3.  Select a region.
4.  Select the resources in the resource list to bind tags.
5.  Click Edit Tags at the bottom of the resource list.

    **Note:** Choose **More** \> **Edit Tags at the bottom of the resource list if the selected resources are Instance.** .

6.  In the edit label dialog box,
    -   If the selected resource has already been created a label, click the existing label, and select the available labels.
    -   Click **Create** and set Key and Value if no tags are available for the selected resource: Note when entering:
        -   Key is mandatory whereas Value is optional.
        -   Key cannot start with aliyun, http://, or https://. The key is case-insensitive and can contain up to 64 characters.
        -   Value cannot start with http:// or https://. The value is case-insensitive and can contain up to 128 characters. It can be empty.
        -   Any tag Key of a resource must be unique. A tag with the same key as an existing one will be overwritten.
        -   Available Tags and Create are grayed out if the selected resources are already bound with 20 tags. You need to unbind some tags before binding new tags.
7.  Click **Confirm**.

To check if tags are successfully bound, use the Edit Tags function of the resource or click Tags in the left-side navigation bar of the ECS console.  You can click Tags with a tag symbol at the top of the resource list to filter resources.

