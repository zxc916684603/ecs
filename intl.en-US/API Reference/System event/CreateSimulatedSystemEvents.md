# CreateSimulatedSystemEvents {#CreateSimulatedSystemEvents .reference}

Schedules simulated system events for one or more Elastic Compute Service \(ECS\) instances. The system events that are simulated do not occur in the real system and the simulation does not affect ECS instances.

## Description {#section_hbw_vnm_x2b .section}

-   You can view the scheduled system events in the ECS console, [ECS API](reseller.en-US/API Reference/Operations and monitoring/DescribeInstanceHistoryEvents.md#), or cloud monitoring service.

-   The following table describes the life cycle of a simulated system event.

    |Name|Description|Status|
    |:---|:----------|:-----|
    |`Scheduled`|The simulated system event has been scheduled.|The status for the simulated system event is automatically changed to `Scheduled` after the schedule.|
    |`Executed`|The simulated system event has been executed.|The status for the simulated system event is automatically changed to `Executed` at the scheduled time specified by the NotBefore parameter if no manual intervention is involved.|
    |`Canceled`|The simulated system event has been canceled.|The status for the simulated system event is changed to `Canceled` if you cancel the event by making a [CancelSimulatedSystemEvents](reseller.en-US/API Reference/Operations and monitoring/CancelSimulatedSystemEvents.md#) request.|
    |`Avoided`|The simulated system event has been avoided.|The status for the simulated system event of maintenance-triggered instance restart can be changed to `Avoided` if you [restart the instance](reseller.en-US/API Reference/Instances/RebootInstance.md#) before the scheduled time of the simulated system event. The maintenance-triggered instance restart is indicated by the SystemMaintenance.Reboot value.|


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The operation that you want to perform. Value: CreateSimulatedSystemEvents.|
|RegionId|String|Yes|The ID of the region.For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InstanceId.N|String|Yes|The IDs of one or more ECS instances. Value range of N: \[1, 100\]. The ECS IDs must be displayed in a repeated list format.|
|EventType|String|Yes|The type of a system event. Optional values:-   SystemMaintenance.Reboot: The instance restarts because of maintenance.
-   SystemFailure.Reboot: The instance restarts due to a system failure.
-   InstanceFailure.Reboot: The instance restarts due to an instance failure.

|
|NotBefore|String|Yes|The start time of the scheduled event execution time.The time format follows the [ISO8601](../reseller.en-US/API Reference/Appendix/ISO 8601 Time Format.md#) standard, and the UTC time is used. The format is yyyy-MM-ddTHH:mm:ssZ.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|EventIdSet|List of event IDs \(`EventId`\)|The list of simulated event IDs.|

## Examples { .section}

**Request example**

```
https://ecs.aliyuncs.com/?Action=CreateSimulatedSystemEvents
&RegionId=cn-hangzhou
&InstanceId. 1=i-instance1
&InstanceId. 2=i-instance1
&EventType=SystemMaintenance.Reboot
&NotBefore=2018-12-01T06:32:31Z
&<Common Request Parameters>
```

**Response example**

**XML format**

```
<CreateSimulatedSystemEventsResponse>
	<EventIdSet>
		<EventId>e-xhskHun1256xxxx</EventId>
		<EventId>e-xhskHun1257xxxx</EventId>
	</EventIdSet>
        <RequestId>E69EF3CC-94CD-42E7-8926-F133B86387C0</RequestId>
</CreateSimulatedSystemEventsResponse>
```

**JSON format**

```
{
    "RequestId":"E69EF3CC-94CD-42E7-8926-F133B86387C0",
	"EventIdSet":{
		"EventId": "e-xhskHun1256xxxx",
		"EventId": "e-xhskHun1257xxxx"
	}
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|InvalidNotBefore.Passed|The NotBefore of system event has passed.|400|The specified value for the NotBefore parameter is later than the current time.|
|InvalidInstanceId.NotFound|Cannot find InstanceId.|400|The specified instance ID does not exist.|
|SimulatedEventLimitExceeded|The amount of active simulated system event exceeds limit.|400|The amount of active simulated system events has exceeded the limit in the region.|
|InstanceIdLimitExceeded|The amount of InstanceId specified exceeds limit.|400|The number of specified instance IDs cannot exceed 100 at a time.|
|MissingParameter|The input parameter that is mandatory for processing this request is not supplied.|404|The value for a required parameter is not specified.|

