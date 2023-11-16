---
description: Setting up the webhook at the customer side
---

# Setting up the webhook

To receive a webhook trigger you will need:

* A **simple web service** reachable from the internet, which listens to some URL.
* The web service should support **SSL** **only** and you will need a **SSL certificate**.

{% hint style="warning" %}
The web service should be configured to use **TLS v1.2** or **TLS v1.3**. 

Self-signed certificates are NOT supported.
{% endhint %}

{% hint style="info" %}
You can test the security level of your certificate at [SSL Labs](https://www.ssllabs.com/ssltest/)
{% endhint %}

* The web service should support **basic authentication** or a **static bearer token**.
* The HTTP method should be either **POST** or **GET**.

## Setting up the POST order webhook

Your POST **order** webhook must implement the POST order webhook OpenAPI specifications: 

{% hint style="info" %}
[POST order webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost)
{% endhint %}

* Use the `orderEvent` field when using the **native** delivery schedule.
* Use the `simpleOrderEvent` field when using the **simple**  delivery schedule.
* Use the `orderDocumentsEvent` field when using order documents events.

See [the API manual](https://docs.tradecloud1.com/api/introduction/api/delivery-schedule) to read about the native versus the simple delivery schedule.

{% hint style="warning" %}
When using the **order event** it will **ONLY** contain the order lines **affected** by the event.
{% endhint %}

When using the `orderDocumentsEvent` field, you must [download the document](https://docs.tradecloud1.com/api/processes/order/buyer/receive/download-document) as the document content is not embedded in the event itself.

## Setting up the POST shipment webhook

Your POST **shipment** webhook must implement the POST shipment webhook OpenAPI specifications: 

{% hint style="info" %}
[POST shipment webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookPost)
{% endhint %}

{% hint style="warning" %}
When you **use the shipment event** it will contain **ALL** the lines and **ALL** the documents. 
You can filter new/changed lines and documents based on the `lastUpdatedAt` fields.
{% endhint %}

## Setting up the GET order webhook

Your GET order webhook must implement the GET order webhook OpenAPI specification: 

{% hint style="info" %}
[GET order webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookGet)
{% endhint %}

You must also implement the GET order OpenAPI specification to fetch the actual order: 

{% hint style="info" %}
[GET order OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order/specs.yaml#/order/getOrderByIdRoute)
{% endhint %}

{% hint style="warning" %}
When you **GET the order** you will get **ALL** the lines. 
You can filter new/changed order lines based on the `lastChangedAt` fields.
{% endhint %}

## Setting up the GET shipment webhook

Your GET shipment webhook must implement the GET order webhook OpenAPI specification: 

{% hint style="info" %}
[GET shipment webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookGet)
{% endhint %}

{% hint style="warning" %}
When you **GET the shipment** you will get **ALL** the lines. 
You can filter new/changed shipment lines and documents based on the `lastChangedAt` fields.
{% endhint %}

You must also implement the GET shipment OpenAPI specification to fetch the actual shipment: 

{% hint style="info" %}
[GET shipment OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment/specs.yaml#/shipment/getShipmentByIdRoute)
{% endhint %}

## Next: configure the webhook

{% page-ref page="configure-the-webhook.md" %}
