---
title: CoOpSetting Data Object - Campaign Management
ms.service: bing-ads-campaign-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Defines the ad group level settings for feed-based Microsoft Shopping Campaigns.
---
# CoOpSetting Data Object - Campaign Management
Defines the ad group level settings for feed-based Microsoft Shopping Campaigns.

> [!NOTE]
> This setting is only applicable for ad groups in Microsoft Shopping Campaigns that are setup for Sponsored Products. Sponsored Products are only available in the United States and are currently under open beta.

## Syntax
```xml
<xs:complexType name="CoOpSetting" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Setting">
      <xs:sequence>
        <xs:element minOccurs="0" name="BidBoostValue" nillable="true" type="xs:double" />
        <xs:element minOccurs="0" name="BidMaxValue" nillable="true" type="xs:double" />
        <xs:element minOccurs="0" name="BidOption" nillable="true" type="tns:BidOption" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="bidboostvalue"></a>BidBoostValue|The default bid boost percentage that you'll see in the Microsoft Advertising web application for new product groups.<br/><br/>This ad group level target setting is not used directly in the auction. The product group bids are used to boost your partner's bid.<br/><br/>**Add:** Required if the [BidOption](#bidoption) is set to BidBoost, and otherwise you may not set this element.<br/>**Update:** Required if the [BidOption](#bidoption) is set to BidBoost, and otherwise you may not set this element.|**double**|
|<a name="bidmaxvalue"></a>BidMaxValue|The flat amount of your Sponsored Products bid.<br/><br/>**Add:** Required if the [BidOption](#bidoption) is set to BidBoost, and otherwise you may not set this element.<br/>**Update:** Optional if the [BidOption](#bidoption) is set to BidBoost, and otherwise you may not set this element.|**double**|
|<a name="bidoption"></a>BidOption|Determines whether or not to amplify your partner's bid.<br/><br/>A bid value ad group allows you to bid on products that your merchandising partner doesn't target. If this element is set to BidValue, the auction will use use a [FixedBid](fixedbid.md) for product groups that have a [CriterionBid](biddableadgroupcriterion.md#criterionbid).<br/><br/>A bid boost allows you to amplify your partner's bid. If this element is set to BidBoost, the auction will use use a [BidMultiplier](bidmultiplier.md) for product groups that have a [CriterionBid](biddableadgroupcriterion.md#criterionbid). You should only use BidBoost if your partner uses BidValue.<br/><br/>**Add:** If this element is not set, the default Sponsored Products bidding option for the ad group is BidValue.<br/>**Update:** Read-only. If you attempt to change the previous bid option an error will be returned.|[BidOption](bidoption.md)|

The [CoOpSetting](coopsetting.md) object has [Inherited Elements](#inheritedelements).

## <a name="inheritedelements"></a>Inherited Elements

### <a name="inheritedelementssetting"></a>Inherited Elements from Setting
The [CoOpSetting](coopsetting.md) object derives from the [Setting](setting.md) object, and inherits the following elements. The descriptions below are specific to [CoOpSetting](coopsetting.md), and might not apply to other objects that inherit the same elements from the [Setting](setting.md) object.  

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="type"></a>Type|The type of the setting. This value is *CoOp* when you retrieve a Sponsored Products setting. For more information about setting types, see the [Setting Data Object Remarks](setting.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|**string**|

## Requirements
Service: [CampaignManagementService.svc v12](https://campaign.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v12/CampaignManagementService.svc)  
Namespace: https\://bingads.microsoft.com/CampaignManagement/v12  

