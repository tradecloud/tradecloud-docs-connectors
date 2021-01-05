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

Currently, src/app/auth/routes/login/state/sso.connections.ts has the following mappings

```text
export const azureAppMappings: AzureConnectionMappings = {  
  tradecloud1prod: {
    clientId: '99f40fa5-fbed-4d23-b8ef-4e2d25205eff',
    tenantId: 'fc2e432f-1e78-4e28-ac62-33861e815454',
  },
  damenaccp: {
    // TODO: add real credentials for damenaccp. ASK MARCEL
    clientId: 'ADD IT',
    tenantId: 'ADD IT',
  },
  damenprod: {
    // TODO: add real credentials for damenprod. ASK MARCEL
    clientId: 'ADD IT',
    tenantId: 'ADD IT',
  },
};

const globalDomainMappings: SsoConnectionMap = {
  'tradecloud1local.onmicrosoft.com': 'tradecloud1local',
  'tradecloud1test.onmicrosoft.com': 'tradecloud1test',
  'tradecloud1accp.onmicrosoft.com': 'tradecloud1accp',
  'tradecloud1.onmicrosoft.com': 'tradecloud1prod',
};

const connectionsByEmail: { [email: string]: AzureConnection } = {
  'user@tradecloud1local.com': 'tradecloud1local',
  'user1@tradecloud1local.com': 'tradecloud1accp',
  'shubham.gupta@damen.com': 'damenaccp',
};

```



Here keys are the email domains and the values are the connection names. Make sure you have added clientId and tenantId for the connection name. **Connection names are just logical keys to make it easy to organize configurations**.

You can override the global domain configuration and have it specific to a user.  Add the key as the email address in the `connectionsByEmail` map and the value as the connection name which corresponds to the AD environment to which the user belongs.

## Microservices Configuration

Similar configuration needs to be added to the application.conf in **both** **authentication and user** microservices. Here is what the configuration looks like

```text
sso {
   domainMapping = [
     {
        domain = "tradecloud1.onmicrosoft.com"
        companyId =  "06893bba-e131-4268-87c9-7fae64e16ee9"
        tenantId =  "fc2e432f-1e78-4e28-ac62-33861e815454"
     },
     {
        domain = "damen.com"
        companyId =  "12680143-ccab-571b-bddd-ad353e3b30a7"
        tenantId =  "ADD IT"
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

