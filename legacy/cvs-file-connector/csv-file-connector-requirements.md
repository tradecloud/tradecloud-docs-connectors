---
description: >-
  Technical requirements for the .NET connector installed at the customer
  premises
---

# CSV File Connector Requirements

## Buyer account number (supplier only)

If you are a supplier, Tradecloud needs to know the **account number of your customer.**

**Please send the account number to support@tradecloud.nl** and we will configure it in Tradecloud.

Your integration and Tradecloud will use the _orderBuyerCode_ to route to the correct buyer.

## Environments

There is an acceptance **test** environment and a **live** environment.

These environments are isolated by **two separate installed connectors** with **each a CSV root**.

## Windows Server

The .NET connector needs a **(shared) Windows Server** where it will be installed as a **Windows Service**.

* Processor: **X64** architecture, it will use max. 10% of 1 processor core
* Memory: max. 100 MB
* Disk: max. 200 MB

### .NET framework

The Windows Server should have the .**NET framework 4.5** or higher run time installed.

### Firewall

The Windows Server should have **outgoing internet access** on **TCP / IP port 5670**.

## Program Files

The .NET connector will be installed by default in:

* C:\Program Files\TradeCloud Connector **Test**
* C:\Program Files\TradeCloud Connector **Live**

It is possible to select another folder during setup.

## CSV root

Each .NET connector needs a **root folder** or **network share**.

* the connector will create **sub folders** in the root folder automatically
* there are two **archive** folders for incoming and outgoing files, which are not cleaned automatically
* a CSV file has approx. size 4 KB per order and 1 KB per order response.

## Windows Account

The .NET connector needs a **Windows user account**

* with **read and write rights** on each **own installation folder** and sub folders
* with **read and write rights** on the **CVS root folder** or share and its sub folders
