---
layout: post
title:  "Optimize your Azure Alerts using Logic Apps"
date:   2018-06-25 00:00:00
categories: azure
---

Azure Monitor is a powerful tool to monitor all the aspects of you Azure application.
However keeping track of when, where and why can be a challenge when your Azure environment(s) grows in size and complexity.
This post will show you some neat tricks thats possible by combining Alerts with Logic Apps.


## Alerts in Azure Monitor
Alerts can be configured in many different views. The main entrypoint is probably supposed to be through __Azure Monitor__ which I find useful for the overview and most use cases. When configuring the classic metric alerts though, I prefer to navigate to the resource in question and add an alert from there.

![Screenshot of Azure Alerts]({{ site.url }}/assets/azure-alerts/alerts.png)

Azure Monitor currently have two types of alerts, the __Alerts (classic)__, divided into _Activity Log_ and _Metric Alerts_, and the newer __Alerts__ which enables support for multiple alert criterieas, severity levels and advanced action groups. The new alert system is much more advanced and definitely a better choice. There are however still some scenarios where the classic alerts are useful. I've found that guest level performance monitoring of virtual machines (for instance alerts related to free Disk Space) is one of them.

For more information please see the [official documentation on Alerts](https://docs.microsoft.com/en-us/azure/monitoring-and-diagnostics/monitoring-overview-unified-alerts) in Azure Monitor.


## Logic Apps
Logic Apps is one of Microsoft Azure's _serverless_ products and helps you build automatic processes and workflows.
I personally like the Logic Apps for it's simplicity and visual design tools and love to experiment with it's vast amount external integrations.
These integrations makes it possible to create a triggered workflow to suit your needs, in a matter of minutes.

The [Logic Apps Documentation](https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-overview) gives an overview of the key concepts of Logic Apps and have some pretty thorough tutorials created by Microsoft employee Esther Fan.


## Creating cool alerts using Logic Apps
When configuring the alerts Action Group it is possible to specify a Logic App as _Action Type_. There is a requirement that the Logic App already exists AND that the Logic App is configured with a HTTP trigger _When a HTTP request is received_.