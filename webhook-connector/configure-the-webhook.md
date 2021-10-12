---
description: Configurate the webhook in the Tradecloud portal
---

# Configure the webhook

## Configure your webhook in the Tradecloud1 portal

### Select Webhook

As a company admin configure the webhook in your company settings on the [Tradecloud1 platform](http://portal.tradecloud1.com):

![](<../.gitbook/assets/Blue sailboats webhook.png>)

* Select **My team** in the menu below your avatar.
* Select **Settings** in the page menu.
* Select **Webhook** in the Integration section.

### Select events to receive

A default set of events will be enabled. The actual set you want to receive wil be dependent on the capabilities of your integration and ERP system.

![](<../.gitbook/assets/Blue sailboats webhook events.png>)

### Configure method, url and credentials

![](<../.gitbook/assets/Blue sailboats webhook url.png>)

* Select **GET**,** POST** or **PUT **as HTTP method.
* Enter your webhook **URL**. 
  * **https** is required.
  * use **{orderId}** or **{legacyOrderId}** variables in the URL in case of **GET** method.
* Enter either** Basic authentication** username and password or a static **Bearer token.**

{% hint style="warning" %}
Use** {orderId} **when you use API version 2 on tradecloud1.com\
Use **{legacyOrderId} **when you use API version 1 on tradecloud.nl
{% endhint %}

{% hint style="info" %}
You can test webhook triggers using [webhook.site](https://webhook.site)\
Use bogus username and password.
{% endhint %}
