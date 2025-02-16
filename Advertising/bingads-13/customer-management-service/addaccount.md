---
title: AddAccount Service Operation - Customer Management
ms.service: bing-ads-customer-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Creates a new account within an existing customer.
dev_langs: 
  - csharp
  - java
  - php
  - python
---
# AddAccount Service Operation - Customer Management
Creates a new account within an existing customer. 

> [!NOTE]
> Only a user with Super Admin credentials can add accounts. For more information, see the [User Roles](../guides/account-hierarchy-permissions.md#user-roles) technical guide.  

> [!TIP]
> Resellers should call [SignupCustomer](signupcustomer.md) instead of *AddAccount*. For more details see the [Account Hierarchy](../guides/account-hierarchy-permissions.md#account-hierarchy) technical guide.

## <a name="request"></a>Request Elements
The *AddAccountRequest* object defines the [body](#request-body) and [header](#request-header) elements of the service operation request. The elements must be in the same order as shown in the [Request SOAP](#request-soap). 

> [!NOTE]
> Unless otherwise noted below, all request elements are required.

### <a name="request-body"></a>Request Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="account"></a>Account|The account that you want to add to the existing customer.<br/><br/>You must specify the ParentCustomerId in the advertiser account object.|[AdvertiserAccount](advertiseraccount.md)|

### <a name="request-header"></a>Request Header Elements
[!INCLUDE[request-header](./includes/request-header.md)]

## <a name="response"></a>Response Elements
The *AddAccountResponse* object defines the [body](#response-body) and [header](#response-header) elements of the service operation response. The elements are returned in the same order as shown in the [Response SOAP](#response-soap).

### <a name="response-body"></a>Response Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="accountid"></a>AccountId|A system-generated account identifier corresponding to the new account specified in the request.<br/><br/>Use this identifier with operation requests that require an *AccountId* element and a *CustomerAccountId* SOAP header element.|**long**|
|<a name="accountnumber"></a>AccountNumber|A system-generated account number that is used to identify the account in the Microsoft Advertising web application. The account number has the form, X*nnnnnnn*, where *nnnnnnn* is a series of digits.|**string**|
|<a name="createtime"></a>CreateTime|The date and time that the account was added. The date and time value reflects the date and time at the server, not the client. For information about the format of the date and time, see the dateTime entry in [Primitive XML Data Types](https://go.microsoft.com/fwlink/?linkid=859198).|**dateTime**|

### <a name="response-header"></a>Response Header Elements
[!INCLUDE[response-header](./includes/response-header.md)]

## <a name="request-soap"></a>Request SOAP
This template was generated by a tool to show the [order](../guides/services-protocol.md#element-order) of the [body](#request-body) and [header](#request-header) elements for the SOAP request. For supported types that you can use with this service operation, see the [Request Body Elements](#request-header) reference above.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v13">
    <Action mustUnderstand="1">AddAccount</Action>
    <AuthenticationToken i:nil="false">ValueHere</AuthenticationToken>
    <DeveloperToken i:nil="false">ValueHere</DeveloperToken>
  </s:Header>
  <s:Body>
    <AddAccountRequest xmlns="https://bingads.microsoft.com/Customer/v13">
      <Account xmlns:e1315="https://bingads.microsoft.com/Customer/v13/Entities" i:nil="false">
        <e1315:BillToCustomerId i:nil="false">ValueHere</e1315:BillToCustomerId>
        <e1315:CurrencyCode i:nil="false">ValueHere</e1315:CurrencyCode>
        <e1315:AccountFinancialStatus i:nil="false">ValueHere</e1315:AccountFinancialStatus>
        <e1315:Id i:nil="false">ValueHere</e1315:Id>
        <e1315:Language i:nil="false">ValueHere</e1315:Language>
        <e1315:LastModifiedByUserId i:nil="false">ValueHere</e1315:LastModifiedByUserId>
        <e1315:LastModifiedTime i:nil="false">ValueHere</e1315:LastModifiedTime>
        <e1315:Name i:nil="false">ValueHere</e1315:Name>
        <e1315:Number i:nil="false">ValueHere</e1315:Number>
        <e1315:ParentCustomerId>ValueHere</e1315:ParentCustomerId>
        <e1315:PaymentMethodId i:nil="false">ValueHere</e1315:PaymentMethodId>
        <e1315:PaymentMethodType i:nil="false">ValueHere</e1315:PaymentMethodType>
        <e1315:PrimaryUserId i:nil="false">ValueHere</e1315:PrimaryUserId>
        <e1315:AccountLifeCycleStatus i:nil="false">ValueHere</e1315:AccountLifeCycleStatus>
        <e1315:TimeStamp i:nil="false">ValueHere</e1315:TimeStamp>
        <e1315:TimeZone i:nil="false">ValueHere</e1315:TimeZone>
        <e1315:PauseReason i:nil="false">ValueHere</e1315:PauseReason>
        <e1315:ForwardCompatibilityMap xmlns:e1316="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          <e1316:KeyValuePairOfstringstring>
            <e1316:key i:nil="false">ValueHere</e1316:key>
            <e1316:value i:nil="false">ValueHere</e1316:value>
          </e1316:KeyValuePairOfstringstring>
        </e1315:ForwardCompatibilityMap>
        <e1315:LinkedAgencies i:nil="false">
          <e1315:CustomerInfo>
            <e1315:Id i:nil="false">ValueHere</e1315:Id>
            <e1315:Name i:nil="false">ValueHere</e1315:Name>
          </e1315:CustomerInfo>
        </e1315:LinkedAgencies>
        <e1315:SalesHouseCustomerId i:nil="false">ValueHere</e1315:SalesHouseCustomerId>
        <e1315:TaxInformation xmlns:e1317="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          <e1317:KeyValuePairOfstringstring>
            <e1317:key i:nil="false">ValueHere</e1317:key>
            <e1317:value i:nil="false">ValueHere</e1317:value>
          </e1317:KeyValuePairOfstringstring>
        </e1315:TaxInformation>
        <e1315:BackUpPaymentInstrumentId i:nil="false">ValueHere</e1315:BackUpPaymentInstrumentId>
        <e1315:BillingThresholdAmount i:nil="false">ValueHere</e1315:BillingThresholdAmount>
        <e1315:BusinessAddress i:nil="false">
          <e1315:City i:nil="false">ValueHere</e1315:City>
          <e1315:CountryCode i:nil="false">ValueHere</e1315:CountryCode>
          <e1315:Id i:nil="false">ValueHere</e1315:Id>
          <e1315:Line1 i:nil="false">ValueHere</e1315:Line1>
          <e1315:Line2 i:nil="false">ValueHere</e1315:Line2>
          <e1315:Line3 i:nil="false">ValueHere</e1315:Line3>
          <e1315:Line4 i:nil="false">ValueHere</e1315:Line4>
          <e1315:PostalCode i:nil="false">ValueHere</e1315:PostalCode>
          <e1315:StateOrProvince i:nil="false">ValueHere</e1315:StateOrProvince>
          <e1315:TimeStamp i:nil="false">ValueHere</e1315:TimeStamp>
          <e1315:BusinessName i:nil="false">ValueHere</e1315:BusinessName>
        </e1315:BusinessAddress>
        <e1315:AutoTagType i:nil="false">ValueHere</e1315:AutoTagType>
        <e1315:SoldToPaymentInstrumentId i:nil="false">ValueHere</e1315:SoldToPaymentInstrumentId>
      </Account>
    </AddAccountRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response-soap"></a>Response SOAP
This template was generated by a tool to show the order of the [body](#response-body) and [header](#response-header) elements for the SOAP response.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v13">
    <TrackingId d3p1:nil="false" xmlns:d3p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</TrackingId>
  </s:Header>
  <s:Body>
    <AddAccountResponse xmlns="https://bingads.microsoft.com/Customer/v13">
      <AccountId>ValueHere</AccountId>
      <AccountNumber d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</AccountNumber>
      <CreateTime>ValueHere</CreateTime>
    </AddAccountResponse>
  </s:Body>
</s:Envelope>
```

## <a name="example"></a>Code Syntax
The example syntax can be used with [Bing Ads SDKs](../guides/client-libraries.md). See [Bing Ads API Code Examples](../guides/code-examples.md) for more examples.
```csharp
public async Task<AddAccountResponse> AddAccountAsync(
	AdvertiserAccount account)
{
	var request = new AddAccountRequest
	{
		Account = account
	};

	return (await CustomerManagementService.CallAsync((s, r) => s.AddAccountAsync(r), request));
}
```
```java
static AddAccountResponse addAccount(
	AdvertiserAccount account) throws RemoteException, Exception
{
	AddAccountRequest request = new AddAccountRequest();

	request.setAccount(account);

	return CustomerManagementService.getService().addAccount(request);
}
```
```php
static function AddAccount(
	$account)
{

	$GLOBALS['Proxy'] = $GLOBALS['CustomerManagementProxy'];

	$request = new AddAccountRequest();

	$request->Account = $account;

	return $GLOBALS['CustomerManagementProxy']->GetService()->AddAccount($request);
}
```
```python
response=customermanagement_service.AddAccount(
	Account=Account)
```

## Requirements
Service: [CustomerManagementService.svc v13](https://clientcenter.api.bingads.microsoft.com/Api/CustomerManagement/v13/CustomerManagementService.svc)  
Namespace: https\://bingads.microsoft.com/Customer/v13  

