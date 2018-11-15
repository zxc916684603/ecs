# InstanceAttributesType {#InstanceAttributesType .reference}

Lists the ECS instance attributes.

## Node {#section_nhx_2kp_ydb .section}

Depends on the interface.

## Subnodes {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|InstanceId|String|Instance ID.|
|InstanceName|String|Instance name.|
|Description|String|Instance description.|
|ImageId|String|ID of the image that is running in the instance.|
|RegionId|String|ID of the region where the instance belongs.|
|ZoneId|String|Zone ID of the zone where the ENS instance is located.|
|Cpu|Integer|Number of vCPU.|
|GPUSpec|String|GPU processor type of the instance.|
|GPUAmount|Integer|GPU processor number of the instance.|
|Memory|Float|Memory size in GiB.|
|InstanceType|String|Instance type.|
|InstanceTypeFamily|String|Instance type family|
|HostName|String|Instance host name.|
|SerialNumber|String|Instance serial number.|
|Status|String|Instance status.|
|SecurityGroupIds|[SecurityGroupIdSetType](reseller.en-US/API Reference/Data type/SecurityGroupIdSetType.md#)|Security groups that manage the specified instance.|
|PublicIpAddress|[IpAddressSetType](reseller.en-US/API Reference/Data type/IpAddressSetType.md#)|Public IP address of the instance.|
|InternetMaxBandwidthIn|Integer|Maximum incoming bandwidth from the internet network.|
|InternetMaxBandwidthOut|Integer|Maximum outgoing bandwidth to the internet network.|
|InternetChargeType|String|The billing method of the network bandwidth. Possible values:-   PayByTraffic: You are billed based on the traffic.

|
|CreationTime|String|Instance creation time. The time format follows the [ISO8601](../reseller.en-US/API Reference/Appendix/ISO 8601 Time Format.md#) standard, and the UTC time is used. The format is yyyy-MM-ddTHH:mm:ssZ.|
|InstanceNetworkType|String|Network type of the instance. Possible values: Classic | Vpc|
|VpcAttributes |[VpcAttributesType](reseller.en-US/API Reference/Data type/VpcAttributesType.md#)|VPC related attributes of an ECS instance.|
|EipAddress|[EipAddressAssociateType](reseller.en-US/API Reference/Data type/EipAddressAssociateType.md#)|EIP binding information.|
|InnerIpAddress|[IpAddressSetType](reseller.en-US/API Reference/Data type/IpAddressSetType.md#)|Intranet IP address.|
|OperationLocks|[OperationLocksType](reseller.en-US/API Reference/Data type/OperationLocksType.md#)|Reason why an instance is locked.|
|InstanceChargeType |String|Instance billing method. Possible values:-   PrePaid: Subscription.
-   PostPaid: Pay-As-You-Go.

|
|SaleCycle|String|The billing cycle selected for a Subscription instance. Optional values: week | month | year.|
|SpotPriceLimit|Float|The hourly price threshold for a preemptible instance, and it takes effect only when parameter `SpotStrategy=SpotWithPriceLimit`. Three decimal places are allowed at most.|
|SpotStrategy|String|The spot price you are willing to accept for preemptible instances. Possible values:-   NoSpot: A normal Pay-As-You-Go instance.
-   SpotWithPriceLimit: Sets the maximum price for a spot instance.
-   SpotAsPriceGo: A price that is based on the highest Pay-As-You-Go instance.

Default value: NoSpot.|
|DeviceAvailable|Boolean|Whether a new disk can attach to the instance or not.|
|StoppedMode|String|Whether a VPC-Connected ECS instance is charged after it is stopped or not. Possible values:-   KeepCharging: You are billed after the ECS instance is stopped, and its resource and Internet IP address are reserved.
-   StopCharging: You are not billed after the ECS instance is stopped, and its resource and Internet IP address are not reserved. You may be unable to restart the instance.
-   Not-applicable: The instance is not applicable for using the StoppedMode parameter.

|
|DeploymentSetId|String|Deployment set ID.|
|NetworkInterfaces|[NetworkInterfaceType](reseller.en-US/API Reference/Data type/NetworkInterfaceType.md#)|The ENI related information.|
|IoOptimized|Boolean |Whether an instance is I/O optimized or not.|
|ExpiredTime|String|Time of expiration. The time format follows the [ISO8601](../reseller.en-US/API Reference/Appendix/ISO 8601 Time Format.md#) standard, and the UTC time is used. The format is yyyy-MM-ddTHH:mm:ssZ.|
|KeyPairName|String|SSH key pair name.|

