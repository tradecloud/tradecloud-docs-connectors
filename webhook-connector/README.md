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

- **POST** which will contain the **order event** or **shipment event** in a JSON body.
- **GET** which will contain the **order ID** or **shipment ID** as path or query parameter.

See [the API manual](https://docs.tradecloud1.com/api/introduction/api/webhook-vs-polling) about pro's and cons of either choice.
{% endhint %}

### Using the POST webhook

In case of a **POST** webhook you can use the **event** inside the request JSON body:

{% hint style="info" %}
[POST order webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost)

[POST shipment webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookPost)
{% endhint %}

{% hint style="warning" %}
When you **use the order event** it will **ONLY** contain the lines **affected** by the event.

When you **use the shipment event** it will contain **ALL** the lines and **ALL** the documents. 
You can filter new/changed lines and documents based on the `lastChangedAt` fields.
{% endhint %}

### Using the GET webhook

In case of a **GET** webhook, the triggered webhook URL contains an order id parameter, for example:

```text
GET https://yourcompany.com/any/order/path/:orderId
GET https://yourcompany.com/any/shipment/path/:shipmentId

or

GET HTTP://yourcompany.com/any/path?orderId=:orderId
GET HTTP://yourcompany.com/any/path?shipmentId=:shipmentId
```

#### Step 2. Your webhook service fetches the actual order or shipment from Tradecloud

When using the **GET webhook**, you must fetch the actual order or shipment from Tradecloud using the **order ID** or **shipment ID**:

```text
GET https://api.accp.tradecloud1.com/order/:orderId
GET https://api.accp.tradecloud1.com/shipment/:shipmentId
```

{% hint style="info" %}
[GET order OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order/specs.yaml#/order/getOrderByIdRoute)  
[GET shipment OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment/specs.yaml#/shipment/getShipmentByIdRoute)
{% endhint %}

{% hint style="warning" %}
When you **GET the order or shipment** you will get **ALL** the lines. 
You can filter new/changed lines and documents based on the `lastChangedAt` fields.
{% endhint %}

## Next: setting up the webhook

{% page-ref page="setting-up-the-webhook.md" %}
