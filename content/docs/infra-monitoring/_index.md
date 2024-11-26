---
title: Tutorial to resolve app outage with host data
description: Learn how to identify failing apps using infrastructure data.
---

Your infrastructure requires regular inspection and maintenance. Like a city planner designing a new road or bridge, decisions about what your system needs should come from careful observation about existing limitations. For a tech stack, this looks like a series of resource decisions that affect the performance of your APIs, services, and apps.

With our agent, you can collect metrics and event data to help you make resource decisions about your system infrastructure. This doc synthesizes a platform journey for troubleshooting app failure with host data.

## Objectives 

You will learn to: 

* Scope your data to help you find root cause
* Make data-driven resource decisions using your host data

The tutorial assumes you've [already created your first alert](). 

## Make a resource decision about an outage

{{% steps %}}

###  Start with your alerts

When you're first building out your maintenace workflows, we recommend starting with **Summary page overview** until you find a  better starting point for your unique use case. To start out, we're going to head on over to **PLATFORMWEBSITE > TILE NAME HERE > ANOTHER THING TO SELECT > Infrastructure** to view the summary page. This page shows you a _lot_ of aggregated data about your system, but we can break this down into something more manageable. 

![stildata](/image/stildata.png)

We've divided your summary page into three sections:

* A row of four widgets that identify the particulars of your system, like the number of apps serviced by your hosts and how many alerts are notifying you about incidents in your system. 
* A middle section with time series graphs showing you a high level overview of your CPU, memory, and disk resources.
* A summary table that breaks down these metrics by individual hosts.

You might be familiar with our filter bar anchored to the top of all our capability pages. You can use this filter bar to scope the summary page to data about alerting entities. We've added this query to the filter bar: `alertSeverity = 'CRITICAL'`

### Find the failing app

Notice how this query scoped the entire page from hundreds of hosts to three. 

![stildata](/image/stildata.png)

The **CPU (%)** time series indicates that:

* `apache-svr01` spiked from 15% CPU usage to just over 60%
* `proxy-west-2` mimicked the behavior
* `host-tower-chicago` flatlined

This isn't enough information to declare our root cause, but it does limit the range of possibilities for our incident. There are any number of reasons for high CPU, but it's likely the issue has something to do with either:

* The app is running a redundant process that's causing CPU to spike, so the app-owning team needs to optimize some code.
* More end users are accessing a certain component and adding stress to our system, so we need to provision more resources to meet that load.

If we click the applications widget, our summary page opens a relationship modal that shows different apps serviced by various hosts. Note how the `Orders team` service is both alerting a critical incident and has a rrelationship to `apache-svr01` (but not the other two). 

![stildata](/image/stildata.png)

We can exit the modal and return to the summary page so we can explore the overview page for `apache-svr-01`.

### Determine root cause

Since we've identified our fussy app, we can start testing our hypotheses from earlier. At this stage, the goal is to identify any patterns that help us answer the question: is app failure related to inefficient code or stress on the system?

The host overview page shows familiar widgets like CPU, memory, and disk usage, but also includes data about network, processes, load, and storage. To the right of the page is a sidebar that shows information about latest events limited to 30 minutes ago, any other related entities, and open issues your team's created. This isn't helpful to us right now, but we suspect you'll encounter situations in the future where it can definitely help you. 

![stildata](/image/stildata.png)

Since we're disambiguating whether root cause is about app code or resources, we'll take a quick glance at our **Network** and **Processes** widgets. We can see that:

* Our load average time series shows regular intervals for the last hour, but nothing that parallels our CPU % pattern.
* Network traffic shows regular interviews, but no parallels either.
* Our running processes show about a dozen different kinds of processes, but there's a `ruby` process using 77.34% of your CPU. 

 If load stress affected our CPU %, we'd expect to see a steep spike at the same time our CPU spiked, then a potential flatline when the app failed in the network and load graphs. Since we definitely don't see that, we have pretty high confidence that the critical incident has to do with some kind of app process, not a resource one. 
 
 Since we don't need to provision any resources to our host, we can notify the app-owning team that some Ruby process is disrupting their `Orders team` service.

{{< callout type="info" >}}
  It's best practice to check your **Latest events** sidebar to ensure someone hasn't made direct changes to the machine. Look for any change in the machine's config file or whether someone has entered the machine to make changes directly. 
{{< /callout >}}

{{% /steps %}}

## What's next?

So far we've covered how to use infrastructure data to troubleshoot a resource-related incident. We've covered how to scope down from thousands of hosts to a set of hosts, then correlated data to make a decision. The next doc shows you how to create custom dashboards using infrastructure metrics.