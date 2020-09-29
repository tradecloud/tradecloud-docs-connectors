---
description: >-
  This page describes the configurations needed on Auth0 side to allow users to
  login using Azure AD
---

# Azure Active Directory Connector - Auth0 Side

The detailed setup process is described at this link [https://auth0.com/docs/connections/enterprise/azure-active-directory/v2\#create-an-enterprise-connection-in-auth0](https://auth0.com/docs/connections/enterprise/azure-active-directory/v2#create-an-enterprise-connection-in-auth0). We will not duplicate all the information as it can become obsolete. We have however captured the summary below just so that every time we don't need to read the full Auth0 documentation

## Configuration Summary

* Navigate to the [Connections &gt; Enterprise](https://manage.auth0.com/#/connections/enterprise) page in the [Auth0 Dashboard](https://manage.auth0.com/#/), and click the `+` next to **Microsoft Azure AD**
* Enter general information for your connection.
* Enter Client ID and Client Secret which we get after adding a new application in Azure AD
* Click **Create**.
* To use your new Azure AD enterprise connection, you must first [enable the connection](https://auth0.com/docs/dashboard/guides/connections/enable-connections-enterprise) for both portal and api application.
* Now you're ready to [test your connection](https://auth0.com/docs/dashboard/guides/connections/test-connections-enterprise). 

