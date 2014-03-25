---
layout: post
status: publish
published: true
title: learning some Erlang
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 160
wordpress_url: http://thewebdev.de/?p=160
date: '2011-10-06 18:59:19 +0200'
date_gmt: '2011-10-06 17:59:19 +0200'
categories:
- Uncategorized
tags:
- erlang
- functional programming
- learning
- couchdb
comments:
- id: 180
  author: Funky
  author_email: ice15422@aol.com
  author_url: ''
  date: '2011-10-22 20:27:57 +0200'
  date_gmt: '2011-10-22 19:27:57 +0200'
  content: I always appreciate a great article or piece of writing. Thanks for the
    contribution.
- id: 462
  author: Jeffrey Smith
  author_email: jeffreysmith1985@live.com
  author_url: ''
  date: '2012-02-16 00:06:15 +0100'
  date_gmt: '2012-02-15 23:06:15 +0100'
  content: Thx for the advice, and your web page definitely looks good. Just what
    wp design are you employing?
---
<p>You now might think: <em>What the hell is Erlang? </em>And a few months back I didn't even knew what exactly it was. I only knew it is a programming language, and that somehow Ericsson was involved in developing it.</p>
<p><img class="alignright" title="Erlang Logo" src="http://upload.wikimedia.org/wikipedia/commons/4/42/Erlang_logo.png" alt="" width="340" height="289" /></p>
<p>For me it really started when I learned to use CouchDB, I am doing a talk about it in November/December in my company Mayflower GmbH (you are all invited, it's free and there's pizza and beer!). I think CouchDB has a nicely designed REST interface and it's simple to use yet very powerful. As always with such interresting projects, I wanted to take a look at the source code (hey it's open source and you can learn a lot of such projects by just downloading the source and read a little code, I strongly recommend this to every developer out there!).</p>
<p>So I read a bit of the source code of Couch and it's written mainly in <a href="http://www.erlang.org/" target="_blank">Erlang</a>. The syntax seemed a bit strange, but for me that's not a reason to leave this and look for fun somewhere else. Instead <a href="http://pragprog.com/book/jaerlang/programming-erlang" target="_blank">I bought me a ebook for my Kindle</a> (it's from one of the inventors of Erlang, <a href="http://en.wikipedia.org/w/index.php?title=Joe_Armstrong_(programming)&amp;redirect=no" target="_blank">Joe Armstrong</a>).</p>
<p>I already knew Erlang has a sometimes very strange syntax, but I found out that in Erlang, you don't have to write much code to do something. Erlang programs are said to be up to 70% smaller than for instance C programs (or PHP, Perl, Java or whatever else).</p>
<p>Erlang is a functional programming language, that means: no objects, classes and everything else you might know from other languages you already know. In functional programming, everything is a function, there is no mutable state as in most other languages (and that makes concurrency a lot easier). You might know Lamdas and Closures and they are mostly inspired from the functional world.</p>
<p>I think it's worth to learn such a language, it will give you a different view on how to solve common programming tasks. After years of programming in object-oriented languages it will give you some fresh ideas :)</p>
<p>I will post more articles about Erlang in the next time, so stay tuned. If you are interested in what I have learned so far, watch my <a href="https://github.com/domnikl/learning_erlang">repository on github</a>.</p>
