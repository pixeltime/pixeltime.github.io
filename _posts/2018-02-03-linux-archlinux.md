---
title: archLinx
date: 2018-02-03
categories:
 - archLinux安装
tags: 
- Linux
---
archLinux 

<!-- more -->
当初看着官方的说明，和各种博客和贴吧，真的都有点放弃了。还好后面硬是杠上了。

准备：win32Diskxxx，archLinux 镜像。。。

话说BIOS的UEFI要注意一下，（`后面有好大的坑`）


希望能看到。。。
<pre>
<code class="lang-Bash">
	root@archiso~#
</code>
</pre>

联网。。。一般笔记本都自带网卡的吧、xk wifi-menu 就行了

好,同步一下时间吧
<pre>
<code class="lang-Bash">
	root@archiso~# timedatectl set-ntp true
</code>
</pre>

分区 cfdisk(MBR)/cgdisk(UEFI) ，MS-DOS。。。???、xk

mkfs.格式化分区，mkswap 用于swap分区

挂载分区

<pre>
<code class="lang-Bash">
	root@archiso~# mount /dev/sdax /mnt
</code>
</pre>

交换分区用swapon /dev/sdax
其他分区记得先mkdir!

修改仓库: /etc/pacman.d/mirrorlist

`pacman -Syy` 更新源

安装基本系统

<pre>
<code class="lang-Bash">
	root@archiso~# pacstrap /mnt base base-devel iw dialog wpa_supplicant wpa_actiond
</code>
</pre>

生成fstab:`genfstab -U /mnt >> /mnt/etc/fstab`

进入正常的终端:`arch-chroot /mnt /bin/bash`

设置时区:`ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime`

设置UTC时区:`hwclock --systohc --utc`

环境:`vi /etc/locale.gen `，after then   `locale-gen` then `echo LANG=en_US.UTF-8 > /etc/locale.conf`

hostname `echo hostname > /etc/hostname`

password......

grub 挺重要的....

`pacman -S grub os-prober`

`grub-install --target=i386-pc /dev/sda --recheck` (有时候可能要 -f)MBR这么做,UEFI就是其他的了

`grub-mkconfig -o /boot/grub/grub.cfg` (生成grub引导信息)

`pacman -S xorg` 基本的桌面

`pacman -S deepin deepin-extra lightdm` deepin桌面(还需要配置一下)

`pacman -S networkmanager` 

`google fonts `,`adobe fonts`

`useradd -m -s /bin/bash user` (add user)

`systemctl enable lightdm` 

差不多了(`换mac`) 太折腾了

![image01]({{ site.url }}/my_pics/2018/minecrafts.jpg)







