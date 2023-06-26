---
description: >-
  Tradecloud triggers a webhook to notify the buyer or supplier the order, response or shipment is new or has been updated.
---

# Webhook Connector

## Using the webhook

### Step 1. Tradecloud sends a webhook trigger to your webhook service

When an order, response or shipment is new or has been changed at Tradecloud, we will trigger your webhook.

{% hint style="info" %}
You can either choose **GET** which will contain the **orderId** or **shipmentId** as path or query parameter

Or you can choose **POST or PUT** which will contain the **order event**, **order document event** or **shipment event** in a JSON body.
{% endhint %}

In case of GET,  the triggered webhook URL contains an `orderId` or `shipmentId` parameter, for example:

```text
GET https://yourcompany.com/any/path/:orderId
```

### Step 2. Your webhook service fetches the actual order from Tradecloud

In case of a **GET webhook**, using the **orderId**, **legacyOrderId** or **shipmentId** you can fetch the actual order from Tradecloud:

```text
GET https://api.accp.tradecloud1.com/order/:orderId
```

{% hint style="info" %}
[API v2 GET order OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order/specs.yaml#/order/getOrderByIdRoute)
{% endhint %}

```text
GET https://api.accp.tradecloud1.com/shipment/:shipmentId
```

{% hint style="info" %}
[API v2 GET shipment OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment/specs.yaml#/shipment/getShipmentByIdRoute)
{% endhint %}

In case of **POST** or **PUT** **webhook** you can use the **order event** or **shipment event** inside the request JSON body:

{% hint style="info" %}
[POST/PUT order webhook endpoint OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookPost)
{% endhint %}

{% hint style="info" %}
[POST/PUT shipment webhook endpoint OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookPost)
{% endhint %}

{% hint style="warning" %}
When you **GET the order yourself** you will get **ALL** the order lines. 

When you **use the order event** it will **ONLY** contain the lines **affected** by the order event.

When you either GET the shipment or use the shipment event, it will always contain all the shipment lines.
{% endhint %}

## Setting up your webhook service

To receive a webhook trigger you will need:

* a **simple web service** reachable from the internet, which listens to some URL
* the web service should support **SSL** **only** and you will need a **SSL certificate**

{% hint style="warning" %}
Self-signed certificates are NOT supported
{% endhint %}

* the web service should be configured to use **TLS v1.2**

{% hint style="info" %}
You can test the security level of your certificate at [SSL Labs](https://www.ssllabs.com/ssltest/)
{% endhint %}

* the web service should support **basic authentication**
* the HTTP method should be either **GET, POST** or **PUT**

## Configure your webhook in Tradecloud1

As a company admin you may configure an order, order document and shipment webhooks in your company profile on the [Tradecloud1 platform](http://portal.tradecloud1.com/):

![](.gitbook/assets/tradecloud1-company-webhook-configuration.png)

* Type: select Webhook
* HTTP method: select **GET**, **POST** or **PUT**
* URL: enter your webhook URL. **https** and in case of GET **{orderId}** is required.
* Username: enter the **username** as configured in your webhook service
* Password: enter the **password** as configured in your webhook service
* Bearer token: enter the **bearer token**, as alternative for Username & Password, as configured in your webhook service

{% hint style="warning" %}
Use **{orderId}** when you use API version 2 on tradecloud1.com  
Use **{legacyOrderId}** when you use API version 1 on tradecloud.nl
{% endhint %}

{% hint style="info" %}
You can test webhook triggers using [webhook.site](https://webhook.site)  
Use bogus username and password.
{% endhint %}



