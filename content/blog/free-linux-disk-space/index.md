---
title: "Free Linux Disk Space"
excerpt: "No matter how big a hard drive your Linux machine has, it will be full at some point. How to find and fix the problem."
tags:
- df
- du
image_leader:
  src: "vitaly-otinov-BzuUDHCi_vo-unsplash.jpg"
  alt: "Clean up disk space in Linux. Dental floss really."
date: 2021-11-03T08:50:55+01:00
draft: false
---
{{< post/header >}}

    {{< post/title_and_excerpt >}}

    {{< post/meta >}}

{{< /post/header >}}

{{< post/image_leader caption="Photo by Vitaly Otinov on Unsplash" >}}

{{% post/content %}}

For a desktop having no more disk space is annoying. For a server having no more space usually means a reinstall. Not fun for anyone involved.

First, we need to find if there is a problem and where that problem is.

## The 'df' command, disk space usage

How bad is it? How full are your disks? Find out with the 'df' command.
The 'df' command is ancient. Its release was in 1971!

The command reports file system space usage and will display it in ordered columns. Think of a file system as a drive or a disk (it's not, but it's close enough).
Here are three invocations of 'df':

[![asciicast](https://asciinema.org/a/446614.svg)](https://asciinema.org/a/446614)

The first is just vanilla 'df'. It shows the file systems present on the system, and it has a column called 'Use%'. When that number creeps to 100%, you're in trouble. Pretty useful already.

But these large numbers make no sense. Perhaps in 1971, a kilobyte was a lot. Nowadays, terabyte disks are no exception. Adding the '-h' flag helps. It is short for '--human-readable', and it does precisely that. It's the second invocation and formats the kilobytes into units that make sense. This is the command you will use.

The third version is the one we use at Disk Notifier. The '--portability' flag ensures that 'df' works more predictably across systems and is ideal for scripting.

Now that we know how big the problem is, let's move on.

## The 'du' command, file space usage

Let's figure out where that disk space is going.

The 'du' command is just as old as 'df', hailing from the '70s. 'du' will display file space usage. Again ordered in columns.

[![asciicast](https://asciinema.org/a/ueRiHqSdju4XwgSiYa7G3WWoT.svg)](https://asciinema.org/a/ueRiHqSdju4XwgSiYa7G3WWoT)

Similar to 'df', it also has a plain version and a human-friendly version. The first version displays the amounts in kilobytes and the latter in human-readable units.

'du' is recursive and without arguments runs in the current directory. If you pass it a path, it will start from there.

It is tempting to write 'du -h /', getting results on all the directories in the system. However, doing so is a bad idea! It will be very slow and is likely to spam the standard out with tons of permission warnings.
Use the '-d' or '--max-depth' flag to stop the recursion at a certain level. Then inspect the results and drill down in a particular directory.

## A complete disk space investigation

Let's have a look at a real-world example:

[![asciicast](https://asciinema.org/a/Py0B0tzRkdEK27W3VjWC0uixm.svg)](https://asciinema.org/a/Py0B0tzRkdEK27W3VjWC0uixm)

The command I used was:

```shell
du --human-readable --max-depth 1 2> /dev/null | sort --human-numeric-sort
```

For clarity, I expanded all flags, but usually, I wouldn't. Running the command in my home directory revealed a directory called '.local', which seemed rather big. Eventually, I found out that my Steam games took up a large chunk of disk space. Together with the 'containers' directory, I use Docker quite a bit.

## Fancy rewrites

Rust is a popular up and coming language one of the advantages of the languages is that it is fast. Its speed inspired programmers to rewrite just about every command-line tool. 'du' is no exception, and ['dust'](https://github.com/bootandy/dust) is that rewrite. It is incredibly fast and ergonomic and my go-to when checking my disk space.

## Cleaning up

Once you have figured out where that disk space went, it is time to clean it up. So whip out 'rm' and say goodbye to your Steam games, log files or containers!

{{% /post/content %}}

{{< post/footer >}}
