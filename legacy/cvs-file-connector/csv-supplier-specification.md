---
description: CSV (RFC 4180) supplier side  specification
---

# CSV Supplier Specification

You can find the supplier side specification in this Google Spreadsheet:

### [CSV Connector supplier specification](https://docs.google.com/spreadsheets/d/1mCnIehWQfn96BHgeXR7sYbsmE9isLJkDFyjKfVpt-ZE)

{% hint style="info" %}
Gmail/GSuite account and access authorization required
{% endhint %}

You may find these tabs below in the spreadsheet:

| Tab | Description |
| :--- | :--- |
| Standard | General rules |
| Flow | Incoming and outgoing flows and the folders used. |
| Order fields | Fields specification of the incoming orders |
| Order examples | An example of an incoming order |
| Response fields | Fields specification of the outgoing order responses |
| Response example | An example of an outgoing order response |

{% hint style="info" %}
In the outgoing order responses, always provide all mandatory fields.

An error report may be generated in \outgoing\error\response-yyyyddmm-hhmm.txt
{% endhint %}

### Supplier Examples

{% file src="../../.gitbook/assets/tradecloud-supplier-example-incoming-order.csv" %}

{% file src="../../.gitbook/assets/tradecloud-supplier-example-outgoing-order-response.csv" %}

