---
layout: post
status: publish
published: true
title: ! 'TextMate: syntax highlighting for Erlang'
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 161
wordpress_url: http://thewebdev.de/?p=161
date: '2011-10-06 13:01:16 +0200'
date_gmt: '2011-10-06 12:01:16 +0200'
categories:
- Uncategorized
tags:
- erlang
- textmate
- syntax highlighting
comments:
- id: 7433
  author: Silvano
  author_email: silvanojr@gmail.com
  author_url: ''
  date: '2013-03-25 17:04:20 +0100'
  date_gmt: '2013-03-25 16:04:20 +0100'
  content: Thank you Sir! :)
---
<p>I've been learning a little Erlang in the last few weeks and sometimes I use my Macbook to write some small functions, libs and so on. But it seems that TextMate hasn't build-in support for Erlang, so all my pretty code was just black :-(</p>
<p>But that isn't that big a problem: I found a <a href="https://github.com/textmate/erlang.tmbundle">bundle for Erlang on github</a> (man I love this site, makes finding those nice pieces of code even simpler) and added it. So you just have to do:</p>
<p>[code lang="bash"]</p>
<p>mkdir -p /Library/Application Support/TextMate/Bundles</p>
<p>[/code]</p>
<p>then cd to this directory and clone the repo in there:</p>
<p>[code lang="bash"]</p>
<p>git clone https://github.com/textmate/erlang.tmbundle.git</p>
<p>[/code]</p>
<p>Now when you restart TextMate and open a .erl file everything will be fine :)</p>
