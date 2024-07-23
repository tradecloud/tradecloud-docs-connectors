---
description: >-
  Tradecloud triggers a webhook to notify the buyer or supplier the order or
  shipment is new or has been updated.
---

# Webhook Connector

## Using the webhook

### Tradecloud sends a webhook trigger to your webhook service

When an order or shipment is new or has been changed at Tradecloud, we will trigger your webhook.

{% hint style="info" %}
You can either choose between the **POST** or **GET** webhook: 

- **POST** will contain the **order**, **order documents** or **shipment event** in a JSON or tXML body.
- **GET** will contain the **order ID** or **shipment ID** as path or query parameter.

See [the API manual](https://docs.tradecloud1.com/api/introduction/api/webhook-vs-polling) to read about pro's and cons of either choice.
{% endhint %}

### Using the POST webhook

In case of a **POST** webhook you can use the data of the **event** inside the request body.

#### Your webhook service must download the document content from Tradecloud

If you are receiving **order documents events**, the POST request body contains a document `objectId`. You must [download the document](https://docs.tradecloud1.com/api/processes/order/buyer/receive/download-document) as the document content is not embedded in the event itself.

### Using the GET webhook

In case of a **GET** webhook, the triggered webhook URL contains an **order ID** or **shipment ID** parameter, for example:

```text
GET https://yourcompany.com/any/order/path/:orderId
GET https://yourcompany.com/any/shipment/path/:shipmentId
```

#### Your webhook service fetches the actual order or shipment from Tradecloud

When using the **GET webhook**, you must fetch the actual order or shipment from Tradecloud using the **order ID** or **shipment ID**:

```text
GET https://api.accp.tradecloud1.com/order/:orderId
GET https://api.accp.tradecloud1.com/shipment/:shipmentId
```

## Next: setting up the webhook

{% page-ref page="setting-up-the-webhook.md" %}
