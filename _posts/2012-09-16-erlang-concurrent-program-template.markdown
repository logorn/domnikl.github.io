---
layout: post
status: publish
published: true
title: Erlang Concurrent Program Template
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 490
wordpress_url: http://thewebdev.de/?p=490
date: '2012-09-16 07:36:11 +0200'
date_gmt: '2012-09-16 06:36:11 +0200'
categories:
- Uncategorized
tags:
- github
- erlang
- gist
- concurrent
comments:
- id: 9325
  author: exterm
  author_email: me@alienemperor.de
  author_url: ''
  date: '2013-04-03 09:33:07 +0200'
  date_gmt: '2013-04-03 08:33:07 +0200'
  content: Why not use a gen_server behavior instead?
- id: 9326
  author: Dominik Liebler
  author_email: liebler.dominik@googlemail.com
  author_url: ''
  date: '2013-04-03 09:48:00 +0200'
  date_gmt: '2013-04-03 08:48:00 +0200'
  content: I didn't know about behaviors when I wrote this. Now I would definitely
    use a gen_server behavior here.
---
<p>To start development on a new Erlang module that supports concurrent processing, I wrote myself a template, that is mostly inspired by the template from Joe Armstrong and his book <a title="Programming Erlang - Software for a Concurrent World" href="http://pragprog.com/book/jaerlang/programming-erlang" target="_blank">Programming Erlang - Software for a Concurrent World</a>.</p>
<p><code>[gist]https://gist.github.com/3727470[/gist]</code></p>
<p>I developed the template from the book a bit further and used <em>MFA</em> (Module, Function, Argument List) in the <em>spawn</em> call to enable dynamic code upgrades.</p>
<p>In the top you can see, that all functions will be exported (that means, callable from other modules or the shell). This is only for debugging purposes.</p>
<p>As a default, the loop will just print out, what has been received from the client process.</p>
