---
title: SearchClientLinks Service Operation - Customer Management
ms.service: bing-ads-customer-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Searches for the client links for the customer of the current authenticated user, filtered by the search criteria.
dev_langs: 
  - csharp
  - java
  - php
  - python
---
# SearchClientLinks Service Operation - Customer Management
Searches for the client links for the customer of the current authenticated user, filtered by the search criteria. The operation returns the most recent link for each unique combination of agency customer and client account. 

> [!NOTE]
> Only a user with Super Admin or Standard credentials can add, update, and search for client links to advertiser accounts. 
> 
> Only a user with Super Admin credentials can add, update, and search for client links to customers. 
> 
> Customer to customer linking is only available in Bing Ads API version 13 for pilot customers where [GetCustomerPilotFeatures](getcustomerpilotfeatures.md) returns feature identifier 449. 

If your user is within a client customer that has one or more accounts managed by an agency, then you may search one at a time for individual accounts that were or are eligible to be linked. To search by individual account, set the predicate field to ClientAccountId and set the predicate value to the account identifier that you want to find.

> [!TIP]
> For more information about the client link lifecycle, see the [Account Hierarchy](../guides/account-hierarchy-permissions.md#account-hierarchy) technical guide. For more information about becoming an agency, see the [Resources for agency partners](https://about.ads.microsoft.com/en-us/resources/agency-hub). For more information from a client's perspective, see [How to have an agency manage your Microsoft Advertising account](https://help.ads.microsoft.com/#apex/3/en/52004/3). 

## <a name="request"></a>Request Elements
The *SearchClientLinksRequest* object defines the [body](#request-body) and [header](#request-header) elements of the service operation request. The elements must be in the same order as shown in the [Request SOAP](#request-soap). 

> [!NOTE]
> Unless otherwise noted below, all request elements are required.

### <a name="request-body"></a>Request Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="ordering"></a>Ordering|Determines the order of results.<br/><br/>This request element is optional. If specified, you should only include one *OrderBy* element in the list. Additional elements are not supported and will be ignored by the service.<br/><br/>For this service operation, the following values are supported in the *Field* element of a *OrderBy* object.<br/><br/>*Id* - The order is determined by the *ClientAccountId* element of the returned [ClientLink](clientlink.md).<br/><br/>*Name* - The order is determined by the *Name* element of the returned [ClientLink](clientlink.md).<br/><br/>*Number* - The order is determined by the *ManagingCustomerNumber* element of the returned [ClientLink](clientlink.md).|[OrderBy](orderby.md) array|
|<a name="pageinfo"></a>PageInfo|Determines the index and size of results per page.|[Paging](paging.md)|
|<a name="predicates"></a>Predicates|Determines the conditions that must be met to return client links.<br/><br/>You must include one or two predicates.<br/><br/>For details about how results are determined for each supported predicate [Field](predicate.md#field) value see [Predicate Remarks](predicate.md#remarks).|[Predicate](predicate.md) array|

### <a name="request-header"></a>Request Header Elements
[!INCLUDE[request-header](./includes/request-header.md)]

## <a name="response"></a>Response Elements
The *SearchClientLinksResponse* object defines the [body](#response-body) and [header](#response-header) elements of the service operation response. The elements are returned in the same order as shown in the [Response SOAP](#response-soap).

### <a name="response-body"></a>Response Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="clientlinks"></a>ClientLinks|The list of client link invitations.|[ClientLink](clientlink.md) array|

### <a name="response-header"></a>Response Header Elements
[!INCLUDE[response-header](./includes/response-header.md)]

## <a name="request-soap"></a>Request SOAP
This template was generated by a tool to show the [order](../guides/services-protocol.md#element-order) of the [body](#request-body) and [header](#request-header) elements for the SOAP request. For supported types that you can use with this service operation, see the [Request Body Elements](#request-header) reference above.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v12">
    <Action mustUnderstand="1">SearchClientLinks</Action>
    <AuthenticationToken i:nil="false">ValueHere</AuthenticationToken>
    <DeveloperToken i:nil="false">ValueHere</DeveloperToken>
  </s:Header>
  <s:Body>
    <SearchClientLinksRequest xmlns="https://bingads.microsoft.com/Customer/v12">
      <Predicates xmlns:e405="https://bingads.microsoft.com/Customer/v12/Entities" i:nil="false">
        <e405:Predicate>
          <e405:Field i:nil="false">ValueHere</e405:Field>
          <e405:Operator>ValueHere</e405:Operator>
          <e405:Value i:nil="false">ValueHere</e405:Value>
        </e405:Predicate>
      </Predicates>
      <Ordering xmlns:e406="https://bingads.microsoft.com/Customer/v12/Entities" i:nil="false">
        <e406:OrderBy>
          <e406:Field>ValueHere</e406:Field>
          <e406:Order>ValueHere</e406:Order>
        </e406:OrderBy>
      </Ordering>
      <PageInfo xmlns:e407="https://bingads.microsoft.com/Customer/v12/Entities" i:nil="false">
        <e407:Index>ValueHere</e407:Index>
        <e407:Size>ValueHere</e407:Size>
      </PageInfo>
    </SearchClientLinksRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response-soap"></a>Response SOAP
This template was generated by a tool to show the order of the [body](#response-body) and [header](#response-header) elements for the SOAP response.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v12">
    <TrackingId d3p1:nil="false" xmlns:d3p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</TrackingId>
  </s:Header>
  <s:Body>
    <SearchClientLinksResponse xmlns="https://bingads.microsoft.com/Customer/v12">
      <ClientLinks xmlns:e408="https://bingads.microsoft.com/Customer/v12/Entities" d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">
        <e408:ClientLink>
          <e408:ClientAccountId d4p1:nil="false">ValueHere</e408:ClientAccountId>
          <e408:ClientAccountNumber d4p1:nil="false">ValueHere</e408:ClientAccountNumber>
          <e408:ManagingCustomerId d4p1:nil="false">ValueHere</e408:ManagingCustomerId>
          <e408:ManagingCustomerNumber d4p1:nil="false">ValueHere</e408:ManagingCustomerNumber>
          <e408:Note d4p1:nil="false">ValueHere</e408:Note>
          <e408:Name d4p1:nil="false">ValueHere</e408:Name>
          <e408:InviterEmail d4p1:nil="false">ValueHere</e408:InviterEmail>
          <e408:InviterName d4p1:nil="false">ValueHere</e408:InviterName>
          <e408:InviterPhone d4p1:nil="false">ValueHere</e408:InviterPhone>
          <e408:IsBillToClient>ValueHere</e408:IsBillToClient>
          <e408:StartDate d4p1:nil="false">ValueHere</e408:StartDate>
          <e408:Status d4p1:nil="false">ValueHere</e408:Status>
          <e408:SuppressNotification>ValueHere</e408:SuppressNotification>
          <e408:LastModifiedDateTime>ValueHere</e408:LastModifiedDateTime>
          <e408:LastModifiedByUserId>ValueHere</e408:LastModifiedByUserId>
          <e408:Timestamp d4p1:nil="false">ValueHere</e408:Timestamp>
          <e408:ForwardCompatibilityMap xmlns:e409="http://schemas.datacontract.org/2004/07/System.Collections.Generic" d4p1:nil="false">
            <e409:KeyValuePairOfstringstring>
              <e409:key d4p1:nil="false">ValueHere</e409:key>
              <e409:value d4p1:nil="false">ValueHere</e409:value>
            </e409:KeyValuePairOfstringstring>
          </e408:ForwardCompatibilityMap>
        </e408:ClientLink>
      </ClientLinks>
    </SearchClientLinksResponse>
  </s:Body>
</s:Envelope>
```

## <a name="example"></a>Code Syntax
The example syntax can be used with [Bing Ads SDKs](../guides/client-libraries.md). See [Bing Ads API Code Examples](../guides/code-examples.md) for more examples.
```csharp
public async Task<SearchClientLinksResponse> SearchClientLinksAsync(
	IList<Predicate> predicates,
	IList<OrderBy> ordering,
	Paging pageInfo)
{
	var request = new SearchClientLinksRequest
	{
		Predicates = predicates,
		Ordering = ordering,
		PageInfo = pageInfo
	};

	return (await CustomerManagementService.CallAsync((s, r) => s.SearchClientLinksAsync(r), request));
}
```
```java
static SearchClientLinksResponse searchClientLinks(
	ArrayOfPredicate predicates,
	ArrayOfOrderBy ordering,
	Paging pageInfo) throws RemoteException, Exception
{
	SearchClientLinksRequest request = new SearchClientLinksRequest();

	request.setPredicates(predicates);
	request.setOrdering(ordering);
	request.setPageInfo(pageInfo);

	return CustomerManagementService.getService().searchClientLinks(request);
}
```
```php
static function SearchClientLinks(
	$predicates,
	$ordering,
	$pageInfo)
{

	$GLOBALS['Proxy'] = $GLOBALS['CustomerManagementProxy'];

	$request = new SearchClientLinksRequest();

	$request->Predicates = $predicates;
	$request->Ordering = $ordering;
	$request->PageInfo = $pageInfo;

	return $GLOBALS['CustomerManagementProxy']->GetService()->SearchClientLinks($request);
}
```
```python
response=customermanagement_service.SearchClientLinks(
	Predicates=Predicates,
	Ordering=Ordering,
	PageInfo=PageInfo)
```

## Requirements
Service: [CustomerManagementService.svc v12](https://clientcenter.api.bingads.microsoft.com/Api/CustomerManagement/v12/CustomerManagementService.svc)  
Namespace: https\://bingads.microsoft.com/Customer/v12  

