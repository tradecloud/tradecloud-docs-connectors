---
description: >-
  This page describes the configurations needed on AD side to allow users to
  login using Azure AD
---

# Azure AD Connector - AD Configuration

The Azure AD Connector provides Single Sign On access for your users on Tradecloud.

Only the users you allow \(using an AD conditional access policy\) are synced to Tradecloud.

A new Active Directory user is automatically created in your Tradecloud company.

{% hint style="info" %}
The Azure AD Connector is an add-on. Contact sales@tradecloud1.com for info.
{% endhint %}

## Configure Azure AD for authentication

To allow users to log in using a Azure AD account, you must register Tradecloud as an application in the Microsoft Azure portal

To register your app with Azure AD, see Microsoft's [Quickstart: Register an application with the Microsoft identity platform](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app).

During registration, configure the following settings:

| Option | Setting |
| :--- | :--- |
| Supported account types | To allow users from external organizations \(like other Azure AD directories\) choose the appropriate multitenant option. Multitenant options include the following: Accounts in any organizational directory \(Any Azure AD directory - Multitenant\). |
| Redirect URI | Enter your callback URL:  [https://portal.tradecloud1.com/msal-callback/login](https://portal.tradecloud1.com/msal-callback/login) |

During this process, Microsoft generates an Application \(client\) ID; you can find this on the app's Overview screen. Take note of this value.

### Add permissions

Tradecloud needs OpenID delegated `email`and `profile` permissions to be able to create a Tradecloud identity and user. The email, given name and family name will be added to the id token, which Tradecloud uses to create a identity and user. Tradecloud will NOT call the Graph API.

To add permissions, see Microsoft's [Quickstart: Configure a client application to access web APIs - Add permissions to access web APIs](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-configure-app-access-web-apis#add-permissions-to-access-web-apis).

You will need to configur OpenID permissions for the **Microsoft Graph API**.

While setting up your permissions, configure the following settings:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Permission Section</th>
      <th style="text-align:left"><b>Permission</b>
      </th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Delegated permissions</td>
      <td style="text-align:left">
        <p>email</p>
        <p>profile</p>
      </td>
      <td style="text-align:left">
        <p>View users&apos; email address</p>
        <p>View users&apos; basic profile</p>
      </td>
    </tr>
  </tbody>
</table>

### Send credentials to Tradecloud

Send client id and tenant id to Tradecloud so that one of the engineers can configure SSO for you.

![](../.gitbook/assets/image%20%282%29.png)

