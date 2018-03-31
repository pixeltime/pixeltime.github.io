---
title: fdisk
description: fdisk
date: 2018-03-31
categories:
 - fdisk
tags:
 - Linux
---

> fdisk command ,记得最开始只会用cfdisk...


<!-- more -->

## 很简单但实用的命令,可以查看磁盘信息.(当然也可以使用`lsblk /dev/yourdisk`)

```sh
root@slackware:/# fdisk -l
```

它会检测出你的所有磁盘
 eg:
 
```sh
root@slackware:/# fdisk -l

Disk /dev/sda: 1 GB, 1024 bytes

...

```

## 帮助

使用`fdisk /dev/sda` 之后,将会输出一堆的提示信息.

```sh
The number of cylinders for this disk is set to 8841.
There is nothin wron with that but this is larer than 10
...

```

在此之后

```sh
Command (m for help): m
Command action
	a  toggle a bootable flag
	b  edit bsd disklabel
	c  toggle the dos compatibility flag
	d  delete a partition
	l  list known partition types
	m  print this menu
	n  add a new partition
	o  create a new empty DOS partition table
	p  print the partition table
	q  quit without saving changes
	s  create a new empty Sun disklabel
	t  change a partition’s system id
	u  change display/entry units
	v  verify the partition table
	w  write table to disk and exit
	x  extra functionality (experts only)

```

就是fdisk的命令了

```sh
Command: (m for help): n
Command action
	e extended
	p primary partition (1-4)
P
Partition number (1-4):1
First cylinder (1-8841, default 1): 1
Last cylinder or +size or +sizeM or +sizeK (1-8841, default 8841): +4G
```
`n` 表示创建一个分区
`e`与`p` 表示扩展分区和主分区,(主分区一般都是4个一下...)
`1`与`+4G`表示柱面开始是1,结束是4096....

如果分一个swap分区,则要改变`system id`(如果使用`cfdisk`,可以明显的查看,83Linux,84则是Linux swap)

`t`命令进入修改

```sh
Command (m for help): t
Partition number (1-4): 1
Hex code (type L to list codes): 82
```

最好保存就用`w`,如果不放心,可以使用`p`查看一下...

## mount 挂载分区

mkfs.extx 格式化分区

`mount /dev/sdayourdisknum /mnt` 挂载`/`分区(其他分区也一样)
`mkdir /mnt/home`,`mount /dev/sdayourdisknum /mnt/home` 挂载`/home` 分区

`mkswap /dev/sdayourdisknum` 交换分区使用
`swapon /dev/sdayourdisknum` 激活交换分区


## 结束

好了可以痛痛快快的去玩其他Linux发行版了...
