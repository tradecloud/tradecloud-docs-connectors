---
description: Setting up the webhook at the customer side
---

# Setting up the webhook

To receive a webhook trigger you will need:

* a **simple web service **reachable from the internet, which listens to some URL
* the web service should support **SSL** **only** and you will need a **SSL certificate**

{% hint style="warning" %}
Self-signed certificates are NOT supported
{% endhint %}

* the web service should be configured to use** TLS v1.2**

{% hint style="info" %}
You can test the security level of your certificate at [SSL Labs](https://www.ssllabs.com/ssltest/)
{% endhint %}

* the web service should support **basic authentication**
* the HTTP method should be either **GET, POST **or** PUT**

{% swagger baseUrl="https://yourcompany.com" path="/any/path" method="post" summary="Webhook with event" %}
{% swagger-description %}
The POST and PUT webhook method is used to send the order event when the order (response) is new or has been updated.
{% endswagger-description %}

{% swagger-parameter in="body" name="Body" type="string" %}
Order event JSON body
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```


```
{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
[POST/PUT webhook endpoint OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookPost)
{% endhint %}

{% swagger baseUrl="https://yourcompany.com" path="/any/path/:orderId" method="get" summary="Webhook with id" %}
{% swagger-description %}
The GET webhook method is used to send the order id when the order (response) is new or has been updated.
{% endswagger-description %}

{% swagger-parameter in="path" name="orderId" type="string" %}
order identifier
{% endswagger-parameter %}

{% swagger-parameter in="query" name="orderId" type="string" %}
order identifier
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
[GET webhook endpoint OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookGet)
{% endhint %}

## Next: configure the webhook

{% content-ref url="configure-the-webhook.md" %}
[configure-the-webhook.md](configure-the-webhook.md)
{% endcontent-ref %}

