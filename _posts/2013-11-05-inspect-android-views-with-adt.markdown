---
layout: post
status: publish
published: true
title: Inspect Android views with ADT
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 611
wordpress_url: http://thewebdev.de/?p=611
date: '2013-11-05 17:20:09 +0100'
date_gmt: '2013-11-05 16:20:09 +0100'
categories:
- Uncategorized
tags:
- android
- adt
- debugging
comments:
- id: 38488
  author: Dominik Liebler (@domnikl)
  author_email: domnikl@twitter.com
  author_url: http://twitter.com/domnikl/status/397764951298686976/
  date: '2013-11-05 17:38:49 +0100'
  date_gmt: '2013-11-05 16:38:49 +0100'
  content: ! 'new post: Inspect Android views with ADT - http://t.co/ILrRHl1Vzg'
---
<p>You ever wondered how this cool Android apps build their views, e.g. which components did they use, which properties they set? Or have you been stuck in debugging and the view won't just show up where you intended it to be?</p>
<p>Luckily, the Android Development Tools (ADT) have a function called 'Dump View Hierarchy' buried in the Devices View:</p>
<p><a href="http://thewebdev.de/wp-content/uploads/2013/11/dump_view_hierarchy.png"><img title="Dump View Hierarchy" alt="Dump View Hierarchy" src="http://thewebdev.de/wp-content/uploads/2013/11/dump_view_hierarchy.png" width="487" height="83" /></a></p>
<p>The cool thing is, you can not only inspect the views of the app you are developing, but of all views that are shown on your connected device or emulator.</p>
<p><a href="http://thewebdev.de/wp-content/uploads/2013/11/view_hierarchy.png"><img title="View Hierarchy" alt="View Hierarchy" src="http://thewebdev.de/wp-content/uploads/2013/11/view_hierarchy.png" width="488" height="344" /></a></p>
<p>This is just a simple example with the Google Mail app. Other apps are built with much more views and it's a great for learning how to build specific UI patterns with Android views.</p>
