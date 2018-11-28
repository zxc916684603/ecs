# API计费 {#ApiBilling .reference}

## 计费 {#Billing .section}

注意，这句需要区分专有云和公共云：会涉及到资源计费，建议您提前了解云服务器ECS的计费方式。更多详情，请参阅 [计费概述](../../../../cn.zh-CN/产品定价/计费概述.md#)。

注意，这句需要区分专有云和公共云：更换计费方式后，默认自动扣费。您需要确保账户余额充足，否则会生成异常订单，此时只能作废订单。如果您的账户余额不足，可以将参数 `AutoPay` 置为 `false`，此时会生成正常的未支付订单，您可以登录 [ECS管理控制台](https://ecs.console.aliyun.com/) 支付。

如果您的专有网络VPC类型实例开启了VPC内实例停机不收费功能后，为防止地域内ECS资源不足而引起无法重启实例，您需要在调用接口前关闭停机不收费功能。更多详情，请参阅 [StopInstance](cn.zh-CN/API参考/实例/StopInstance.md#)。

## 快照 {#section_yxk_nxx_52b .section}

自2017年3月28日起，ECS快照正式商业化并纳入收费服务，计费详情请参阅 [../../../../dita-oss-bucket/SP\_2/DNA0011810291/ZH-CN\_TP\_9597.md\#](../../../../cn.zh-CN/隐藏/快照计费.md#)。关于快照收费的更多信息，请参阅 [快照商业化FAQ](https://help.aliyun.com/document_detail/52045.html)。

