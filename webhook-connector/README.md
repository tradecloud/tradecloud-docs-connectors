---
description: >-
  Tradecloud triggers a webhook to notify the buyer or supplier the order
  (response) is new or has been updated.
---

# Webhook Connector

## Using the webhook

### Step 1. Tradecloud sends a webhook trigger to your webhook service

When an order \(response\) is new or has been changed at Tradecloud, we will trigger your webhook.

{% hint style="info" %}
You can either choose **GET** which will contain the **order id** as path or query parameter

Or you can choose **POST or PUT** which will contain the **order event** in a JSON body.
{% endhint %}

In case of GET,  the triggered webhook URL contains an order id parameter, for example:

```text
GET https://yourcompany.com/any/path/:orderId
```

### Step 2. Your webhook service fetches the actual order from Tradecloud

In case of a **GET webhook**, using the **order id** you can fetch the actual order from Tradecloud:

```text
GET https://api.accp.tradecloud1.com/order/:orderId
```

{% hint style="info" %}
[API v2 GET order OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order/specs.yaml#/order/getOrderByIdRoute)
{% endhint %}

```text
GET https://test.tradecloud.nl/api/v1/purchaseOrder/:legacyOrderId
```

{% hint style="info" %}
[API v1 GET purchaseOrder OpenAPI specification](https://test.tradecloud.nl/api/v1/docs#!/Purchase_order_API/getOrder)
{% endhint %}

In case of **POST** or **PUT** **webhook** you can use the **order event** inside the request JSON body:

{% hint style="info" %}
[POST/PUT webhook endpoint OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookPost)
{% endhint %}

{% hint style="warning" %}
When you **GET the order yourself** you will get **ALL** the order lines. 

When you **use the order event** it will **ONLY** contain the lines **affected** by the order event.
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

{% api-method method="get" host="https://yourcompany.com" path="/any/path/:orderId" %}
{% api-method-summary %}
Webhook with order id
{% endapi-method-summary %}

{% api-method-description %}
The GET webhook method is used to send the order id when the order \(response\) is new or has been updated.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="orderId" type="string" required=false %}
order identifier
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="orderId" type="string" required=false %}
order identifier
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
[GET webhook endpoint OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookGet)
{% endhint %}

{% api-method method="post" host="https://yourcompany.com" path="/any/path" %}
{% api-method-summary %}
Webhook with event
{% endapi-method-summary %}

{% api-method-description %}
The POST and PUT webhook method is used to send the order event when the order \(response\) is new or has been updated.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="Body" type="string" required=false %}
Order event JSON body
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```


```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
[POST/PUT webhook endpoint OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookPost)
{% endhint %}

{% hint style="info" %}
A **legacy** **order** will also contain the legacyOrderId, but no version.
{% endhint %}

## Next: configure the webhook

{% page-ref page="configure-the-webhook.md" %}





