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
You can either choose GET which will contain the order id as path or query parameter

Or you can choose POST or PUT which will contain the order event in a JSON body.
{% endhint %}

In case of GET,  the triggered webhook URL contains an order id parameter, for example:

```text
GET https://yourcompany.com/any/path/:orderId
```

### Step 2. Your webhook service fetches the actual order from Tradecloud

In case of **GET**, using the order id, you can fetch the actual order from Tradecloud:

```text
GET https://api.accp.tradecloud1.com/order/:orderId
```

{% hint style="info" %}
[API v2 GET order specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order/specs.yaml#/order/getOrderByIdRoute)
{% endhint %}

```text
GET https://test.tradecloud.nl/api/v1/purchaseOrder/:orderId
```

{% hint style="info" %}
[API v1 GET purchaseOrder specification](https://test.tradecloud.nl/api/v1/docs#!/Purchase_order_API/getOrder)
{% endhint %}

In case of **POST** or **PUT** you can use the order event inside the request JSON body.

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

{% api-method method="get" host="" path="/any/path/:orderId" %}
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

{% api-method method="post" host="" path="/any/path" %}
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
The webhook body is equal to the [Find order by id](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order/specs.yaml#/order/getOrderByIdRoute) response body  
The body will ONLY contain the lines affected by the order event.
{% endhint %}

{% hint style="info" %}
A **legacy** **order** will also contain the legacyOrderId, but no version.
{% endhint %}

## Configure your webhook in Tradecloud1

As a company admin you may configure a webhook in your company profile on the [Tradecloud1 platform](http://portal.tradecloud1.com/):

![](.gitbook/assets/tradecloud1-company-webhook-configuration.png)

* Type: select Webhook
* HTTP method: select **GET**, **POST** or **PUT**
* URL: enter your webhook URL. **https** and either **{orderId}** or **{legacyOrderId}** are required.
* Username: enter the **username** as configured in your webhook service
* Password: enter the **password** as configured in your webhook service

{% hint style="warning" %}
Use **{orderId}** when you use API version 2 on tradecloud1.com  
Use **{legacyOrderId}** when you use API version 1 on tradecloud.nl
{% endhint %}

{% hint style="info" %}
You can test webhook triggers using [webhook.site](https://webhook.site)  
Use bogus username and password.
{% endhint %}



