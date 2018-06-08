# PriceType {#PriceType .reference}

The price information of a specified resource.

## Node Name {#section_a2r_ty5_ydb .section}

Price

## Subnode {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|Currency|String| The unit of currency.|
|OriginalPrice|Double| The original price.|
|DiscountPrice|Double|The trade discount.|
|TradePrice|Double|The trading price, equal to the value of OriginalPrice minus the value of DiscountPrice.|

