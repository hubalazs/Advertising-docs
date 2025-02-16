---
title: ResponsiveAd Data Object - Campaign Management
ms.service: bing-ads-campaign-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: A responsive ad format for Audience ads in the Microsoft Audience Network.
---
# ResponsiveAd Data Object - Campaign Management
A responsive ad format for Audience ads in the Microsoft Audience Network.

Responsive ads automatically adjust to accommodate the sizes and shapes of audience ad formats. These ads work best with informative text rather than calls to action.

> [!NOTE]
> Not everyone is enabled for Audience campaigns in the Microsoft Audience Network yet. If you don't, don't worry. It's coming soon. 

> [!NOTE]
> Duplicate responsive ads are allowed in the same ad group. 

## Syntax
```xml
<xs:complexType name="ResponsiveAd" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Ad">
      <xs:sequence>
        <xs:element minOccurs="0" name="BusinessName" nillable="true" type="xs:string" />
        <xs:element minOccurs="0" name="CallToAction" nillable="true" type="tns:CallToAction" />
        <xs:element minOccurs="0" name="Headline" nillable="true" type="xs:string" />
        <xs:element minOccurs="0" name="Images" nillable="true" type="tns:ArrayOfAssetLink">
          <xs:annotation>
            <xs:appinfo>
              <DefaultValue EmitDefaultValue="false" xmlns="http://schemas.microsoft.com/2003/10/Serialization/" />
            </xs:appinfo>
          </xs:annotation>
        </xs:element>
        <xs:element minOccurs="0" name="LandscapeImageMediaId" nillable="true" type="xs:long" />
        <xs:element minOccurs="0" name="LandscapeLogoMediaId" nillable="true" type="xs:long" />
        <xs:element minOccurs="0" name="LongHeadline" nillable="true" type="xs:string" />
        <xs:element minOccurs="0" name="SquareImageMediaId" nillable="true" type="xs:long" />
        <xs:element minOccurs="0" name="SquareLogoMediaId" nillable="true" type="xs:long" />
        <xs:element minOccurs="0" name="Text" nillable="true" type="xs:string" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="businessname"></a>BusinessName|The name of the business.<br/><br/>Depending on your audience ad's placement, your business's name may appear in your ad.<br/><br/>The length of the string is limited to 25 characters.<br/><br/>**Add:** Required<br/>**Update:** Optional. If no value is set for the update, this setting is not changed.|**string**|
|<a name="calltoaction"></a>CallToAction|A brief, punchy reason for customers to click your ad right now.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[CallToAction](calltoaction.md)|
|<a name="headline"></a>Headline|This is one of two possible headlines that could appear in your audience ads.<br/><br/>Because audience ads are responsive, we require multiple headlines so they can flexibly serve across a variety of publishers and placements.<br/><br/>The length of the string is limited to 25 characters.<br/><br/>**Add:** Required<br/>**Update:** Optional. If no value is set for the update, this setting is not changed.|**string**|
|<a name="images"></a>Images|Because audience ads are responsive, you can create multiple image assets with different sizes and aspect ratios so they can flexibly display across a variety of publishers and placements.<br/><br/>Include one or more [AssetLink](assetlink.md) objects that each contain an [ImageAsset](imageasset.md) with [SubType](imageasset.md#subtype) and crop settings that match the desired aspect ratio. If this element is set (not null), then [LandscapeImageMediaId](#landscapeimagemediaid) and [SquareImageMediaId](#squareimagemediaid) are both ignored. For more information see the [remarks](#remarks) below.<br/><br/>**Add:** Required if [LandscapeImageMediaId](#landscapeimagemediaid) is not set.<br/>**Update:** Optional. If no value is set for the update, this setting is not changed.|[AssetLink](assetlink.md) array|
|<a name="landscapeimagemediaid"></a>LandscapeImageMediaId|The identifier of the image asset used for landscape images with 1.91:1 aspect ratio that could appear in your audience ads.<br/><br/>The aspect ratio of the stored image media can vary, so long as the image asset crop settings result in the supported aspect ratio for this element. To confirm the effective aspect ratio with crop settings, use the [Images](#images) element.<br/><br/>Although in Bing Ads API version 12 you can use the [LandscapeImageMediaId](#landscapeimagemediaid) and [SquareImageMediaId](#squareimagemediaid), these elements are deprecated and will be removed in a future version. You have more flexibility and control of cropped images via the [Images](#images) element.<br/><br/>**Add:** Required if [Images](#images) is not set. If [Images](#images) is set, this element is ignored.<br/>**Update:** Optional. If [Images](#images) is set, this element is ignored. If no value is set for the update, this setting is not changed.|**long**|
|<a name="landscapelogomediaid"></a>LandscapeLogoMediaId|This element is reserved for internal use, and will be removed from a future version of the Bing Ads API.|**long**|
|<a name="longheadline"></a>LongHeadline|This is one of two possible headlines that could appear in your audience ads.<br/><br/>Because audience ads are responsive, we require multiple headlines so they can flexibly serve across a variety of publishers and placements.<br/><br/>The length of the string is limited to 90 characters.<br/><br/>**Add:** Required<br/>**Update:** Optional. If no value is set for the update, this setting is not changed.|**string**|
|<a name="squareimagemediaid"></a>SquareImageMediaId|The identifier of the image asset used for square images with 1:1 aspect ratio that could appear in your audience ads.<br/><br/>The aspect ratio of the stored image media can vary, so long as the image asset crop settings result in the supported aspect ratio for this element. To confirm the effective aspect ratio with crop settings, use the [Images](#images) element. If [Images](#images) is set (not null), then [LandscapeImageMediaId](#landscapeimagemediaid) and [SquareImageMediaId](#squareimagemediaid) are both ignored.<br/><br/>Although in Bing Ads API version 12 you can use the [LandscapeImageMediaId](#landscapeimagemediaid) and [SquareImageMediaId](#squareimagemediaid), these elements are deprecated and will be removed in a future version. You have more flexibility and control of cropped images via the [Images](#images) element.<br/><br/>**Add:** Optional. If [Images](#images) is set, this element is ignored. If you do not choose a square image asset for the ad, Microsoft Advertising will automatically create a new square image asset by cropping the [LandscapeImageMediaId](#landscapeimagemediaid). For more information see the [remarks](#remarks) below.<br/>**Update:** Optional. If [Images](#images) is set, this element is ignored and Microsoft Advertising will automatically create a new square image asset by cropping the LandscapeImageMedia image asset. If [Images](#images) is not set, and if you do not set this element, Microsoft Advertising will automatically create a new square image asset by cropping the [LandscapeImageMediaId](#landscapeimagemediaid). If no value is set for the update, this setting is not changed.|**long**|
|<a name="squarelogomediaid"></a>SquareLogoMediaId|This element is reserved for internal use, and will be removed from a future version of the Bing Ads API.|**long**|
|<a name="text"></a>Text|Depending on your audience ad's placement, this text will appear below or adjacent to your ad's long or short headline.<br/><br/>You have more character space to work with in the ad text than in the headline. So once the imagery and headline have a potential customer's attention, the ad text needs to convince them to click it. What sets your product or service apart?<br/><br/>The text must contain at least one word.<br/><br/>The length of the string is limited to 90 characters.<br/><br/>The text cannot contain the newline (\n) character.<br/><br/>**Add:** Optional<br/>**Update:** Optional. If no value is set for the update, this setting is not changed.|**string**|

The [ResponsiveAd](responsivead.md) object has [Inherited Elements](#inheritedelements).

## <a name="inheritedelements"></a>Inherited Elements

### <a name="inheritedelementsad"></a>Inherited Elements from Ad
The [ResponsiveAd](responsivead.md) object derives from the [Ad](ad.md) object, and inherits the following elements. The descriptions below are specific to [ResponsiveAd](responsivead.md), and might not apply to other objects that inherit the same elements from the [Ad](ad.md) object.  

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="adformatpreference"></a>AdFormatPreference|This element is not applicable for responsive ads.|**string**|
|<a name="devicepreference"></a>DevicePreference|This element is not applicable for responsive ads.|**long**|
|<a name="editorialstatus"></a>EditorialStatus|The editorial review status of the ad, which indicates whether the ad is pending review, has been approved, or has been disapproved.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdEditorialStatus](adeditorialstatus.md)|
|<a name="finalappurls"></a>FinalAppUrls|This element is not applicable for responsive ads.|[AppUrl](appurl.md) array|
|<a name="finalmobileurls"></a>FinalMobileUrls|The mobile landing page URL.<br/><br/>The following validation rules apply to Final URLs and Final Mobile URLs.<br/>- The length of the URL is limited to 2,048 characters. The HTTP or HTTPS protocol string does count towards the 2,048 character limit.<br/>- You may specify up to 10 items for both [FinalUrls](#finalurls) and [FinalMobileUrls](#finalmobileurls); however, only the first item in each list is used for delivery. The service allows up to 10 for potential forward compatibility.<br/>- Usage of '{' and '}' is only allowed to delineate tags, for example *{lpurl}*.<br/>- Final URLs must each be a well-formed URL starting with either http:// or https://.<br/>- If you specify [FinalMobileUrls](#finalmobileurls), you must also specify [FinalUrls](#finalurls).<br/>- You may not specify [FinalMobileUrls](#finalmobileurls) if the device preference is set to mobile.<br/><br/>This URL is used only if the keyword does not specify a final mobile URL.<br/><br/>**Add:** Optional<br/>**Update:** Optional|**string** array|
|<a name="finalurls"></a>FinalUrls|The landing page URL.<br/><br/>The domain portion of the URL in combination with the path 1 and path 2 strings cannot exceed 67 characters.<br/><br/>The following validation rules apply to Final URLs and Final Mobile URLs.<br/>- The length of the URL is limited to 2,048 characters. The HTTP or HTTPS protocol string does count towards the 2,048 character limit.<br/>- You may specify up to 10 items for both [FinalUrls](#finalurls) and [FinalMobileUrls](#finalmobileurls); however, only the first item in each list is used for delivery. The service allows up to 10 for potential forward compatibility.<br/>- Usage of '{' and '}' is only allowed to delineate tags, for example *{lpurl}*.<br/>- Final URLs must each be a well-formed URL starting with either http:// or https://.<br/>- If you specify [FinalMobileUrls](#finalmobileurls), you must also specify [FinalUrls](#finalurls).<br/>- You may not specify [FinalMobileUrls](#finalmobileurls) if the device preference is set to mobile. Also note that  if this ad's *TrackingUrlTemplate* or *UrlCustomParameters* element are set, then at least one final URL is required.<br/><br/>This URL is used only if the keyword does not specify a final URL.<br/><br/>**Add:** Required<br/>**Update:** Optional|**string** array|
|<a name="finalurlsuffix"></a>FinalUrlSuffix|The final URL suffix can include tracking parameters that will be appended to the end of your landing page URL. We recommend placing tracking parameters that your landing page requires in a final URL suffix so that your customers are always sent to your landing page. For more details and validation rules see [Final URL Suffix](../guides/url-tracking-upgraded-urls.md#finalurlsuffixvalidation) in the technical guides.<br/><br/>This feature is only available for customers in the Final URL Suffix Phase 2 pilot ([GetCustomerPilotFeatures](../customer-management-service/getcustomerpilotfeatures.md) returns 566). If you are not in the pilot this property will be ignored and no error will be returned. During calendar year 2019 this feature will be enabled for all customers.<br/><br/>**Add:** Optional<br/>**Update:** Optional. If no value is set for the update, this setting is not changed.|**string**|
|<a name="forwardcompatibilitymap"></a>ForwardCompatibilityMap|The list of key and value strings for forward compatibility to avoid otherwise breaking changes when new elements are added in the current API version.<br/><br/>Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for this object.|[KeyValuePairOfstringstring](keyvaluepairofstringstring.md) array|
|<a name="id"></a>Id|The unique Microsoft Advertising identifier of the ad.<br/><br/>**Add:** Read-only<br/>**Update:** Required and Read-Only|**long**|
|<a name="status"></a>Status|The status of the ad.<br/><br/>You can set the ad status to Active or Paused.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[AdStatus](adstatus.md)|
|<a name="trackingurltemplate"></a>TrackingUrlTemplate|The tracking template to use as a default for all landing page URLs.<br/><br/>The following validation rules apply to tracking templates. For more details about supported templates and parameters, see the Microsoft Advertising help article [What tracking or URL parameters can I use?](https://help.ads.microsoft.com/#apex/3/en/56799/2)<br/>- Tracking templates defined for lower level entities e.g. ads override those set for higher level entities e.g. campaign. For more information, see [Entity Limits](../guides/entity-hierarchy-limits.md).<br/>- The length of the tracking template is limited to 2,048 characters. The HTTP or HTTPS protocol string does count towards the 2,048 character limit.<br/>- The tracking template must be a well-formed URL beginning with one of the following: *http://*, *https://*, *{lpurl}*, or *{unescapedlpurl}*.<br/>- Microsoft Advertising does not validate whether custom parameters exist. If you use custom parameters in your tracking template and they do not exist, then the landing page URL will include the key and value placeholders of your custom parameters without substitution. For example, if your tracking template is *http://tracker.example.com/?season={_season}&promocode={_promocode}&u={lpurl}* and neither *{_season}* or *{_promocode}* are defined at the campaign, ad group, criterion, keyword, or ad level, then the landing page URL will be the same.<br/><br/>**Add:** Optional<br/>**Update:** Optional|**string**|
|<a name="type"></a>Type|The type of the ad. This value is *ResponsiveAd* when you retrieve a responsive ad. For more information about ad types, see the [Ad Data Object Remarks](ad.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdType](adtype.md)|
|<a name="urlcustomparameters"></a>UrlCustomParameters|Your custom collection of key and value parameters for URL tracking.<br/><br/>Microsoft Advertising will accept the first 3 [CustomParameter](customparameter.md) objects that you include within the [CustomParameters](customparameters.md) object, and any additional custom parameters will be ignored. Each [CustomParameter](customparameter.md) includes [Key](customparameter.md#key) and [Value](customparameter.md#value) elements. For customers in the Custom Parameters Limit Increase Phase 2 pilot ([GetCustomerPilotFeatures](../customer-management-service/getcustomerpilotfeatures.md) returns 565), Microsoft Advertising will accept the first 8 custom parameter key and value pairs that you include, and if you include more than 8 custom parameters an error will be returned. During calendar year 2019 the limit will be increased from 3 to 8 for all customers.<br/><br/>**Add:** Optional<br/>**Update:** Optional. If no value is set for the update, this setting is not changed. Set the *UrlCustomParameters* element to null or empty to retain any existing custom parameters. To remove all custom parameters, set the [Parameters](customparameters.md#parameters) element of the [CustomParameters](customparameters.md) object to null or empty. To remove a subset of custom parameters, specify the custom parameters that you want to keep in the [Parameters](customparameters.md#parameters) element of the [CustomParameters](customparameters.md) object.|[CustomParameters](customparameters.md)|

## <a name="remarks"></a>Remarks
Because audience ads are responsive, you can create multiple image assets with different sizes and aspect ratios so they can flexibly display across a variety of publishers and placements. In the [Images](#images) element include one or more [AssetLink](assetlink.md) objects that each contain an [ImageAsset](imageasset.md) with [SubType](imageasset.md#subtype) set to one of the string values in the table below.

|Sub Type|Minimum dimensions in pixels|
|--------|--------|--------|
|LandscapeImageMedia|703 width x 368 height<br/>Aspect radio 1.91:1|
|SquareImageMedia|300 width x 300 height<br/>Aspect radio 1:1|
|ImageMedia169X100|622 width x 368 height<br/>Aspect radio 1.69:1|
|ImageMedia93X100|311 width x 333 height<br/>Aspect radio 0.93:1|
|ImageMedia15X10|300 width x 200 height<br/>Aspect radio 1.5:1|
|ImageMedia155X100|300 width x 194 height<br/>Aspect radio 1.55:1|
|ImageMedia133X100|100 width x 75 height<br/>Aspect radio 1.33:1|
|ImageMedia178X100|624 width x 350 height<br/>Aspect radio 1.78:1|
|ImageMedia172X100|300 width x 174 height<br/>Aspect radio 1.72:1|

> [!NOTE]
> Media for responsive ads are provisioned via the [Image](image.md) object using the [AddMedia](addmedia.md) operation. You can use the GIF, JPEG, or PNG MIME types. Images with animation are not supported. Although you can only add media with a few aspect ratios via the [AddMedia](addmedia.md) operation, you can use [ImageAsset](imageasset.md) crop settings to determine the effective aspect ratio in the context of each responsive ad [AssetLink](assetlink.md). The aspect ratio of the stored image would be unchanged in the account level media library.
> 
> The maximum file size is 5 MB. The maximum width and height in pixels are 2592 and 2048 independently, and you must still maintain one of the supported aspect ratios. For example if the image asset with sub type LandscapeImageMedia is 2592 in width, then the height must be 1357.

You are only required to provide a landscape image asset. In the [Images](#images) element include an [AssetLink](assetlink.md) that contains one [ImageAsset](imageasset.md) with [SubType](imageasset.md#subtype) set to LandscapeImageMedia. The recommended dimensions for the LandscapeImageMedia are 1200 width x 628 height. Optionally you can include additional asset links, i.e., one image asset for each supported sub type. For any image asset sub types that you do not explicitly set, Microsoft Advertising will automatically create image asset links by cropping the LandscapeImageMedia. 

Given the [GetAdsByAdGroupId](getadsbyadgroupid.md) response example below, please take note of the following:
- The same image asset identifier (e.g., 1234567890000) is used for all auto-generated image asset sub types. Whether or not you let Microsoft Advertising automatically generate the cropped images, the [Id](imageasset.md#id) does not need to be unique among the image assets linked to the same ad. 
- Because the ad in this example was created without crop settings for the LandscapeImageMedia image asset sub type, all image assets are cropped except for the original landscape image. 
- Whether or not the landscape image has its own crop settings, Microsoft Advertising uses the true height of the landscape image for all of the default crop settings. In this example the crop height for all system generated image assets is 628, and we can infer that the landscape image (LandscapeImageMedia sub type) with 1.91:1 aspect ratio has width and height of 1200x628. Even if the landscape image asset link had been created with crop settings e.g., 703x368, the crop settings of the auto-generated image assets are based on the full dimensions of the landscape image (again that would be 1200x628 in this example). 
- Although in Bing Ads API version 12 you could use the [LandscapeImageMediaId](#landscapeimagemediaid) and [SquareImageMediaId](#squareimagemediaid), these elements are deprecated and will be removed in a future version. You have more flexibility and control of cropped images via the [Images](#images) element. 

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
	<s:Header>
		<h:TrackingId xmlns:h="https://bingads.microsoft.com/CampaignManagement/v12">3acf4989-d6a3-405f-9fd1-a2e8dd1b09f8</h:TrackingId>
	</s:Header>
	<s:Body>
		<GetAdsByAdGroupIdResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v12">
			<Ads xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
				<Ad i:type="ResponsiveAd">
					<AdFormatPreference i:nil="true"/>
					<DevicePreference>0</DevicePreference>
					<EditorialStatus>Inactive</EditorialStatus>
					<FinalAppUrls i:nil="true"/>
					<FinalMobileUrls xmlns:a="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
						<a:string>http://mobile.contoso.com/womenshoesale</a:string>
					</FinalMobileUrls>
					<FinalUrls xmlns:a="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
						<a:string>http://www.contoso.com/womenshoesale</a:string>
					</FinalUrls>
					<ForwardCompatibilityMap xmlns:a="http://schemas.datacontract.org/2004/07/System.Collections.Generic"/>
					<Id>9876543210000</Id>
					<Status>Active</Status>
					<TrackingUrlTemplate i:nil="true"/>
					<Type>ResponsiveAd</Type>
					<UrlCustomParameters i:nil="true"/>
					<BusinessName>Contoso</BusinessName>
					<CallToAction>AddToCart</CallToAction>
					<Headline>Fast &amp; Easy Setup</Headline>
					<Images>
						<AssetLink>
							<Asset i:type="ImageAsset">
								<Id>1234567890000</Id>
								<Name i:nil="true"/>
								<Type>ImageAsset</Type>
								<CropHeight i:nil="true"/>
								<CropWidth i:nil="true"/>
								<CropX i:nil="true"/>
								<CropY i:nil="true"/>
								<SubType>LandscapeImageMedia</SubType>
							</Asset>
							<AssetPerformanceLabel i:nil="true"/>
							<EditorialStatus i:nil="true"/>
							<PinnedField i:nil="true"/>
						</AssetLink>
						<AssetLink>
							<Asset i:type="ImageAsset">
								<Id>1234567890000</Id>
								<Name i:nil="true"/>
								<Type>ImageAsset</Type>
								<CropHeight>628</CropHeight>
								<CropWidth>628</CropWidth>
								<CropX>286</CropX>
								<CropY>0</CropY>
								<SubType>SquareImageMedia</SubType>
							</Asset>
							<AssetPerformanceLabel i:nil="true"/>
							<EditorialStatus i:nil="true"/>
							<PinnedField i:nil="true"/>
						</AssetLink>
						<AssetLink>
							<Asset i:type="ImageAsset">
								<Id>1234567890000</Id>
								<Name i:nil="true"/>
								<Type>ImageAsset</Type>
								<CropHeight>628</CropHeight>
								<CropWidth>1061</CropWidth>
								<CropX>70</CropX>
								<CropY>0</CropY>
								<SubType>ImageMedia169X100</SubType>
							</Asset>
							<AssetPerformanceLabel i:nil="true"/>
							<EditorialStatus i:nil="true"/>
							<PinnedField i:nil="true"/>
						</AssetLink>
						<AssetLink>
							<Asset i:type="ImageAsset">
								<Id>1234567890000</Id>
								<Name i:nil="true"/>
								<Type>ImageAsset</Type>
								<CropHeight>628</CropHeight>
								<CropWidth>584</CropWidth>
								<CropX>308</CropX>
								<CropY>0</CropY>
								<SubType>ImageMedia93X100</SubType>
							</Asset>
							<AssetPerformanceLabel i:nil="true"/>
							<EditorialStatus i:nil="true"/>
							<PinnedField i:nil="true"/>
						</AssetLink>
						<AssetLink>
							<Asset i:type="ImageAsset">
								<Id>1234567890000</Id>
								<Name i:nil="true"/>
								<Type>ImageAsset</Type>
								<CropHeight>628</CropHeight>
								<CropWidth>942</CropWidth>
								<CropX>129</CropX>
								<CropY>0</CropY>
								<SubType>ImageMedia15X10</SubType>
							</Asset>
							<AssetPerformanceLabel i:nil="true"/>
							<EditorialStatus i:nil="true"/>
							<PinnedField i:nil="true"/>
						</AssetLink>
						<AssetLink>
							<Asset i:type="ImageAsset">
								<Id>1234567890000</Id>
								<Name i:nil="true"/>
								<Type>ImageAsset</Type>
								<CropHeight>628</CropHeight>
								<CropWidth>973</CropWidth>
								<CropX>114</CropX>
								<CropY>0</CropY>
								<SubType>ImageMedia155X100</SubType>
							</Asset>
							<AssetPerformanceLabel i:nil="true"/>
							<EditorialStatus i:nil="true"/>
							<PinnedField i:nil="true"/>
						</AssetLink>
						<AssetLink>
							<Asset i:type="ImageAsset">
								<Id>1234567890000</Id>
								<Name i:nil="true"/>
								<Type>ImageAsset</Type>
								<CropHeight>628</CropHeight>
								<CropWidth>835</CropWidth>
								<CropX>183</CropX>
								<CropY>0</CropY>
								<SubType>ImageMedia133X100</SubType>
							</Asset>
							<AssetPerformanceLabel i:nil="true"/>
							<EditorialStatus i:nil="true"/>
							<PinnedField i:nil="true"/>
						</AssetLink>
						<AssetLink>
							<Asset i:type="ImageAsset">
								<Id>1234567890000</Id>
								<Name i:nil="true"/>
								<Type>ImageAsset</Type>
								<CropHeight>628</CropHeight>
								<CropWidth>1118</CropWidth>
								<CropX>41</CropX>
								<CropY>0</CropY>
								<SubType>ImageMedia178X100</SubType>
							</Asset>
							<AssetPerformanceLabel i:nil="true"/>
							<EditorialStatus i:nil="true"/>
							<PinnedField i:nil="true"/>
						</AssetLink>
						<AssetLink>
							<Asset i:type="ImageAsset">
								<Id>1234567890000</Id>
								<Name i:nil="true"/>
								<Type>ImageAsset</Type>
								<CropHeight>628</CropHeight>
								<CropWidth>1080</CropWidth>
								<CropX>60</CropX>
								<CropY>0</CropY>
								<SubType>ImageMedia172X100</SubType>
							</Asset>
							<AssetPerformanceLabel i:nil="true"/>
							<EditorialStatus i:nil="true"/>
							<PinnedField i:nil="true"/>
						</AssetLink>
					</Images>
					<LandscapeImageMediaId>1234567890000</LandscapeImageMediaId>
					<LandscapeLogoMediaId i:nil="true"/>
					<LongHeadline>Find New Customers &amp; Increase Sales!</LongHeadline>
					<SquareImageMediaId>1234567890000</SquareImageMediaId>
					<SquareLogoMediaId i:nil="true"/>
					<Text>Find New Customers &amp; Increase Sales! Start Advertising on Contoso Today.</Text>
				</Ad>
			</Ads>
		</GetAdsByAdGroupIdResponse>
	</s:Body>
</s:Envelope>
```

## Requirements
Service: [CampaignManagementService.svc v12](https://campaign.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v12/CampaignManagementService.svc)  
Namespace: https\://bingads.microsoft.com/CampaignManagement/v12  

