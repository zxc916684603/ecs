# Create an SSH key pair {#concept_wy4_th1_ydb .concept}

## Limits {#section_odb_g31_ydb .section}

-   [../../../../dita-oss-bucket/SP\_2/DNA0011858383/EN-US\_TP\_9570.md\#](../../../../intl.en-US/Product Introduction/Network and security/SSH key pairs.md#)The SSH key pair, abbreviated as key pair, applies to Linux instances only.
-   Alibaba Cloud only supports the creation of 2048-bit RSA key pairs.
    -   Alibaba Cloud holds the public key of the key pair.
    -   After creating the key pair, you must save and keep the private key of the key pair for further use.
    -   The private key follows the unencrypted PEM-encoded `PKCS#8` format.
-   An Alibaba Cloud account can have a maximum of 500 key pairs per region.

## Create an SSH key pair {#section_f5c_h31_ydb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  In the left-side navigation pane, choose **Networks & Security \> Key Pairs**.
4.  On the  Key Pairs page, select a region, and click**Create Key Pair**.
5.  在 Create Key Pair  enter a name for the key pair, and select **Automatically Create a Key Pair**.

    **Note:** The specified key pair name must be unique. It must not match with the existing key pair or a key pair that was deleted when it was still bound to an instance.  Otherwise, an error message “The key pair already exists” appears.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9728/4669_en-US.png)

6.  Click **OK** to create a key pair.

    **Note:** After a key pair is created, you must download and save the private key for further use.  If you do not have the private key, you cannot log on to  The ECS instance.


After creating the key pair, you can view the information, including  **Key Pair Name** and **Key Pair Fingerprint** in the key pair list.

## Follow-up operations {#section_nn4_5j1_ydb .section}

After creating an SSH key pair, you can bind or unbind it to an ECS instance [EN-US\_TP\_9730.md\#](intl.en-US/User Guide/Key pairs/Bind or unbind an SSH key pair.md#).

