---
description: >-
  Tradecloud triggers a webhook to notify the buyer or supplier the order or
  shipment is new or has been updated.
---

# Webhook Connector

## Using the webhook

### Step 1. Tradecloud sends a webhook trigger to your webhook service

When an order or shipment is new or has been changed at Tradecloud, we will trigger your webhook.

{% hint style="info" %}
You can either choose between the **POST** or **GET** webhook: 

- **POST** which will contain the **order event**, **order documents event** or **shipment event** in a JSON body.
- **GET** which will contain the **order ID** or **shipment ID** as path or query parameter.

See [the API manual](https://docs.tradecloud1.com/api/introduction/api/webhook-vs-polling) to read about pro's and cons of either choice.
{% endhint %}

### Using the POST webhook

In case of a **POST** webhook you can use the **event** inside the request JSON body.

#### Step 2. Your webhook service downloads the actual document from Tradecloud

When using the **order documents event** in the request JSON body, you must [download the document](https://docs.tradecloud1.com/api/processes/order/buyer/receive/download-document) as the document content is not embedded in the event.

### Using the GET webhook

In case of a **GET** webhook, the triggered webhook URL contains an order id parameter, for example:

```text
GET https://yourcompany.com/any/order/path/:orderId
GET https://yourcompany.com/any/shipment/path/:shipmentId
```

#### Step 2. Your webhook service fetches the actual order or shipment from Tradecloud

When using the **GET webhook**, you must fetch the actual order or shipment from Tradecloud using the **order ID** or **shipment ID**:

```text
GET https://api.accp.tradecloud1.com/order/:orderId
GET https://api.accp.tradecloud1.com/shipment/:shipmentId
```

## Next: setting up the webhook

{% page-ref page="setting-up-the-webhook.md" %}
