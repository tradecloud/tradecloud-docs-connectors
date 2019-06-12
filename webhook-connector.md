---
description: >-
  Tradecloud triggers a webhook to notify the buyer or supplier the order
  (response) is new or has been updated.
---

# Webhook Connector

## Using the webhook

### 1. Tradecloud sends a webhook trigger to your webhook service

When an order \(response\) is new or has been changed at Tradecloud, we will trigger your webhook service.

The triggered webhook URL contains an orderId parameter, for example:

```text
GET https://company.com/any/path/:orderId
```

### 2. Your webhook service fetches the actual order from Tradecloud

Using the orderId, you may fetch the actual order from Tradecloud, for example:

```text
GET https://test.tradecloud.nl/api/v1/purchaseOrder/:orderId
```

{% hint style="info" %}
[API v1 GET purchaseOrder specification](https://test.tradecloud.nl/api/v1/docs#!/Purchase_order_API/getOrder)
{% endhint %}

## Setting up your webhook service

To receive a webhook trigger you will need:

* a **simple web service** reachable from the internet, which listens to some URL
* the web service should use **SSL** and you need a **SSL certificate**
* the web service should support **basic authentication**
* the HTTP method should be **GET**
* the URL should contain a parameter **orderId**

{% api-method method="get" host="" path="https://company.com/any/path/:orderId" %}
{% api-method-summary %}
Webhook method
{% endapi-method-summary %}

{% api-method-description %}
The webhook method is used to notify the buyer/supplier the order \(response\) is new or has been updated.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="orderId" type="string" required=true %}
Tradecloud order identifier
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="body" type="string" required=false %}
The request will contain a body, but this is in beta and the json structure will change.
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
You can test the security level of your SSL certificate at [SSL Labs](https://www.ssllabs.com/ssltest/)
{% endhint %}

## Configure your webhook in Tradecloud1

As a company admin you may configure a webhook in your company profile on the [Tradecloud1 platform](http://portal.tradecloud1.com/):

![](.gitbook/assets/tradecloud1-company-webhook-configuration.png)

* Type: select Webhook
* HTTP method: select GET \(POST is not yet supported\)
* URL: enter your webhook URL. https and {orderId} are required.
* Username: enter the user name as configured in your webhook service
* Password: enter the password as configured in your webhook service



