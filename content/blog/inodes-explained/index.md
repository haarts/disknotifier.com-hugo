---
title: "inodex explained"
excerpt: "inodes are simple datastructures that keep track of disk content"
tags:
- file-storage
date: Fri Feb 17 16:39:28 CET 2023
publishdate: 2023-02-17
image_leader:
  src: david-pisnoy-NpMWgJ1_Ohk-unsplash.jpg
  alt: "Thousands of nodes manage the contents on your disk"
draft: false
---

{{< post/header >}}

    {{< post/title_and_excerpt >}}

    {{< post/meta >}}

{{< /post/header >}}

{{< post/image_leader caption="Photo by David Pisnoy on Unsplash" >}}

{{% post/content %}}

## inodes store metadata

Linux inodes are data structures that are used to store information about files and directories on a Linux file system. An inode is a fixed-size data structure that contains information about a file or directory, such as its size, permissions, and the location of its data on the disk.

## one file, one inode

Each file and directory on a Linux file system has its own inode, which is identified by a unique inode number. The inode number is used to access the inode, which contains all the information about the file or directory. Inodes do not contain the actual data of the file or directory, but they do contain pointers to the data blocks on the disk where the data is stored.

## amount of inodes are static

Inodes are created when a file or directory is created, and they are deleted when the file or directory is deleted. The number of inodes on a file system is set when the file system is created, and it cannot be changed later. This means that it is important to choose the appropriate number of inodes for a file system based on the expected number of files and directories that will be created on the file system. This is why ut pays to keep an eye on the inodes! You can have disk space remaining but simply ran out of inodes. This happens when writing many tiny files.

## inode content

The information stored in an inode includes the following:

- File type: Inodes store the type of file, such as a regular file, a directory, a symbolic link, or a special file such as a device node or a socket.
- File permissions: Inodes store the permissions for the file, such as the owner and group of the file, and the read, write, and execute permissions for the file.
- File timestamps: Inodes store the timestamps for the file, such as the time when the file was last accessed, modified, or changed.
- File size: Inodes store the size of the file in bytes.
- Pointers to data blocks: Inodes store pointers to the data blocks on the disk where the data of the file is stored.

Inodes are important for the efficient operation of a Linux file system. They allow the file system to quickly locate and access files and directories, and they enable the file system to keep track of the location and status of all files and directories on the system. Inodes are also used to implement many important features of Linux file systems, such as hard and symbolic links, file permissions, and access control lists.

{{% /post/content %}}

{{< post/footer >}}
