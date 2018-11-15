# ImageType {#ImageType .reference}

The data types for image information.

## Node Name {#section_pp3_yjp_ydb .section}

Image

## Node name {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|ImageId|String|ID of the image.|
|ImageVersion|String|Version of the image.|
|OSType|String|Platform type of the image system. Possible values:-   Windows
-   Linux

|
|Platform|String|OS platform.|
|Architecture|String|Image system. Possible values: i386 | x86\_64.|
|ImageName|String|Name of the image.|
|Description|String|Description|
|Size|Integer|Size of the image.|
|ImageOwnerAlias|String|Alias of the image owner. Possible values:-   system: Public images provided by Alibaba Cloud system.
-   self: Custom images.
-   others: Images shared by other users.
-   marketplace: Images available on the image market.

|
|Osname|String|Display name of the OS.|
|DiskDeviceMappings|[DiskDeviceMapping](intl.en-US/API Reference/Data type/DiskDeviceMapping.md#)|Description of the system with disks and snapshots under an image.|
|ProductCode|String|Product code of the image on the image market.|
|IsSubscribed|Boolean|Whether the user has subscribed to the terms of service for the image product corresponding to the ProductCode. Possible values:-   true: Indicates subscription has been made.
-   false: Indicates subscription has not been made.

|
|Progress|String|Progress of image creation, presented in percentages.|
|Status|String|Status of the image. Possible values:-   Unavailable
-   Available
-   Creating
-   CreateFailed

|
|CreationTime|String|Time of creation. It is represented according to ISO8601. UTC time is used. Format: YYYY-MM-DDThh:mmZ.|
|Usage|String|Resource type with reference relationships: instance/none.|
|IsCopied|String|Is it a copied mirror. Possible values: true | false.|

