# Import an SSH key pair {#concept_hvw_wj1_ydb .concept}

If you prefer to use another key generation tool, you can use it to generate an RSA key pair and then import its public key into Alibaba Cloud. See [SSH key pairs](../intl.en-US/Product Introduction/Network & Security/SSH key pairs.md#) for the supported types of imported key pairs.

**Note:** To guarantee your instance security, keep the private key of the key pair secure and do not import the private key to Alibaba Cloud.

To import an SSH key pair, you must have a key pair that has been generated using another tool. The public key to be imported into Alibaba Cloud must be Base64-encoded.

To import an SSH key pair, follow these steps.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  On the Key Pair page, click **Create Key Pair**.
4.  On the Create Key Pair page, enter a name for the key pair, and select **Import an Existing Key Pair**. **And then, Enter the public key** Enter the public key.

    **Note:** The specified key pair name must not be the same with that of an existing key pair or a key pair that was deleted when it was still bound to an instance. Otherwise, an error message “The key pair already exists.” will appear.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9729/4670_en-US.png)

5.  Click **OK**.

After creation, you can view the information, including **Key Pair Name** and **Key Pair Fingerprint**, in the key pair list.

