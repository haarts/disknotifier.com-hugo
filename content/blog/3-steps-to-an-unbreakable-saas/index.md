---
title: "3 Steps to an Unbreakable Saas"
excerpt: "Nothing gives more stress than production software failing. So how do you build a SaaS which never goes down?"
tags:
- monitoring
- saas
image_leader:
  src: "alexey-turenkov-MIq7jmfHwj0-unsplash.jpg"
  alt: "Disk space alerts are a good place to start"
date: 2021-12-14T20:41:56+01:00
draft: false
---

{{< post/header >}}

    {{< post/title_and_excerpt >}}

    {{< post/meta >}}

{{< /post/header >}}

{{< post/image_leader caption="Photo by Alexey Turenkov on Unsplash" >}}

{{% post/content %}}

Software breaks all the time. A bug brings the database to its knees, or a viral social media post crashes your frontend. If you care about your weekend, you can do a few things to bring peace of mind.

## Build fault-tolerant software

It is tempting to bang out those features and go full steam ahead. Some programming languages make you fly over that happy path. Javascript is an excellent example of this. Got a user input that you need as a number? No problem. Some `parseInt` and be done with it. The risk is evident, of course. What if the user doesn't enter an actual int? A double, perhaps? Or not a number at all. What do you do about that leading whitespace?
Rust takes the opposite approach. You need to handle every edge case. How many bytes does your int take? Signed or unsigned? You'd better not make any assumptions about the input.

It pays to stop and think about how your software can fail. Then, what will you do when it fails? For example, at Disk Notifier, we have multiple backend workers. All of them can fail. When they die, we restart them automatically (with SystemD) and forward the error to [HoneyBadger](https://honeybadger.io). Half of the time, some user input had an unexpected value, or some network was temporarily down.
It is hard to grasp SystemD at first. But after the first Unit file, the others are quick to write.

## Build redundant systems (or don't run on your software)

The first things that come to mind are 'hot failover' and 'read replicas'. Stuff you read about on engineering blogs and hear about at that conference. While incredibly interesting from an engineering perspective, only a fraction of the software developers or devops should have to deal with that. These are Big Tech problems. A myriad of companies can host your Postgres database. There are incredible options to host your static pages. These options include upgrades and security patches, and you no longer need to think about CDNs.

At Disk Notifier we use:
- [Render.com](https://render.com) for our Postgres database
- [Netlify](https://netlify.com) for our sales website/blog

Focus, instead, on your 'secret sauce'. What makes your product unique? At Disk Notifier that is not our snazzy sales website or our incredible Postgres database. It's our backend services that log in to your server, check disk space and send alerts (you could argue that the last one is not our core business either!). Setting up that system from scratch takes half an hour. That, too, is redundancy. 

I'm leaving out Kubernetes. I don't think any company under the size of a hundred engineers should have to deal with that. Keep It Simple, Stupid.
 
## Install monitoring software

Knowing what is up is half the battle. But it needs to be relevant and actionable. Having reams of graphs doesn't help you. So start with the basics and work your way up from there. Our backend is unlikely to run CPU cycles, so I'd rather not be bothered with that statistic. The nerd in me adores [Netdata](https://github.com/netdata/netdata), but how does it help me? Unless monitoring comes with alerting, it is worse than useless. At best, a distraction at the start of the day. Start simple and build it up.

## What about testing?

Sound engineering includes (unit/integration) testing. But that is useful at a different stage. Testing is a great way to communicate intend about your code and gives you the confidence to add features or refactor code. An unbreakable SaaS refers to things going sides ways when enjoying your weekend. 

{{% /post/content %}}

{{< post/footer >}}
