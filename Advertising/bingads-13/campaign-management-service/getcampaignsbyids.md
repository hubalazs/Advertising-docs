---
title: GetCampaignsByIds Service Operation - Campaign Management
ms.service: bing-ads-campaign-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Gets the specified campaigns within an account.
dev_langs: 
  - csharp
  - java
  - php
  - python
---
# GetCampaignsByIds Service Operation - Campaign Management
Gets the specified campaigns within an account.

## <a name="request"></a>Request Elements
The *GetCampaignsByIdsRequest* object defines the [body](#request-body) and [header](#request-header) elements of the service operation request. The elements must be in the same order as shown in the [Request SOAP](#request-soap). 

> [!NOTE]
> Unless otherwise noted below, all request elements are required.

### <a name="request-body"></a>Request Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="accountid"></a>AccountId|The identifier of the account that contains the campaigns to get.|**long**|
|<a name="campaignids"></a>CampaignIds|A maximum of 100 identifiers of the campaigns to get from the specified account.<br/><br/>The identifiers must correspond to campaigns of the specified *CampaignType* or types, and otherwise the service will return error code *EntityIdFilterMismatch* (Code 516).|**long** array|
|<a name="campaigntype"></a>CampaignType|The type of campaigns to get, for example *Search*, *Shopping*, or *DynamicSearchAds*. You can specify one or more types.<br/><br/>This request element is optional. If you do not set any campaign type, the default value is *Search* i.e., only Search campaigns will be returned.|[CampaignType](campaigntype.md)|

### <a name="request-header"></a>Request Header Elements
[!INCLUDE[request-header](./includes/request-header.md)]

## <a name="response"></a>Response Elements
The *GetCampaignsByIdsResponse* object defines the [body](#response-body) and [header](#response-header) elements of the service operation response. The elements are returned in the same order as shown in the [Response SOAP](#response-soap).

### <a name="response-body"></a>Response Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="campaigns"></a>Campaigns|An array of [Campaign](campaign.md) objects that corresponds directly to the campaign identifiers that you specified in the request. Items of the list may be returned as null. For each list index where a campaign was not retrieved, the corresponding element will be null.|[Campaign](campaign.md) array|
|<a name="partialerrors"></a>PartialErrors|An array of [BatchError](batcherror.md) objects that contain details for any campaigns that were not successfully retrieved.<br/><br/>The list of errors corresponds directly to the list of campaigns in the request. Items of the list may be returned as null. For each list index where a campaign was successfully retrieved, the corresponding error element will be null. Ideally all campaigns are retrieved successfully and all elements in this list are null.|[BatchError](batcherror.md) array|

### <a name="response-header"></a>Response Header Elements
[!INCLUDE[response-header](./includes/response-header.md)]

## <a name="request-soap"></a>Request SOAP
This template was generated by a tool to show the [order](../guides/services-protocol.md#element-order) of the [body](#request-body) and [header](#request-header) elements for the SOAP request. For supported types that you can use with this service operation, see the [Request Body Elements](#request-header) reference above.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v13">
    <Action mustUnderstand="1">GetCampaignsByIds</Action>
    <AuthenticationToken i:nil="false">ValueHere</AuthenticationToken>
    <CustomerAccountId i:nil="false">ValueHere</CustomerAccountId>
    <CustomerId i:nil="false">ValueHere</CustomerId>
    <DeveloperToken i:nil="false">ValueHere</DeveloperToken>
  </s:Header>
  <s:Body>
    <GetCampaignsByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v13">
      <AccountId>ValueHere</AccountId>
      <CampaignIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long>ValueHere</a1:long>
      </CampaignIds>
      <CampaignType>ValueHere</CampaignType>
    </GetCampaignsByIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response-soap"></a>Response SOAP
This template was generated by a tool to show the order of the [body](#response-body) and [header](#response-header) elements for the SOAP response.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v13">
    <TrackingId d3p1:nil="false" xmlns:d3p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</TrackingId>
  </s:Header>
  <s:Body>
    <GetCampaignsByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v13">
      <Campaigns d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">
        <Campaign>
          <AudienceAdsBidAdjustment d4p1:nil="false">ValueHere</AudienceAdsBidAdjustment>
          <BiddingScheme d4p1:nil="false" d4p1:type="-- derived type specified here with the appropriate prefix --">
            <Type d4p1:nil="false">ValueHere</Type>
            <!--This field is applicable if the derived type attribute is set to MaxClicksBiddingScheme-->
            <MaxCpc d4p1:nil="false">
              <Amount d4p1:nil="false">ValueHere</Amount>
            </MaxCpc>
            <!--This field is applicable if the derived type attribute is set to MaxConversionsBiddingScheme-->
            <MaxCpc d4p1:nil="false">
              <Amount d4p1:nil="false">ValueHere</Amount>
            </MaxCpc>
            <!--These fields are applicable if the derived type attribute is set to TargetCpaBiddingScheme-->
            <MaxCpc d4p1:nil="false">
              <Amount d4p1:nil="false">ValueHere</Amount>
            </MaxCpc>
            <TargetCpa d4p1:nil="false">ValueHere</TargetCpa>
            <!--No additional fields are applicable if the derived type attribute is set to ManualCpcBiddingScheme-->
            <!--No additional fields are applicable if the derived type attribute is set to EnhancedCpcBiddingScheme-->
            <!--This field is applicable if the derived type attribute is set to InheritFromParentBiddingScheme-->
            <InheritedBidStrategyType d4p1:nil="false">ValueHere</InheritedBidStrategyType>
            <!--These fields are applicable if the derived type attribute is set to TargetRoasBiddingScheme-->
            <MaxCpc d4p1:nil="false">
              <Amount d4p1:nil="false">ValueHere</Amount>
            </MaxCpc>
            <TargetRoas d4p1:nil="false">ValueHere</TargetRoas>
            <!--This field is applicable if the derived type attribute is set to MaxRoasBiddingScheme-->
            <MaxCpc d4p1:nil="false">
              <Amount d4p1:nil="false">ValueHere</Amount>
            </MaxCpc>
          </BiddingScheme>
          <BudgetType d4p1:nil="false">ValueHere</BudgetType>
          <DailyBudget d4p1:nil="false">ValueHere</DailyBudget>
          <ExperimentId d4p1:nil="false">ValueHere</ExperimentId>
          <FinalUrlSuffix d4p1:nil="false">ValueHere</FinalUrlSuffix>
          <ForwardCompatibilityMap xmlns:e74="http://schemas.datacontract.org/2004/07/System.Collections.Generic" d4p1:nil="false">
            <e74:KeyValuePairOfstringstring>
              <e74:key d4p1:nil="false">ValueHere</e74:key>
              <e74:value d4p1:nil="false">ValueHere</e74:value>
            </e74:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id d4p1:nil="false">ValueHere</Id>
          <Name d4p1:nil="false">ValueHere</Name>
          <Status d4p1:nil="false">ValueHere</Status>
          <SubType d4p1:nil="false">ValueHere</SubType>
          <TimeZone d4p1:nil="false">ValueHere</TimeZone>
          <TrackingUrlTemplate d4p1:nil="false">ValueHere</TrackingUrlTemplate>
          <UrlCustomParameters d4p1:nil="false">
            <Parameters d4p1:nil="false">
              <CustomParameter>
                <Key d4p1:nil="false">ValueHere</Key>
                <Value d4p1:nil="false">ValueHere</Value>
              </CustomParameter>
            </Parameters>
          </UrlCustomParameters>
          <CampaignType d4p1:nil="false">ValueHere</CampaignType>
          <Settings d4p1:nil="false">
            <Setting d4p1:type="-- derived type specified here with the appropriate prefix --">
              <Type d4p1:nil="false">ValueHere</Type>
              <!--These fields are applicable if the derived type attribute is set to ShoppingSetting-->
              <LocalInventoryAdsEnabled d4p1:nil="false">ValueHere</LocalInventoryAdsEnabled>
              <Priority d4p1:nil="false">ValueHere</Priority>
              <SalesCountryCode d4p1:nil="false">ValueHere</SalesCountryCode>
              <StoreId d4p1:nil="false">ValueHere</StoreId>
              <!--These fields are applicable if the derived type attribute is set to DynamicSearchAdsSetting-->
              <DomainName d4p1:nil="false">ValueHere</DomainName>
              <Language d4p1:nil="false">ValueHere</Language>
              <PageFeedIds d4p1:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
                <a1:long>ValueHere</a1:long>
              </PageFeedIds>
              <Source d4p1:nil="false">ValueHere</Source>
              <!--This field is applicable if the derived type attribute is set to TargetSetting-->
              <Details d4p1:nil="false">
                <TargetSettingDetail>
                  <CriterionTypeGroup>ValueHere</CriterionTypeGroup>
                  <TargetAndBid>ValueHere</TargetAndBid>
                </TargetSettingDetail>
              </Details>
              <!--These fields are applicable if the derived type attribute is set to CoOpSetting-->
              <BidBoostValue d4p1:nil="false">ValueHere</BidBoostValue>
              <BidMaxValue d4p1:nil="false">ValueHere</BidMaxValue>
              <BidOption d4p1:nil="false">ValueHere</BidOption>
            </Setting>
          </Settings>
          <BudgetId d4p1:nil="false">ValueHere</BudgetId>
          <Languages d4p1:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string>ValueHere</a1:string>
          </Languages>
        </Campaign>
      </Campaigns>
      <PartialErrors d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError d4p1:type="-- derived type specified here with the appropriate prefix --">
          <Code>ValueHere</Code>
          <Details d4p1:nil="false">ValueHere</Details>
          <ErrorCode d4p1:nil="false">ValueHere</ErrorCode>
          <FieldPath d4p1:nil="false">ValueHere</FieldPath>
          <ForwardCompatibilityMap xmlns:e75="http://schemas.datacontract.org/2004/07/System.Collections.Generic" d4p1:nil="false">
            <e75:KeyValuePairOfstringstring>
              <e75:key d4p1:nil="false">ValueHere</e75:key>
              <e75:value d4p1:nil="false">ValueHere</e75:value>
            </e75:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Index>ValueHere</Index>
          <Message d4p1:nil="false">ValueHere</Message>
          <Type d4p1:nil="false">ValueHere</Type>
          <!--These fields are applicable if the derived type attribute is set to EditorialError-->
          <Appealable d4p1:nil="false">ValueHere</Appealable>
          <DisapprovedText d4p1:nil="false">ValueHere</DisapprovedText>
          <Location d4p1:nil="false">ValueHere</Location>
          <PublisherCountry d4p1:nil="false">ValueHere</PublisherCountry>
          <ReasonCode>ValueHere</ReasonCode>
        </BatchError>
      </PartialErrors>
    </GetCampaignsByIdsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="example"></a>Code Syntax
The example syntax can be used with [Bing Ads SDKs](../guides/client-libraries.md). See [Bing Ads API Code Examples](../guides/code-examples.md) for more examples.
```csharp
public async Task<GetCampaignsByIdsResponse> GetCampaignsByIdsAsync(
	long accountId,
	IList<long> campaignIds,
	CampaignType campaignType)
{
	var request = new GetCampaignsByIdsRequest
	{
		AccountId = accountId,
		CampaignIds = campaignIds,
		CampaignType = campaignType
	};

	return (await CampaignManagementService.CallAsync((s, r) => s.GetCampaignsByIdsAsync(r), request));
}
```
```java
static GetCampaignsByIdsResponse getCampaignsByIds(
	java.lang.Long accountId,
	ArrayOflong campaignIds,
	ArrayList<CampaignType> campaignType) throws RemoteException, Exception
{
	GetCampaignsByIdsRequest request = new GetCampaignsByIdsRequest();

	request.setAccountId(accountId);
	request.setCampaignIds(campaignIds);
	request.setCampaignType(campaignType);

	return CampaignManagementService.getService().getCampaignsByIds(request);
}
```
```php
static function GetCampaignsByIds(
	$accountId,
	$campaignIds,
	$campaignType)
{

	$GLOBALS['Proxy'] = $GLOBALS['CampaignManagementProxy'];

	$request = new GetCampaignsByIdsRequest();

	$request->AccountId = $accountId;
	$request->CampaignIds = $campaignIds;
	$request->CampaignType = $campaignType;

	return $GLOBALS['CampaignManagementProxy']->GetService()->GetCampaignsByIds($request);
}
```
```python
response=campaignmanagement_service.GetCampaignsByIds(
	AccountId=AccountId,
	CampaignIds=CampaignIds,
	CampaignType=CampaignType)
```

## Requirements
Service: [CampaignManagementService.svc v13](https://campaign.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v13/CampaignManagementService.svc)  
Namespace: https\://bingads.microsoft.com/CampaignManagement/v13  

