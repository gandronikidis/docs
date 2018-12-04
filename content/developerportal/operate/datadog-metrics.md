---
title: "Datadog for v4 Mendix Cloud"
parent: "metrics"
menu_order: 50
description: "How to configure Mendix Cloud v4 to enable monitoring and analysis with Datadog."
tags: ["Datadog", "Mendix Cloud", "v4", "monitoring", "analysis"]
---

## 1 Introduction

**Datadog** is a monitoring and analysis tool for cloud applications, providing monitoring of servers, databases, tools, and services, through a SaaS-based data analytics platform. You can link your Mendix Cloud v4 apps to Datadog to provide additional monitoring.

This document explains how to configure your Mendix Cloud v4 app to send data to Datadog.

## 2 Datadog API Key

### 2.1 New Datadog User

If you are new to Datadog, you will need to get an account first.

1. Go to the Datadog site ([https://www.datadoghq.com/](https://www.datadghq.com/)) and choose **GET STARTED FREE**.

2. Enter your Datadog account details.

    Once you have entered your details you cannot continue until you have set up your agent.

3. Choose the option **From Source**.

    ![The From Source option on the Agent setup screen](attachments/datadog-metrics/from-source.png)

4. Copy the value of *DD_API_KEY* key shown on the install script.

    ![Source install script shows DD_API_KEY=your API key](attachments/datadog-metrics/dd-api-key.png)

5. You now need to use this API key with your app: see section 3 [Connect Node to Datadog](#connect-node).

### 2.2 Existing Datadog User

To make use of Datadog you will need a Datadog API key. If you do not already have a Datadog API key, you can obtain one here:



## 3 [Connect Node to Datadog]{#connect-node}

To send your runtime information to Datadog, you need to provide the Datadog API key to your environment.

1. Go to the **Environments** page of your app in the *Developer Portal*.

2. Click **Details** to select the environment you wish to monitor with Datadog. 

3. Open the **Runtime** tab.

4. Add a **Custom Environment Variable**.

5. Select **DD_API_KEY** from the *Name* dropdown.

    ![Dropdown containing custom environment variable names](attachments/datadog-metrics/environment-variable-dd-api-key.png)

6. Enter the Datadog **API key** obtained in section 2 as the *Value* of the Environment Variable.

7. Add a second **Custom Environment Variable**:

    * **Name**: *DD_LOG_LEVEL*
    * **Value**: *INFO*

        This will ensure that messages are sent to Datadog. You can change the log level later once you have confirmed that Datadog is receiving them.

7. Return to the **Environments** page for your app and *Deploy* or *Transport* your app into the selected environment.

    {{% alert type="warning" %}}Your app must be **redeployed** as additional dependencies need to be included.<br/><br/>Restarting the app is not sufficient to start sending data to Datadog.{{% /alert %}}

8. **Restart** the application.

## 4 Additional Information

### 4.1 Log Levels

The valid values for **DD_LOG_LEVEL** are:

* CRITICAL
* ERROR
* WARNING
* INFO
* DEBUG

## 4 Related Content

* [Metrics](metrics)