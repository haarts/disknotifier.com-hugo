---
title: "Monitoring as a Service"
excerpt: "Everybody agrees you should monitor your servers. But how can you in a cost effective way?"
tags:
- monitoring
image_leader:
  src: "alexander-popov-GmLfS_S43gA-unsplash.jpg"
  alt: "Monitoring isn't great on it's own. It's great together with alerts."
date: 2021-11-18T08:50:55+01:00
draft: false
publishdate: 2021-11-18
---
{{< post/header >}}

    {{< post/title_and_excerpt >}}

    {{< post/meta >}}

{{< /post/header >}}

{{< post/image_leader caption="Photo by Alexander Popov on Unsplash" >}}

{{% post/content %}}

Everybody operating servers must monitor them. However, it is an industry secret that this is not always the case. Especially with the fleeting nature of servers nowadays, it is easy to lose track. 
Setting up monitoring and alerting should cost as little time and money as possible. With Monitoring as a Service, this is possible.

Monitoring as a Service is a shortcut to simple and effective monitoring and alerting.

## Always up to date

With a SaaS solution, you are always up to date. When you subscribe, the provider takes care of updating the software. Thus ensuring you are always running the latest and greatest. 

## Half the work

With monitoring as a service, the story is a bit more nuanced. It's not like you create a user account, and you are off to the races. Instead, you need to install a so-called 'agent' on each machine you want monitoring.
This agent needs to be updated periodically, and when the service pulls data (like Prometheus), you need to open a firewall port. 
All unless, of course, you are using Disk Notifier. There is no agent to be installed, and no new ports need to be open! [Read](http://disknotifier.com/blog/dead-simple-disk-monitoring/) how this works.

## Predictable costs

The cost of monitoring solutions is opaque. The devops team is continuously spending time and therefore money in installing and maintaining the monitoring software. With a SaaS solution, at least half it the costs is clear upfront. And since the SaaS company has a vested interest in making installing their agent as simple as possible, it is often easy to do so. Simple software installs and upgrades reduce risk and costs.

## Live faster

Since there's only half the work to be done and the remaining work is made as easy as possible, the time to go live is short. Because you can go live fast, there is less time for things to go wrong, reducing operational risk.

## Downsides to Monitoring as a Service

It isn't all great of course. The major downside of SaaS monitoring is that your data is exported from your organization. That might or might not be a problem depending on the data and your situation.

Another consideration is that you now have a new piece of software running on your network. Proper agent software is open source and therefore could be inspected. But how many people do so? When it is a binary, who's to say if what you have running is built from the source you are inspecting? It would be best if you built it yourself. But that negates some of the benefits.

## Alerting as a Service

As an engineer, something is fascinating about graphs. But how much value do these fancy scribbles give you? Unless you are a data scientist, no one should look at charts. 
When running a business, you want to know when things go off the rails. When everything is running smoothly, a monitoring service should be conservative with your time.
Alerting builds on monitoring but is only alerting that is ultimately relevant.

## Options

What are the options when looking for a Monitoring as a Service? Quite a few!
- Disk Notifier: This tops the list for obvious reasons.
- Nagios X: Open source with commercial support.
- Datadog: The web 2.0 monitoring vendor.
- Splunk: They shook up the industry a decade ago.
- Zabbix: A veteran in the industry.
- Paessler PRTG: An even older veteran.

In a series of other post we will have a closer look at each of these solutions.

{{% /post/content %}}

{{< post/footer >}}
