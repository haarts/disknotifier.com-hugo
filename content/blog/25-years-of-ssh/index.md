---
title: "25 Years of SSH"
excerpt: "SSH is a pivotal technology. Not only for us but for the internet at large."
tags:
- SSH
- History
image_leader:
  src: "maria-vojtovicova-SPvJPDXEmqA-unsplash.jpg"
  alt: "Finland, land of the Linux Gods"
date: 2021-10-19T20:39:45+02:00
draft: true
---

{{< post/header >}}

    {{< post/title_and_excerpt >}}

    {{< post/meta >}}

{{< /post/header >}}

{{< post/image_leader caption="Photo by Maria Vojtovicova on Unsplash" >}}

{{% post/content %}}

Last year the SSH protocol turned 25 years old. When I read that, I was surprised. A tool that is so ubiquitous nowadays did not exist a mere 25 years ago.

### An attack started it all

The unique aspect of SSH is that it allows secure communications over an insecure network.  Before 1995 that was of lesser concern. The tool of choice back then was `telnet`— something I sporadically use if I want to see the wire protocol of a particular service like Redis.
Other alternatives were `rsh` and `rlogin`, both part of the Berkeley r-commands suite, hailing from the early 1980s.

SSH was born when its inventor, Tatu Ylönen, then a Helsinki University of Technology student, noticed a password sniffer on the university network (these [Fin's](https://en.wikipedia.org/wiki/Linus_Torvalds) undoubtedly impacted computing!). To combat the attacker, he wrote the first version of 'secure shell'.

### Security for all

It is safe to say that the advent of the Internet made encryption necessary. Since SSH has been made into a protocol with mister Ylönen as the primary contributor, he's still active in the field [today](https://ylonen.org/) and a board member of ssh.com, a company selling products around SSH. The command-line tool you and I are using daily implements this protocol, and almost always, that implementation is OpenSSH.

### Version 2

The protocol evolved, and in 2006 version 2 of the SSH protocol was released. Sometimes you see this reflected on your systems when the documentation refers to the `authorized_keys2` (note the '2'!) file. That was to differentiate between version 1 of the file and version 2. Since OpenSSH version 7.6, released in 2017, all references to the old 1.x version of the protocol are removed, and the `authorized_keys` file dropped the '2' suffix.

### Future

The future of SSH is undoubtedly bright. However, there's much work to be done with the quickly evolving encryption landscape. Quantum hard encryption is one of the fields Tatu is actively working on.

I also think that the explosion of IoT will bring challenges to SSH. For example, I use SSH to deploy software to a handful of servers. What happens if I need to deploy to thousands securely? Yet another direction I think is interesting is the lack of stable connections. [Mosh](https://mosh.org/) is an excellent example of how flaky connections can be handled. 

{{% /post/content %}}

{{< post/footer >}}
