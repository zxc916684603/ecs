# InstanceMonitorDataType {#InstanceMonitorDataType .reference}

Type of instance metric data.

## Node {#section_tlx_qkp_ydb .section}

InstanceMonitorData

## Subnode {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|InstanceId|String|ID of the instance.|
|CPU|Integer|CPU usage, measured in percentages \(%\).|
|IntranetRX|Integer|Intranet traffic received by the instance, measured in kbits.|
|IntranetTX|Integer|Intranet traffic sent by the instance, measured in kbits.|
|IntranetBandwidth|Integer|Intranet bandwidth of the instance, network traffic per unit time, measured in kbits/s.|
|InternetRX|Integer|Internet traffic received by the instance, measured in kbits.|
|InternetTX|Integer|Internet traffic sent by the instance, measured in kbits.|
|InternetBandwidth|Integer|Internet bandwidth of the instance, network traffic per unit time, measured in kbits/s.|
|IOPSRead|Integer|System disk IO reads, measured in /s.|
|IOPSWrite|Integer|System disk IO writes, measured in /s.|
|BPSRead|Integer|System disk read bandwidth, measured in Byte/s.|
|BPSWrite|Integer|System disk write bandwidth, measured in Byte/s.|
|TimeStamp|String|Time of the traffic query, which is presented according to [ISO8601](intl.en-US/API Reference/Appendix/ISO 8601 Time Format.md#), and UTC time is used. The format is YYYY-MM-DDThh:mmZ.|

