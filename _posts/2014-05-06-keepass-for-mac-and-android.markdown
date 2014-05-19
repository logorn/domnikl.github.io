---
layout: post
status: publish
published: true
title: Syncing Keepass Databases between Mac, Chrome and Android
author: Dominik Liebler
date: '2014-05-06 20:20:53 +0100'
---

With the recent background of the [Heartbleed](en.wikipedia.org/wiki/Heartbleed) bug in mind and everything around it, there's a good chance you already changed all your passwords (if not, do so NOW!). I did and I also wanted a secure way to store the passwords and to also have them available on my Android phone if I need them.

At first, I downloaded [KyPass Companion](https://itunes.apple.com/de/app/kypass-companion/id555293879?mt=12), which is a Mac port of the Keepass tool and works really well. Important for the integration into Browsers is the KeepassHttp server. It is run on localhost and provides an interface to store and retrieve passwords from the database.

Here comes the browser into play: [ChromeIPass](https://chrome.google.com/webstore/detail/chromeipass/ompiailgknfdndiefoaoiligalphfdae) will connect to the KeepassHttp interface and use it to store new passwords, change them accordingly or fill in the fields automatically for you if you need it.

The last part in the chain is the question of how do I sync the database between my Mac and my Android phone? The solution is rather simple: [ownCloud](http://owncloud.org). I run it on a server using nginx and PHP FPM and it runs really well (I also sync documents, pictures, music, calendars, contacts and so on). 

On my phone I use [Keepass2Android](https://play.google.com/store/apps/details?id=keepass2android.keepass2android&hl=de), which will provide everything I need: copying user names and passwords from it, a quick unlock mechanism and syncing over Webdav from/to ownCloud.

