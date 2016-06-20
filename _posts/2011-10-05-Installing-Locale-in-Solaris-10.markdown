---
layout: post
title: Installing Locale in Solaris 10
comments: true
---

Link: [Gopi Desaboyina Solaris Blogs](http://gdesaboyina.wordpress.com/2011/04/22/installing-locale-in-solaris-10/)


### Installing Japanese fonts/Locale in Solaris 10.
=======================================
1. Check what all locales you’ve installed using locale -a
2. localeadm -lt –> Check if you’ve Japanese there. If not you can directly install from DVD localeadm -a
3. localeadm -v -a ja -d /<DVD Mount Path/Solaris_10/Product>
4. localeadm -v -r ja –> This one removes the Japnese Packages ( Only Locale Related Packages).
5. set the LANG & LC_ALL variables then open gedit or appropriate program to check fonts.

### Check if your installation supports Japanese Region ?
=====================================================

### localeadm -lt
You do not appear to have created a fresh config file since you began using this application.
If you have a set of Solaris install images available to you, it is recommended that you do so before proceeding.

Do you wish to create a new config file? [y/n]: y

Please select the option that was used to install Solaris

1.  CD installation/net installed CD images
2.  DVD installation/net installed combined image

Please enter your choice:
^C
The following regions are supported by localeadm: <!-- more -->

—————–

Australasia (aua)
[ Australia, New Zealand ]

Central America (cam)
[ Costa Rica, Guatemala, Nicaragua, Panama, El Salvador ]

Central Europe (ceu)
[ Austria, Czech Republic, Germany, Hungary, Poland, Slovakia, Switzerland (German), Switzerland (French) ]

Eastern Europe (eeu)
[ Albania, Bosnia, Bulgaria, Estonia, Croatia, Kazakhstan, Lithuania, Latvia, Macedonia, Romania, Russia, Serbia, Slovenia, Turkey, Ukraine ]

Middle East (mea)
[ Saudi Arabia, Israel ]

Northern Africa (naf)
[ Egypt ]

North America (nam)
[ Canada (English), Canada (French), United States, Mexico ]

Northern Europe (neu)
[ Denmark, Finland, Iceland, Norway (Bokmal), Norway (Nyorsk),  Sweden ]

South America (sam)
[ Argentina, Bolivia, Brazil, Chile, Colombia, Ecuador, Paraguay, Peru, Uruguay, Venezuela ]

Southern Europe (seu)
[ Cyprus, Italy, Greece, Malta (English), Malta (Maltese), Portugal, Spain (Catalan), Spain (Spanish) ]

Western Europe (weu)
[France, Holland, Belgium (French), Belgium (Flemish), Ireland, England, Luxembourg (French), Luxembourg (German) ]

Japanese (ja)

Korean (korean)

Simplified Chinese (china)

Traditional Chinese (Hong Kong) (hongkong)

Traditional Chinese (taiwan)

Thai (th_th)

Hindi (hi_in)

Done.


### Checking
=======================
### locale
LANG=C
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_ALL=
### ls -ltr /var/adm/messages*
-rw-r–r–   1 root     root      350534 Feb 28 20:11 /var/adm/messages.2
-rw-r–r–   1 root     root      435091 Mar 28 23:05 /var/adm/messages.1
-rw-r–r–   1 root     root      124690 Apr 16 21:04 /var/adm/messages.0
-rw-r–r–   1 root     root       59680 Apr 22 02:59 /var/adm/messages

### export LANG=ja
### export LC_ALL=ja
### locale
LANG=ja
LC_CTYPE="ja"
LC_NUMERIC="ja"
LC_TIME="ja"
LC_COLLATE="ja"
LC_MONETARY="ja"
LC_MESSAGES="ja"
LC_ALL=ja

### ls -ltr /var/adm/messages*
-rw-r–r–   1 root     root      350534  2?????? 28??????  20:11 /var/adm/messages.2
-rw-r–r–   1 root     root      435091  3?????? 28??????  23:05 /var/adm/messages.1
-rw-r–r–   1 root     root      124690  4?????? 16??????  21:04 /var/adm/messages.0
-rw-r–r–   1 root     root       59680  4?????? 22??????  02:59 /var/adm/messages
