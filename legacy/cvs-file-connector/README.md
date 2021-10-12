---
description: CSV (RFC 4180) files using a .NET connector installed at the customer premises
---

# CVS File Connector

{% hint style="warning" %}
Deprecated connector on the Tradecloud legacy platform (tradecloud.nl)
{% endhint %}

Use the CSV file connector in case you want to exchange new and changed orders and order responses using the Tradecloud proprietary CSV format and shared folders on your on premise server as transport.

|                                                    |                                                                                                                                                                                                                   |
| -------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Data Format                                        | [RFC 4180](https://tools.ietf.org/html/rfc4180)                                                                                                                                                                   |
| Message types                                      | Order (new and changed), Order response (new and changed)                                                                                                                                                         |
| Specifications                                     | <p><a href="csv-buyer-specification.md">CVS Buyer Specification</a></p><p><a href="csv-supplier-specification.md">CSV Supplier Specification</a> <br>(Gmail/GSuite account and access authorization required)</p> |
| Transport                                          | Shared folders on your on premise server                                                                                                                                                                          |
| [Requirements](csv-file-connector-requirements.md) | On premise installation, .NET 4.5 framework, outbound tcp/ip port 5670                                                                                                                                            |
| Availability                                       | Available for buyer and supplier sides                                                                                                                                                                            |
