---
title: "Surprising results from a Reddit question."
excerpt: "'What do you use to manage your home server?' was the question posted on Reddit. Turns out SSH reigns supreme."
date: 2021-10-14T22:03:07+02:00
tags:
- SSH
- Insight
draft: false
image_leader:
  src: "lorenzo-herrera-p0j-mE6mGo4-unsplash.jpg"
  alt: "SSH home server management"
---

{{< post/header >}}

    {{< post/title_and_excerpt >}}

    {{< post/meta >}}

{{< /post/header >}}

{{< post/image_leader caption="Photo by Lorenzo Herrera on Unsplash" >}}

{{% post/content %}}

The other week I posted a question on [r/selfhosted](https://www.reddit.com/r/selfhosted/comments/q1wobo/how_many_of_you_use_ssh_to_manage_your_server/). The question was simple:

> How many of you use SSH to manage your server?

To be entirely frank I expected a good number of people to answer positively. But I wasn't expecting such an overwhelming majority to use SSH!

The post gathered over 500 comments and I thought it'd be insightful to summarize what the community is using here.

### Clear winner

Reddit is kind enough to expose an API, and after twiddling around for half an hour, I could download the entire thread as a JSON document. Then, together with [jq](https://stedolan.github.io/jq/), I did some rudimentary analysis. Out of the 186 top-level comments, 154 said they use SSH to access their home server. That's more than 82%!

It is essential to say that SSH is exclusively used to manage Linux home servers. Windows machines are all managed with [RDP](https://docs.microsoft.com/en-us/troubleshoot/windows-server/remote/understanding-remote-desktop-protocol). But only a  fraction of the r/selfhosted community members are using Windows machines, just under 5%.

#### Alternatives

What I expected to people using more were things like the Linux equivalent of a remote desktop. A solution based on [VNC](https://www.raspberrypi.com/documentation/computers/remote-access.html#vnc), for example. However, there are RDP solutions for Linux as well.

Another option I thought would be popular would be webUIs to administer a server, like [Plesk](https://www.plesk.com/). But I've read all 500+ comments, and none of them mentions anything like that. So it seems I was just dead wrong there.

#### VPNs

Notable is the number of people protecting their home server access with a variety of tunnels and VPNs. Out of the 186 top-level comments, 60 use some VPN. That's a little over a third. OpenVPN seems a dying breed, but Wireguard is popular. Some people mention bastions and jump hosts, but they seem to be in the minority. A significant portion of people chooses not to access their home server from the internet at all. Instead, they prefer to do administrative tasks on their server from the comfort of their local network.

#### SSH Security

When it comes to SSH, almost everybody follows these security practices:

- they disable root login
- they disable password login and use key-based authentication only
- run the SSH daemon on a different port than 22

The last point is under [some debate](https://security.stackexchange.com/questions/32308/should-i-change-the-default-ssh-port-on-linux-servers) if it yields a security benefit, but it indeed prevents your logs from being filled up with nonsense!

A good number of people (almost 8%) also report using [fail2ban](https://mosh.org/) to secure their network further. I have the experience that fail2ban is indeed easy to set up, getting that extra bit of security with little overhead.

Securing SSH is not an easy task, and it will be the subject of a future post. But I like the advice given in this [blog post](https://stribika.github.io/2015/01/04/secure-secure-shell.html). For a quick scan of how your SSH looks like to the outside world, try [ssh-audit.com](https://www.ssh-audit.com/). That website is using on the open-source [ssh-audit](https://github.com/jtesta/ssh-audit) software.

I had fun reading all the comments and learned a good deal. Thanks!

{{% /post/content %}}

{{< post/footer >}}
