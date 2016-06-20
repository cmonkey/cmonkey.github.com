---
layout: post
title: Solaris Disk 安装
date: Monday, December 19, 2011 12:51:16 PM CST
comments: true
---

先在oracle下载dvd包
在windows的fat32下建立solaris 文件夹
解压缩solaris dvd，将boot 文件夹中的multiboot,x86.miniroot 文件copy到solaris文件夹。
最后得到的文件夹可能是这样:
F:/solaris
   sol-10-u10-ga2-x86-dvd.iso
   multiboot
   x86.miniroot

现在reboot系统；进入grub，按c进入grub command。

    find /solaris/multiboot

得到输出可能是这样 (hd0,1)

    root (hd0,1)
    kernel /solaris/multiboot kernel/unxi -B install_media=dsk
    module /solaris/miniroot
    boot
<!-- more -->
进入solaris安装环境
进入选择界面
1为默认,是UFS系统。
3或者4是ZFS系统。
选择3
然后得到找不到系统文件
进入shell
输入如下命令:
    mount -F pcfs /dev/dsk/c1d0p0:1 /mnt

c1d0p0:1 是系统的FAT32 那一块硬盘，具体在不同机器上各不一样

    lofiadm -a /mnt/solaris/sol-10-u10-ga2-x86-dvd.iso
    mount -F hsfs /dev/lofi/1 /cdrom
    exit

现在可能需要重新选择一次，安装什么样的系统。
选择3，进入安装根系统是ZFS的安装界面。
ZFS可以提供全新安装或者升级安装。


今天看到各类媒体都在报道朝鲜的金正日在前两天，
也就是2011-12-7的时候在火车上挂了。个人唯一的感受就是朝鲜的改革开放是否在明年如他们自己所说的那样如期到来。
社会都在不停的进步，生活的这片土地，还有那么多悲惨的事情，但自己似乎无能为力，
乌坎，很多地方都在上演悲剧。
