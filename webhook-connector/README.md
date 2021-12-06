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
You can either choose between the **POST** / **PUT** or **GET** webhook.

**POST or PUT** which will contain the **order event** or **shipment event** in a JSON body.

**GET** which will contain the **order ID** or **shipment ID** as path or query parameter.

See [the API manual](https://tradecloud.gitbook.io/api/api/webhook-vs-polling) about pro's and cons of either choice.
{% endhint %}

{% hint style="warning" %}
When you **use the event** it will **ONLY** contain the lines **affected** by the event.

When you **GET the order yourself** you will get **ALL** the lines
{% endhint %}

In case of **POST** or **PUT** **webhook** you can use the **event** inside the request JSON body:

{% hint style="info" %}
[POST/PUT order webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookPost)

POST/PUT shipment webhook OpenAPI specification TO DO
{% endhint %}

In case of GET,  the triggered webhook URL contains an order id parameter, for example:

```text
GET https://yourcompany.com/any/order/path/:orderId
GET https://yourcompany.com/any/shipment/path/:shipmentId

or

GET HTTP://yourcompany.com/any/path?orderId=:orderId
GET HTTP://yourcompany.com/any/path?shipmentId=:shipmentId
```

### Step 2. Your webhook service fetches the actual order or shipment from Tradecloud

In case of a **GET webhook**, using the **order ID** or **shipment ID** you can fetch the actual order or shipment from Tradecloud:

```text
GET https://api.accp.tradecloud1.com/order/:orderId
GET https://api.accp.tradecloud1.com/shipment/:shipmentId
```

{% hint style="info" %}
[GET order OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order/specs.yaml#/order/getOrderByIdRoute)  
GET shipment OpenAPI specification TO DO
{% endhint %}

## Next: setting up the webhook

{% page-ref page="setting-up-the-webhook.md" %}

