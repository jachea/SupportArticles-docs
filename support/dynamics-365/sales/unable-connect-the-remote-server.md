---
title: Unable to connect to the remote server
description: Provides a solution to errors that occur when a custom plugin is deployed in a Microsoft Dynamics CRM environment that executes a SOAP action to connect to an external address or service.
ms.reviewer: 
ms.topic: troubleshooting
ms.date: 
---
# Unable to connect to the remote server error generated by a custom plugin in Microsoft Dynamics CRM

This article provides a solution to errors that occur when a custom plugin is deployed in a Microsoft Dynamics CRM environment that executes a SOAP action to connect to an external address or service.

_Applies to:_ &nbsp; Microsoft Dynamics CRM 2011, Dynamics CRM 2013, Microsoft Dynamics CRM 2013 Service Pack 1, Dynamics CRM 2015  
_Original KB number:_ &nbsp; 3080697

## Symptoms

Consider the following scenario: A custom plugin is deployed in a Microsoft Dynamics CRM environment that executes a SOAP action to connect to an external address or service. The plugin may receive one of the following error messages if a network proxy is required for external communication:

> Unable to connect to the remote server

> Error: There was no endpoint listening at *\<Custom Service Address>* that could not accept the message. This is often caused by an incorrect address or SOAP action. See InnerException, if present, for more details.

## Cause

The Microsoft Dynamics CRM application server is sitting behind a network proxy and the plugin is configured to run in Isolation Mode (Sandbox). In this scenario, the service account running the Microsoft Dynamics CRM Sandbox Service didn't have access through the network proxy.

## Resolution

Use the following steps to configure the Microsoft Dynamics CRM Sandbox Service Account to use the network proxy:

1. Sign in to the Microsoft Dynamics CRM Application Server using the Microsoft Dynamics CRM Sandbox Service Account.
2. Open Internet Explorer.
3. Navigate to **Tools** > **Internet Options** > **Connections** > **LAN Settings**.
4. Update either the **Use Automatic Configuration Script** or **Proxy Server** sections per the local environment configuration.

## More information

As the plugin executes in Isolation Mode, the call to external address or service is made by the Microsoft Dynamics CRM Sandbox Service account. This account can access the external service from the Microsoft Dynamics CRM server that hosts the Microsoft Dynamics CRM Sandbox Service.
