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
| Redirect URI | Enter your callback URL:  [https://portal.tradecloud1.com/auth0-callback](https://portal.tradecloud1.com/auth0-callback) |

During this process, Microsoft generates an Application \(client\) ID for the application; you can find this on the app's Overview screen. Make note of this value.

### Create a client secret

To create a client secret, see Microsoft's [Quickstart: Configure a client application to access web APIs - Add Credentials to your web application](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-configure-app-access-web-apis#add-credentials-to-your-web-application).

Once generated, **make note of this value**.

If you configure an expiring secret, make sure to **record the expiration date**; you will need to renew the key before that day to avoid a service interruption. We recommend you choose "never expires"

### Add permissions

To add permissions, see Microsoft's [Quickstart: Configure a client application to access web APIs - Add permissions to access web APIs](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-configure-app-access-web-apis#add-permissions-to-access-web-apis).

You will need to configure permissions for the **Microsoft Graph API**.

While setting up your permissions, configure the following settings:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Permission Section</th>
      <th style="text-align:left"><b>Permission/Field</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Delegated permissions</td>
      <td style="text-align:left">
        <p>Users &gt; User.Read</p>
        <p>Directory &gt; Directory.Read.All</p>
        <p>Directory &gt; Directory.AccessAsUser.All</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Application permissions</td>
      <td style="text-align:left">Directory &gt; Directory.Read.All</td>
    </tr>
  </tbody>
</table>

### Send credentials to Tradecloud

Send client id and client secret using a secure email or a secure link to Tradecloud so that one of the engineers can configure SSO for you.

