# DescribeZones {#DescribeZones .reference}

Describes the zones that are available to you in a specified region. For more information, see [Regions and zones](https://www.alibabacloud.com/help/doc-detail/40654.htm).

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: Description zones.|
|RegionId|String|Yes|The region ID. You can call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InstanceChargeType|String|No|Billing methods of the instance. For more information, see [Pricing overview](../../../../intl.en-US/Pricing/Pricing overview.md#). Optional values:-   PrePaid: Subscription.
-   PostPaid: Pay-As-You-Go.

Default value: PostPaid.|
|SpotStrategy|String|No|Sets your expected spot price for preemptible instances. This parameter takes effect when you set `InstanceChargeType` to `PostPaid`. For more information, see [Preemptible instance](../../../../intl.en-US/Product Introduction/Instance/Preemptible instance.md#). Optional values:-   NoSpot: Bids as a normal Pay-As-You-Go instance.
-   SpotWithPriceLimit: Sets a bidding price threshold for the spot instance.
-   SpotAsPriceGo: Sets a highest Pay-As-You-Go price by the bidding system automatically.

Default value: NoSpot.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|Zones|[ZoneType](intl.en-US/API Reference/Data type/ZoneType.md#)|A collection that contains `ZoneType` information.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeZones
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeZonesResponse>
    <Zones>
        <Zone>
            <AvailableResourceCreation>
                <ResourceTypes>Instance</ResourceTypes>
                <ResourceTypes>Disk</ResourceTypes>
            </AvailableResourceCreation>
            <LocalName></LocalName>
            <ZoneId>cn-hangzhou-d</ZoneId>
            <AvailableDiskCategories>
                <DiskCategories>cloud</DiskCategories>
            </AvailableDiskCategories>
        </Zone>
        <Zone>
            <AvailableResourceCreation>
                <ResourceTypes>Instance</ResourceTypes>
                <ResourceTypes>Disk</ResourceTypes>
            </AvailableResourceCreation>
            <LocalName></LocalName>
            <ZoneId>cn-hangzhou-b</ZoneId>
            <AvailableDiskCategories>
                <DiskCategories>cloud</DiskCategories>
            </AvailableDiskCategories>
        </Zone>
    </Zones>
    <RequestId>6DB97BCC-92BA-424D-A7C8-3F6486612BAE</RequestId>
</DescribeZonesResponse>
```

 **JSON format** 

```
{
  "RequestId": "A347EF0E-BBCC-4EFA-BD79-27AA3ACFD1BF",
  "Zones": {
    "Zone": [
      {
        "AvailableDiskCategories": {
          "DiskCategories": [
            "cloud"
          ]
        },
        "AvailableResourceCreation": {
          "ResourceTypes": [
            "Instance",
            "Disk"
          ]
        },
        "LocalName": "",
        "ZoneId": "cn-hangzhou-d"
      },
      {
        "AvailableDiskCategories": {
          "DiskCategories": [
            "cloud"
          ]
        },
        "AvailableResourceCreation": {
          "ResourceTypes": [
            "Instance",
            "Disk"
          ]
        },
        "LocalName": "",
        "ZoneId": "cn-hangzhou-b"
      }
    ]
  }
}
```

## Error codes {#ErrorCode .section}

All are common error codes. For more information, see [Common error codes](https://error-center.alibabacloud.com/status/product/Ecs).

