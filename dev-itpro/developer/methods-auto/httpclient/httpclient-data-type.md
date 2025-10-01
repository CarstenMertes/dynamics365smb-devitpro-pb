---
title: "HttpClient data type"
description: "Provides a data type for sending HTTP requests and receiving HTTP responses from a resource identified by a URI."
ms.author: solsen
ms.date: 08/08/2025
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# HttpClient data type
> **Version**: _Available or changed with runtime version 1.0._

Provides a data type for sending HTTP requests and receiving HTTP responses from a resource identified by a URI.



## Instance methods
The following methods are available on instances of the HttpClient data type.

|Method name|Description|
|-----------|-----------|
|[AddCertificate(Text [, Text])](httpclient-addcertificate-string-string-method.md)|Adds a certificate to the HttpClient class.|
|[AddCertificate(SecretText [, SecretText])](httpclient-addcertificate-secrettext-secrettext-method.md)|Adds a certificate as a SecretText to the HttpClient class.|
|[Clear()](httpclient-clear-method.md)|Sets the HttpClient variable to the default value.|
|[DefaultRequestHeaders()](httpclient-defaultrequestheaders-method.md)|Gets the default request headers which should be sent with each request.|
|[Delete(Text, var HttpResponseMessage)](httpclient-delete-method.md)|Sends a DELETE request to delete the resource identified by the request URL.|
|[Get(Text, var HttpResponseMessage)](httpclient-get-method.md)|Sends a GET request to get the resource identified by the request URL.|
|[GetBaseAddress()](httpclient-getbaseaddress-method.md)|Gets the base address of Uniform Resource Identifier (URI) of the Internet resource used when sending requests.|
|[Patch(Text, HttpContent, var HttpResponseMessage)](httpclient-patch-method.md)|Sends a PATCH request to the specified URI as an asynchronous operation.|
|[Post(Text, HttpContent, var HttpResponseMessage)](httpclient-post-method.md)|Sends a POST request to the specified URI as an asynchronous operation.|
|[Put(Text, HttpContent, var HttpResponseMessage)](httpclient-put-method.md)|Sends a PUT request to the specified URI as an asynchronous operation.|
|[Send(HttpRequestMessage, var HttpResponseMessage)](httpclient-send-method.md)|Sends an HTTP request as an asynchronous operation.|
|[SetBaseAddress(Text)](httpclient-setbaseaddress-method.md)|Sets the base address of Uniform Resource Identifier (URI) of the Internet resource used when sending requests.|
|[Timeout([Duration])](httpclient-timeout-method.md)|Gets or sets the duration in milliseconds to wait before the request times out.|
|[UseDefaultNetworkWindowsAuthentication()](httpclient-usedefaultnetworkwindowsauthentication-method.md)|Sets the HttpClient credentials to use the default network credentials for Windows authentication. If this method is invoked after any HTTP request has started; a runtime error occurs.|
|[UseResponseCookies(Boolean)](httpclient-useresponsecookies-method.md)|If true, the client automatically attaches cookies received in the response to all subsequent requests.|
|[UseServerCertificateValidation(Boolean)](httpclient-useservercertificatevalidation-method.md)|If true, the client validates the server certificate for all HTTP requests. If false, it skips validation.|
|[UseWindowsAuthentication(Text, Text [, Text])](httpclient-usewindowsauthentication-string-string-string-method.md)|Sets the HttpClient credentials to use the specified network credentials for Windows authentication. If this method is invoked after any HTTP request has started; a runtime error occurs.|
|[UseWindowsAuthentication(SecretText, SecretText [, SecretText])](httpclient-usewindowsauthentication-secrettext-secrettext-secrettext-method.md)|Sets the HttpClient credentials to use the specified network credentials for Windows authentication. If this method is invoked after any HTTP request has started; a runtime error occurs.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The supported security protocols are controlled by the **SecurityProtocol** configuration setting. For more information, see [Microsoft Dynamics 365 Business Central Server Configuration](../../../administration/configure-server-instance.md#Compatibility).

## Ways that HttpClient calls can fail

All of the methods HttpClient.Delete, HttpClient.Get, HttpClient.Post, HttpClient.Put, or HttpClient.Send in the HttpClient data type can fail and return false. 

[!INCLUDE[allowhttpclientnote](../../includes/include-http-call-failure-reasons.md)]


[!INCLUDE[httpCallErrors](../../../includes/include-http-call-errors-note.md)]

[!INCLUDE[allowhttpclientnote](../../../includes/include-http-allowhttpclient-note.md)]

## Mock outbound HttpClient web service calls during testing

Testability of AL code that interacts with external web services is enhanced when the responses from these services can be simulated in AL, eliminating the need to configure actual endpoints. Mocking outbound web calls is useful when testing that your code is capable of handling a wide range of possible responses, and allowing you to track outbound traffic during the test executions. Learn more in [Mock outbound HttpClient web service calls during testing](../../devenv-httpclient-mock-outbound-calls.md). 

## Telemetry

[!INCLUDE[httpclientTelemetry](../../../includes/telemetry-outgoing-http.md)] 

For more information, see [Outgoing Web Service Request Telemetry](../../../administration/telemetry-webservices-outgoing-trace.md). 

### Troubleshoot errors

[!INCLUDE[httpclientErrors](../../../includes/errors-outgoing-http.md)] 

#### HTTP status codes
[!INCLUDE[httpStatusCodes](../../../includes/include-http-status-codes.md)]

#### Common HTTP status error codes
[!INCLUDE[httpStatusErrorCodes](../../../includes/include-http-status-error-codes.md)]


## Performance considerations

[!INCLUDE[httpclientPerformance](../../../includes/performance-outgoing-http.md)]


## Related information
[Call external services with the HttpClient data type](../../devenv-httpclient.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[Outgoing Web Service Request Telemetry](../../../administration/telemetry-webservices-outgoing-trace.md)  
[Mock outbound HttpClient web service calls during testing](../../devenv-httpclient-mock-outbound-calls.md)  
