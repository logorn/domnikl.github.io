---
layout: post
status: publish
published: true
title: type-safe collections in PHP
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 306
wordpress_url: http://thewebdev.de/?p=306
date: '2012-02-03 19:11:30 +0100'
date_gmt: '2012-02-03 18:11:30 +0100'
categories:
- Uncategorized
tags:
- php
- collections
- gist
comments: []
---
<p>Yes, you've read the headline correctly, although PHP is a weakly-typed language, sometimes you just need to make sure, that an argument to a method is of a certain type. As of PHP 5.3 you can use type-hinting to ensure this situation.</p>
<p>Image you were implementing a simple blog system. Every post can have a collection of comments associated to it and you don't want to have trackbacks in this collection. And the list of comments should be distinct. You don't want that spam comment over and over again in this list.</p>
<p>PHP already provides a type for this task in the SPL: SplObjectStorage is the best way to storage a list of unique objects that can be iterated over and provides array-like access. Here's a basic example:</p>
<p><script src="https://gist.github.com/1731448.js?file=spl_object_storage.php"></script></p>
