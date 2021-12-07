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
The web service should be configured to use **TLS v1.2**
{% endhint %}

{% hint style="info" %}
You can test the security level of your certificate at [SSL Labs](https://www.ssllabs.com/ssltest/)
{% endhint %}

* the web service should support **basic authentication** or **static bearer token**
* the HTTP method should be either **GET, POST** or **PUT**

{% api-method method="post" host="https://yourcompany.com" path="/any/path" %}
{% api-method-summary %}
Webhook with event
{% endapi-method-summary %}

{% api-method-description %}
The POST and PUT webhook method is used to send the order or shipment event when the order or shipment is new or has been updated.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="Body" type="string" required=false %}
Order or shipment event JSON body
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
{% endapi-method-response-example-description %}
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
[POST/PUT order webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookPost)

[POST/PUT shipment webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookPost)
{% endhint %}


{% api-method method="get" host="https://yourcompany.com" path="/any/path/:orderId" %}
{% api-method-summary %}
Webhook with id
{% endapi-method-summary %}

{% api-method-description %}
The GET webhook method is used to send the order id or shipment id when the order or shipment is new or has been updated.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="orderId" type="string" required=false %}
order identifier
{% endapi-method-parameter %}
{% api-method-parameter name="shipmentId" type="string" required=false %}
order identifier
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
{% endapi-method-response-example-description %}
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
[GET order webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookGet)

[GET shipment webhook OpenAPI specification][https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookGet]
{% endhint %}

## Next: configure the webhook

{% page-ref page="configure-the-webhook.md" %}
