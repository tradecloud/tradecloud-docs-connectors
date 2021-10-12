---
description: >-
  This page describes the configurations needed on Tradecloud side to allow
  users to login using Azure AD
---

# Azure AD Connector - Tradecloud Configuration

{% hint style="info" %}
This configuration will be added by Tradecloud support.
{% endhint %}

## Frontend Configuration

Configuration file for SSO mappings is  `src/app/auth/routes/login/state/sso.connections.ts` .

src/app/auth/routes/login/state/sso.connections.ts example:

```
export const azureAppMappings: AzureConnectionMappings = {  
  tradecloud1prod: {
    clientId: 'HIDDEN',
    tenantId: 'HIDDEN',
  },
  tradecloud1accp: {
    clientId: 'HIDDEN',
    tenantId: 'HIDDEN',
  }
};

const globalDomainMappings: SsoConnectionMap = {
  'tradecloud1.onmicrosoft.com': 'tradecloud1prod'
};

const connectionsByEmail: { [email: string]: AzureConnection } = {
  'user@tradecloud1accp.onmicrosoft.com': 'tradecloud1accp'
};

```



Here keys are the email domains and the values are the connection names. Make sure you have added clientId and tenantId for the connection name. **Connection names are just logical keys to make it easy to organize configurations**.

You can override the global domain configuration and have it specific to a user.  Add the key as the email address in the `connectionsByEmail` map and the value as the connection name which corresponds to the AD environment to which the user belongs.

## Microservices Configuration

Similar configuration needs to be added to the application.conf in **both** **authentication and user** microservices. Here is a configuration example:

```
sso {
   domainMapping = [
     {
        domain = "tradecloud1.onmicrosoft.com"
        companyId =  "HIDDEN"
        tenantId =  "HIDDEN"
     },
     {
        domain = "tradecloud1accp.onmicrosoft.com"
        companyId =  "HIDDEN"
        tenantId =  "HIDDEN"
     }
   ]
}
```

This is a list of SSO mappings corresponding to each AD environment for which we want to enable SSO. Each element contains

* domain - the email domain 
* companyId - Tradecloud company id to which the user belongs
*  tenantId - Azure AD tenant Id. This is used to validate the JWT. 

path of application.conf in authentication microservice - authentication/src/main/resources/application.conf

path of application.conf in user microservice - user/src/main/resources/application.conf
