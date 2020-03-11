---
description: CSV (RFC 4180) buyer side specification
---

# CSV Buyer Specification

You can find the supplier side specification in this Google Spreadsheet:

### [CVS Connector buyer specification](https://docs.google.com/spreadsheets/d/1bdKcYRUDka2PbEPo0OwdXsBGuACwpz7hWatV45zZTjA)

{% hint style="info" %}
Gmail/GSuite account and access authorization required
{% endhint %}

You may find these tabs below in the spreadsheet:

| Tab | Description |
| :--- | :--- |
| Standard | General rules |
| Flow | Incoming and outgoing flows and the folders used. |
| Order fields | Fields specification of the outgoing orders |
| Order examples | An example of an outgoing order |
| Response fields | Fields specification of the incoming order responses |
| Response example | An example of an incoming order response |

{% hint style="info" %}
In the outgoing orders, always provide all mandatory fields

An error report may be generated in \outgoing\error\order-yyyyddmm-hhmm.txt
{% endhint %}

### Buyer Examples

{% file src="../../.gitbook/assets/tradecloud-buyer-example-outgoing-order.csv" %}

{% file src="../../.gitbook/assets/tradecloud-buyer-example-incoming-order-response.csv" %}

