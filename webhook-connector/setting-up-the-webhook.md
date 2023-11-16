---
description: Setting up the webhook at the customer side
---

# Setting up the webhook

To receive a webhook trigger you will need:

* A simple web service reachable from the internet, which listens to some URL.
* The web service should support **SSL** only and you will need a SSL certificate.
* The web service should be configured to use **TLS v1.2** or **v1.3**. 
* Self-signed certificates are NOT supported.
* The web service should support **basic authentication** or a **static bearer token**.
* The supported HTTP method should be either **POST** or **GET**.

{% hint style="info" %}
You can test the security level of your certificate at [SSL Labs](https://www.ssllabs.com/ssltest/)
{% endhint %}

## Setting up the POST order webhook

Your webhook must implement the POST order webhook OpenAPI specifications: 

{% hint style="info" %}
[POST order webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost)
{% endhint %}

* Use the `orderEvent` field when using the **native** delivery schedule.
* Use the `simpleOrderEvent` field when using the **simple**  delivery schedule.
* Use the `orderDocumentsEvent` field when using order documents events.

See [the API manual](https://docs.tradecloud1.com/api/introduction/api/delivery-schedule) to read about the native versus the simple delivery schedule.

{% hint style="warning" %}
An `orderEvent` or `simpleOrderEvent` will **only** contain the order lines **affected** by the event.
{% endhint %}

When using the `orderDocumentsEvent` field, you must [download the document](https://docs.tradecloud1.com/api/processes/order/buyer/receive/download-document) as the document content is not embedded in the event itself.

## Setting up the POST shipment webhook

Your webhook must implement the POST shipment webhook OpenAPI specifications: 

{% hint style="info" %}
[POST shipment webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookPost)
{% endhint %}

{% hint style="warning" %}
THe shipment even will contain **all** the lines and documents. 
You can filter new/changed lines and documents based on the `lastUpdatedAt` fields.
{% endhint %}

When using a `documents` field, you must [download the document](https://docs.tradecloud1.com/api/processes/shipment/buyer/receive/download-document) as the document content is not embedded in the event itself.

## Setting up the GET order webhook

Your webhook must implement the GET order webhook OpenAPI specification: 

{% hint style="info" %}
[GET order webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookGet)
{% endhint %}

You must fetch the actual order according to the GET order OpenAPI specification: 

{% hint style="info" %}
[GET order OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order/specs.yaml#/order/getOrderByIdRoute)
{% endhint %}

{% hint style="warning" %}
The order will contain **all** the lines. 
You can filter new/changed order lines based on the `lastUpdatedAt` fields.
{% endhint %}

## Setting up the GET shipment webhook

Your webhook must implement the GET order webhook OpenAPI specification: 

{% hint style="info" %}
[GET shipment webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookGet)
{% endhint %}

You must fetch the actual shipment according to the GET shipment OpenAPI specification: 

{% hint style="info" %}
[GET shipment OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment/specs.yaml#/shipment/getShipmentByIdRoute)
{% endhint %}

{% hint style="warning" %}
The shipment will contain **all** the lines. 
You can filter new/changed shipment lines and documents based on the `lastUpdatedAt` fields.
{% endhint %}

## Next: configure the webhook

{% page-ref page="configure-the-webhook.md" %}
