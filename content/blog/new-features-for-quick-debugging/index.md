---
title: "New Features for Quick Debugging"
excerpt: "There are few things more frustrating than waiting. Now you don't have to."
tags:
- features
image_leader:
  src: "jezael-melgoza-2FiXtdnVhjQ-unsplash.jpg"
  alt: "Whether it is a Debian, AlmaLinux or Ubuntu disk. Monitoring them is now easier."
date: 2021-12-14T21:03:53+01:00
draft: false
publishdate: 2022-01-08
---

{{< post/header >}}

    {{< post/title_and_excerpt >}}

    {{< post/meta >}}

{{< /post/header >}}

{{< post/image_leader caption="Photo by Jezael Melgoza on Unsplash" >}}

{{% post/content %}}

We're really happy to have finalized two new features which make monitoring these Linux disk of yours a bit easier.

## Check now

Instant feedback is vital in any process. Be it while writing software or doing a new business. When Disk Notifier launched, it was fully functional. You add a server, and after a while, our backend would pick it up and schedule an inspection. Assuming you had copied our snippet correctly, it would work just swimmingly. However, it would be *great* to immediately find out if you copied the snippet you copied works!

![check available disk space quickly](check-now-feature.png)

Now you can. A new button 'check now' on the server details page will allow you to immediately schedule a check of your system. With the other new feature, you have what you need to debug those connection issues quickly!

## Error reporting

It's all great and awesome when you can instruct us to check the connection to our service immediately. But that doesn't help you when all you see is 'connection_error'. So that's why we now propagate the specific SSH error to you. You can read this error message in the notification telling you the connection failed. 

![display SSH connection errors](show-error-feature.png)

Enjoy these features! There's more to come. We're in it for the long haul.

{{% /post/content %}}

{{< post/footer >}}
