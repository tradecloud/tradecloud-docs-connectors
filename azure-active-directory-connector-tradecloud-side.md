# Azure Active Directory Connector - Tradecloud Side

## Frontend Configuration

Get the name of the enterprise connection added in step [https://auth0.com/docs/connections/enterprise/azure-active-directory/v2\#create-an-enterprise-connection-in-auth0](https://auth0.com/docs/connections/enterprise/azure-active-directory/v2#create-an-enterprise-connection-in-auth0) and then add its mapping in file `src/app/auth/routes/login/state/sso.connections.ts` .

Currently, src/app/auth/routes/login/state/sso.connections.ts has the following mappings

```text
const ssoMap: SsoConnectionMap = {
  'tradecloud2.onmicrosoft.com': 'tradecloud2-local',
  'tradecloud1test.onmicrosoft.com': 'tradecloud1test',
  'tradecloud1accp.onmicrosoft.com': 'tradecloud-accp',
  'tradecloud1.onmicrosoft.com': 'tradecloud1prod',
};
```

Here keys are the email domains and the values are the enterprise connections

## Microservices Configuration

Similar configuration needs to be added to the application.conf in **both** **authentication and user** microservices. Here is what the configuration looks like

```text
sso {
   domainMapping {
     tradecloud2.onmicrosoft.com = "06893bba-e131-4268-87c9-7fae64e16ee9"
     tradecloud1test.onmicrosoft.com = "06893bba-e131-4268-87c9-7fae64e16ee9"
     tradecloud1accp.onmicrosoft.com = "06893bba-e131-4268-87c9-7fae64e16ee9"
     tradecloud1.onmicrosoft.com = "06893bba-e131-4268-87c9-7fae64e16ee9"
   }
}
```

Here keys are the email domains and the values are the company ids

path of application.conf in authentication microservice - authentication/src/main/resources/application.conf 

path of application.conf in user microservice - user/src/main/resources/application.conf

