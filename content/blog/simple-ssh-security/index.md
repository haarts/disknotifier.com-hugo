---
title: "Simple SSH Security"
excerpt: "Within a couple of minutes you can improve your SSH security significantly. Here's how."
tags:
- SSH
- Security
image_leader:
  src: "adi-goldstein-EUsVwEOsblE-unsplash.jpg"
  alt: "Proper SSH security is not hard"
date: 2021-10-21T12:03:01+02:00
draft: false
publishdate: 2021-10-29
---

{{< post/header >}}

    {{< post/title_and_excerpt >}}

    {{< post/meta >}}

{{< /post/header >}}

{{< post/image_leader caption="Photo by Adi Goldstein on Unsplash" >}}

{{% post/content %}}

SSH has been around for some time now. But when you install SSH on your favourite OS, it comes with a bunch of defaults enabled which aren't great. It's easy today to make SSH just a little bit more secure.

### Passwordless login

The first and easiest change you can make to your SSH install is to disable password logins. Make sure you can log in to your server with some keys before going ahead!

Now lets make an edit to the `/etc/ssh/sshd_config` file. Search for the `KbdInteractiveAuthentication` line and change the value to `no`. In a lot of guides, you will see this key named `ChallengeResponseAuthentication`. This name is a deprecated alias. What this will do is disable keyboard-interactive authentication. I think we can all agree that the new name covers the meaning much better.
Next, find the key `PasswordAuthentication`. Again, the default value is `yes`, but we'll be setting it to `no`.

The above changes to your SSH daemon disable password authentication. Don't forget to restart the daemon with something like `systemctl reload sshd.service`.

Using keys is safer because it is much harder to lose a key than a password. In addition, a key has a lot more entropy. So with this change, you are already ahead of the pack! Good job.

### Remove weak prime numbers

The following change is removing insecure moduli. I think 'insecure' is too strong of a word to use since these moduli are not shown to be insecure, but the expectation is that they will soon. The client and the server use these moduli to negotiate a secure key. In theory, by removing smaller moduli, it could be that the client and server can not come to an agreement, and a secure connection can not be established. 
Here's a bunch of magic you need to execute:

{{< highlight shell >}}
awk '$5 >= 3071' /etc/ssh/moduli > /etc/ssh/moduli.safe
mv /etc/ssh/moduli.safe /etc/ssh/moduli
{{< /highlight >}}

So what is happening here? The `mv` command is easy. The first command looks for lines in `/etc/ssh/moduli`, which on the fifth line have a value bigger than 3071 and writes those in the `moduli.safe` file.

### Allow strong cyphers only

In a similar vein, we are going to allow only the super-secure cyphers. 
Create a new file `/etc/ssh/sshd_config.d/ssh_hardening.conf`. Add the following to the file:

{{< highlight shell >}}
KexAlgorithms curve25519-sha256,curve25519-sha256@libssh.org,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group-exchange-sha256
Ciphers chacha20-poly1305@openssh.com,aes256-gcm@openssh.com,aes128-gcm@openssh.com,aes256-ctr,aes192-ctr,aes128-ctr
MACs hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,umac-128-etm@openssh.com
HostKeyAlgorithms ssh-ed25519,ssh-ed25519-cert-v01@openssh.com,sk-ssh-ed25519@openssh.com,sk-ssh-ed25519-cert-v01@openssh.com,rsa-sha2-256,rsa-sha2-512,rsa-sha2-256-cert-v01@openssh.com,rsa-sha2-512-cert-v01@openssh.com
{{< /highlight >}}

That's a mouthful. This effectively restricts SSH to use only MAC's, cyphers, and key exchange algorithms, which people way more intelligent than I deem secure.

Note that you need to load this file in your `sshd_config` file. That isn't always standard, so better to check. The file should have a line like `Include /etc/ssh/sshd_config.d/*.conf`. If it doesn't, add it!

### Credits

Obviously, I didn't come up with all these changes. The credit goes to the authors of SSH Audit and various other sources out there. Do visit their site, as they have a neat scanner to determine if your SSH daemon is up to snuff!

### Bonus
Often you will read people recommend that you change the port SSH is listening on. Of course, this doesn't make it more secure. But what it does do is that these annoying scanners stop filling up your logs. 

### More bonus
Disallowing root login is also frequently recommended. I believe this has limited merit in our current landscape since 95% of the time, the user you log in with has sudo privileges. Then it adds no extra security. But you should really judge this for your own situation.

Don't forget to reload that secure beast of an SSH daemon after these changes!

{{% /post/content %}}

{{< post/footer >}}
