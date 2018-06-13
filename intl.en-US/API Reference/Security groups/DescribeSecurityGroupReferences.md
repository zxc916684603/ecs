# DescribeSecurityGroupReferences {#DescribeSecurityGroupReferences .reference}

Queries whether a specified security group has been authorized by other security group or not.

## Description {#section_dcn_yyr_zdb .section}

When you call this interface, consider the following:

-   To authorize a security group includes the inbound rules authorization and the outbound rules authorization.

-   A maximum 100 entries of authorization record can be queried per invocation.

-   When you fail to delete one security group \([DeleteSecurityGroup](intl.en-US/API Reference/Security groups/DeleteSecurityGroup.md#)\), you can call this interface to make sure whether a specified security group has been authorized by other security group or not. If the security group to be deleted is authorized by another security groups, you must withdraw the authorization before the deletion action.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeSecurityGroupReferences.|
|SecurityGroupId.n|String|Yes|The ID of a security group. The value range of n is \[1, 10\].|
|RegionId|String|Yes|The region to where the security group belongs. You can call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|SecurityGroupReferences|[SecurityGroupReference](intl.en-US/API Reference/Data type/SecurityGroupReference.md#)|Information of the security group authorization.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeSecurityGroupReferences
&RegionId=cn-hangzhou
&SecurityGroupId. 1=sg-1133aa
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeSecurityGroupReferencesResponse>
    <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    <SecurityGroupReferences>
      <SecurityGroupReference>
        <SecurityGroupId>sg-1133aa</SecurityGroupId>
        <ReferencingSecurityGroups>
          <ReferencingSecurityGroup>
            <SecurityGroupId>sg-2255cc</SecurityGroupId>
            <AliUid>123</AliUid>
          </ReferencingSecurityGroup>
          <ReferencingSecurityGroup>
            <SecurityGroupId>sg-2255dd</SecurityGroupId>
            <AliUid>123</AliUid>
          </ReferencingSecurityGroup>
        </ReferencingSecurityGroups>
      </SecurityGroupReference>
    </SecurityGroupReferences>
</DescribeSecurityGroupReferencesResponse>
```

 **JSON format** 

```

    "RequestId": "CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    "SecurityGroupReferences":[
        
            "SecurityGroupId":"sg-1133aa",
            "SecurityReferencingGroups":[
                
                    "AliUid":123,
                    "SecurityGroupId":"sg-2255cc"
                
                
                    "AliUid":123,
                    "SecurityGroupId":"sg-2255dd"
                
            
        
    

```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message |HTTP status code |Meaning|
|:---------|:-------------|:----------------|:------|
|Abs.GroupNos.Malformed|The specified parameter SecurityGroupId is essential and size should less than 10.|400|You must specify the `SecurityGroupId.n` parameter. Or the `n` in the `SecurityGroupId.n` cannot exceed 10.|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|400|The specified security group ID does not exist.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|

