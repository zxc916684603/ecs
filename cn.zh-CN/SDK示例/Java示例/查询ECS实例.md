# 查询ECS实例 {#task_1926000 .task}

本文介绍了如何通过阿里云ECS Java SDK调用DescribeInstances根据条件筛选ECS实例。

您必须至少创建了一台ECS实例。详细步骤请参见[批量创建ECS实例](cn.zh-CN/SDK示例/Java示例/创建ECS实例/批量创建ECS实例.md#)。

查询ECS实例适用于在众多实例中快速筛选出需要操作的实例的所需信息，例如：

-   在根据实例ID修改公网带宽前，根据实例计费方式、运行状态、公网带宽计费方式等筛选出符合条件的ECS实例。
-   在更新实例上部署的应用前，查询所有使用了相同镜像的ECS实例。

## 代码示例 {#section_fzh_p23_a2c .section}

以下代码适用于查询中国杭州地域下公网带宽采用按流量计费、实例计费方式采用按量付费、网络类型采用专有网络VPC的ECS实例 ：

``` {#codeblock_gad_swb_020}
import com.aliyuncs.DefaultAcsClient;
import com.aliyuncs.IAcsClient;
import com.aliyuncs.exceptions.ClientException;
import com.aliyuncs.exceptions.ServerException;
import com.aliyuncs.profile.DefaultProfile;
import java.util.*;
import com.aliyuncs.ecs.model.v20140526.*;

public class DescribeInstances {

    public static void main(String[] args) {
        // 创建DefaultAcsClient实例并初始化。
        DefaultProfile profile = DefaultProfile.getProfile("cn-hangzhou", "<yourAccessKeyId>", "<yourAccessSecret>");
        IAcsClient client = new DefaultAcsClient(profile);

        // 创建API请求并设置参数。
        DescribeInstancesRequest request = new DescribeInstancesRequest();
        request.setRegionId("cn-hangzhou");
        request.setInstanceNetworkType("vpc");
        request.setInstanceChargeType("PostPaid");
        request.setInternetChargeType("PayByTraffic");
        request.setPageSize(10);

        try {
        // 发起请求并处理应答或异常。
            DescribeInstancesResponse response = client.getAcsResponse(request);
        for (DescribeInstancesResponse.Instance instance:response.getInstances()) 
            {
                 System.out.println(instance.getImageId());
                 System.out.println(instance.getInstanceId());
                 System.out.println(instance.getPublicIpAddress());
             }
        } catch (ServerException e) {
            e.printStackTrace();
        } catch (ClientException e) {
            System.out.println("ErrCode:" + e.getErrCode());
            System.out.println("ErrMsg:" + e.getErrMsg());
            System.out.println("RequestId:" + e.getRequestId());
        }

    }
}
```

由于以上代码指定获取镜像ID、实例ID以及公网IP地址，则实际返回结果为：

``` {#codeblock_7el_lmd_lm7}
i-bp1gvi17n5p8hav0i***
[47.97.***.21]
ubuntu_16_04_64_20G_alibase_20190620.vhd
i-bp1gc5z6103qs2t40***
[47.99.***.82]
centos_7_06_64_20G_alibase_20190711.vhd
```

**相关文档**  


[DescribeInstances](../../../../cn.zh-CN/API参考/实例/DescribeInstances.md#)

