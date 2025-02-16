---
title: AdExtensionAdditionalField Value Set - Campaign Management
ms.service: bing-ads-campaign-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Defines a list of optional ad extension properties that you can request when calling GetAdExtensionsAssociations and GetAdExtensionsByIds.
---
# AdExtensionAdditionalField Value Set - Campaign Management
Defines a list of optional ad extension properties that you can request when calling [GetAdExtensionsAssociations](getadextensionsassociations.md) and [GetAdExtensionsByIds](getadextensionsbyids.md). The additional field values enable you to get the latest features using the current version of Campaign Management API, and in the next version the corresponding properties will be included in the ad extension by default.  

> [!NOTE]
> This value set is reserved for future use.

## Syntax
```xml
<xs:simpleType name="AdExtensionAdditionalField" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Images" />
        <xs:enumeration value="DisplayText" />
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## <a name="values"></a>Values

|Value|Description|
|-----------|---------------|
|<a name="displaytext"></a>DisplayText|Request that the [DisplayText](imageadextension.md#displaytext) element be included within each returned [ImageAdExtension](imageadextension.md) object.|
|<a name="images"></a>Images|Request that the [Images](imageadextension.md#images) element be included within each returned [ImageAdExtension](imageadextension.md) object.|

## Requirements
Service: [CampaignManagementService.svc v13](https://campaign.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v13/CampaignManagementService.svc)  
Namespace: https\://bingads.microsoft.com/CampaignManagement/v13  

## Used By
[GetAdExtensionsAssociations](getadextensionsassociations.md)  
[GetAdExtensionsByIds](getadextensionsbyids.md)  
