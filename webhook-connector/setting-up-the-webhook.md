---
description: Setting up the webhook at the customer side
---

# Setting up the webhook

To receive a webhook trigger you will need:

* a **simple web service** reachable from the internet, which listens to some URL
* the web service should support **SSL** **only** and you will need a **SSL certificate**

{% hint style="warning" %}
Self-signed certificates are NOT supported
{% endhint %}

{% hint style="warning" %}
The web service should be configured to use **TLS v1.2** or **TLS v1.3**
{% endhint %}

{% hint style="info" %}
You can test the security level of your certificate at [SSL Labs](https://www.ssllabs.com/ssltest/)
{% endhint %}

* the web service should support **basic authentication** or a **static bearer token**
* the HTTP method should be either **POST** or **GET**

## Setting up the POST webhook

Your POST webhook must implement the POST order & shipment webhook OpenAPI specifications: 

{% hint style="info" %}
[POST order webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-webhook/specs.yaml#/order-webhook%20endpoints/webhookPost)

[POST shipment webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookPost)
{% endhint %}

## Setting up the GET webhook

Your GET webhook must implement the GET order & shipment webhook OpenAPI specifications: 

{% hint style="info" %}
[GET order webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-webhook/specs.yaml#/order-webhook%20endpoints/webhookGet)

[GET shipment webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookGet)
{% endhint %}

## Next: configure the webhook

{% page-ref page="configure-the-webhook.md" %}
