# Tag overview {#concept_jzp_qtd_zdb .concept}

Tags can be used to identify resources and user groups. With tags, enterprises and individuals can categorize their ECS resources to make it easier to search and aggregate resources. ECS allows you to add tags and attach them to resources such as instances, snapshots, images, security groups, ENIs, dedicated hosts, SSH key pairs, launch templates, and block storage devices such as disks and Shared Block Storage devices.

## Scenarios {#section_ic2_gkw_wgb .section}

Tags can be used to categorize and manage ECS resources by group to help search for and perform batch operations on resources. For example:

-   You can attach different tags to specific environments such as production and test environments, operating systems such as Windows and Linux, or mobile platforms such as iOS and Android. Create a tag named `Test:Server-Windows` and attach it to all the ECS instances in the test environment. You can easily locate these resources through the tag and perform batch operations such as changing the image for application deployment, upgrading patches, and adding security group rules for network access control.
-   You can add tags such as `FinanceDept:FinanceJoshua` to groups, projects, and departments in team or project management to implement group authorization or mutual authorization. For more information, see [Use tags to authorize ECS instances by group](../../../../reseller.en-US/Best Practices/Use tags to authorize ECS instances by group.md#).

## Limits {#section_rpy_vzb_x8o .section}

-   Each tag has a key-value pair.
-   Each ECS instance can have up to 20 tags attached. A single operation can attach or detach a maximum of 20 tags at a time.
-   Each resource tag key must be unique. If a new tag has the same key as an existing tag, the new tag will overwrite the existing tag.
-   Tag information is not shared across regions. For example, tags created in the China \(Hangzhou\) region are not visible to the China \(Shanghai\) region.
-   When you detach a tag that is not attached to any other resources, the tag will be automatically deleted when it is detached.

## Operations {#section_izk_m6g_dmz .section}

-   [EN-US\_TP\_9742.md\#](reseller.en-US/Tags & Resource Management /Tags/Add a tag to resources.md#)
-   [EN-US\_TP\_9742.md\#](reseller.en-US/Tags & Resource Management /Tags/Add a tag to resources.md#)
-   [Filter resources by tags](reseller.en-US/Tags & Resource Management /Tags/Filter resources by tags.md#)

## API operations {#section_8pu_f96_07f .section}

-   [../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_136258.md\#](../../../../reseller.en-US/API Reference/Tags/TagResources.md#): creates tags and attaches them to specified ECS resources.
-   [ListTagResources](../../../../reseller.en-US/API Reference/Tags/ListTagResources.md#): queries tags that are attached to one or more ECS resources.
-   [UntagResources](../../../../reseller.en-US/API Reference/Tags/UntagResources.md#): detaches and deletes tags from specified ECS resources.

