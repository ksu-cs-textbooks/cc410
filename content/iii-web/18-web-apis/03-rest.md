---
title: "REST"
weight: 15
pre: "3. "
---

Thus far, we've mainly discussed the [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) architectural style for web APIs, since it has become commonly used on the internet today. However, let's briefly look at one other architectural style for web APIs and see how it compares to REST. 

![SOAP](/cc410/images/18/soap.png)[^1]

[^1]: https://commons.wikimedia.org/w/index.php?title=File:Webservice_xrpc.png&oldid=460901418

## SOAP

The [Simple Object Access Protocol](https://en.wikipedia.org/wiki/SOAP), or SOAP, is a standardized protocol for exchanging information between web servers and clients that was first developed in 1998 (a few years before REST was first written about). So, unlike REST, which is simply an architectural style without an underlying standard, SOAP was designed to have a specific standard and implementation. 

SOAP was designed to use [XML](https://en.wikipedia.org/wiki/XML) to transfer data between the client and the server, and includes a specific three-part message structure consisting of an envelope, a set of encoding rules, and a way to represent the actual endpoint requests (function calls) and responses. It uses a specific [XML Schema](https://en.wikipedia.org/wiki/XML_schema) to define the structure of those messages.

[Wikipedia](https://en.wikipedia.org/wiki/SOAP) includes a short example showing how to use SOAP to request the stock price for a stock symbol:

```xml
POST /InStock HTTP/1.1
Host: www.example.org
Content-Type: application/soap+xml; charset=utf-8
Content-Length: 299
SOAPAction: "http://www.w3.org/2003/05/soap-envelope"

<?xml version="1.0"?>
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:m="http://www.example.org">
  <soap:Header>
  </soap:Header>
  <soap:Body>
    <m:GetStockPrice>
      <m:StockName>T</m:StockName>
    </m:GetStockPrice>
  </soap:Body>
</soap:Envelope>
```

Notice that it includes a `SOAPAction` header in the HTTP request, as well as lots of XML in the body of the request. The server would respond with a similarly structured message containing the current stock price of the stock.

## Comparison to REST

While SOAP does have several advantages, such as defining a standardized protocol that can be used with any web service that properly implements it, it also has several disadvantages. Most notably, the data must be encoded into XML, and the resulting XML must be parsed before it can be used. While XML and JSON are both well structured representations of data, the verbosity of XML compared to JSON makes it slower to send, receive and parse. 

Likewise, since SOAP requires additional structure and rules to be added to the HTTP request itself, it makes it more difficult to work with than it seems. Unlike REST, SOAP itself doesn't specify the structure of the endpoints and how to manage state - each application implementing SOAP may use an entirely different structure for the various endpoints used to access, update, and delete resources. REST, on the other hand, doesn't specify exactly how it must be done, but it does lead toward a simple, more usable model for interacting with the server. 

Because of this, most web APIs today follow a RESTful architectural style built directly upon HTTP, instead of using SOAP, even though SOAP is an officially supported web protocol. 
