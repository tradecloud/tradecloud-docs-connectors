---
description: >-
  .NET connector using Exact Globe Entity Services and SQL at customer premises
  (buyer side only)
---

# Exact Globe Connector

{% hint style="warning" %}
Deprecated connecter on the Tradecloud legacy platform (tradecloud.nl)

Use the A B Software Exact Globe Connector on the Tradecloud1 platform (tradecloud1.com)
{% endhint %}

## Functional requirements

For the purchase order module "orderprestatiedatums" should be enabled.

## Technical requirements

Exact Globe Next **409** or higher

### Windows Server

a (shared) **Windows Server** on which the Connector will be installed as a Windows Service

a **Windows account** which is also a **Exact Globe account** under which the Connector Windows Service will be running

* with read and write access to the Exact Globe database
* with access to the Exact Globe Entity Services

**.NET Framework 4.5 installed **- this will be detected by the Connector Installer - a .NET installer will be launched which will download and install .NET 4.5

### SQL Server

access to the **Exact Globe SQL Serve**r

* sql server security should be set to _SQL Server and Windows Authentication mode_
* sql server user _Baco_ with password _JustDoIt!_ should exist (installed by Exact Entity Services)

### Entity Services

access to the **Exact Globe Entity Services** on TCP/IP port **8010**

* should be installed and running
* with access to Exact Globe Database (the Windows Server mac address should be added to table BacoAccessServers)
* WARNING : there are issues with BacoAccessServers when Exact Synergy (standard, not enterprise) is used.

### Internet

**access to the internet** (from inside to the outside) on TCP/IP port **5670** (the ZeroMQ protocol is used)
