---
layout: post
status: publish
published: true
title: The Erlang stack
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 529
wordpress_url: http://thewebdev.de/?p=529
date: '2012-10-01 17:28:17 +0200'
date_gmt: '2012-10-01 16:28:17 +0200'
categories:
- Uncategorized
tags:
- erlang
- stack
- basho
- unittesting
- otp
comments:
- id: 2238
  author: Huseyin Yilmaz
  author_email: yilmazhuseyin@gmail.com
  author_url: http://www.yilmazhuseyin.com
  date: '2012-10-01 19:52:42 +0200'
  date_gmt: '2012-10-01 18:52:42 +0200'
  content: ! "Great article. Thanks.\r\nYou might want to add some debugging tools
    too (like appmon, pman or debugger)."
- id: 2242
  author: Ian Calvert
  author_email: ianjcalvert@gmail.com
  author_url: ''
  date: '2012-10-02 09:20:02 +0200'
  date_gmt: '2012-10-02 08:20:02 +0200'
  content: ! "I've found the following to be extremely useful:\r\n\r\nCowboy : Fast,
    easy to use webserver (https://github.com/extend/cowboy)\r\n\r\nSinan : Similar
    to rebar, but I found rebar somewhat difficult to get running every time I started
    a project. Lots of things to be moved and changed. I use sinan to package all
    the stuff I do these days. (https://github.com/erlware/sinan)\r\n\r\nEvent Tracer
    : One of the most incredible tools I've found in erlang. Live sequence diagrams
    of your running application, with variable detail levels. This is built in and
    pretty easy to use: \r\nhttp://www.erlang.org/documentation/doc-5.7.4/lib/et-1.3.3/doc/html/et_examples.html\r\n
    http://souja.net/2009/04/making-sense-of-erlangs-event-tracer \r\nhttp://jlouisramblings.blogspot.co.uk/2011/10/using-event-tracer-tool-set-in-erlang.html"
- id: 2376
  author: Robert Virding
  author_email: rvirding@gmail.com
  author_url: ''
  date: '2012-10-14 21:08:30 +0200'
  date_gmt: '2012-10-14 20:08:30 +0200'
  content: ! "I prefer common test to eunit as it is much better for testing whole
    systems. And I would stress the ability to build fault-tolerant systems which
    was one of our primary goals with Erlang.\r\n\r\nOtherwise I like it."
- id: 2919
  author: Yurii Rashkovskii
  author_email: yrashk@gmail.com
  author_url: http://rashkovskii.com/
  date: '2012-11-22 02:42:02 +0100'
  date_gmt: '2012-11-22 01:42:02 +0100'
  content: ! 'JFYI, agner has been superseded by EXPM: http://rashkovskii.com/2012/10/01/expm-or-meet-agner-2/'
- id: 2926
  author: The Erlang stack (useful links to learn Erlang) | My Daily Feeds
  author_email: ''
  author_url: http://mydailyfeeds.x10.mx/2012/11/22/the-erlang-stack-useful-links-to-learn-erlang/
  date: '2012-11-22 11:51:31 +0100'
  date_gmt: '2012-11-22 10:51:31 +0100'
  content: ! '[...] Hacker News http://thewebdev.de/the-erlang-stack/       This entry
    was posted in Uncategorized by admin. Bookmark the [...]'
- id: 2928
  author: Anthony Eden
  author_email: anthonyeden@gmail.com
  author_url: ''
  date: '2012-11-22 16:13:24 +0100'
  date_gmt: '2012-11-22 15:13:24 +0100'
  content: ! 'I highly recommend Learn Yourself Some Erlang for Great Good: http://learnyousomeerlang.com/
    - it is an excellent way to get comfortable with Erlang, how it works and how
    it is intended to be used.'
- id: 2930
  author: Culley Smith
  author_email: culley.smith@gmail.com
  author_url: ''
  date: '2012-11-22 16:59:15 +0100'
  date_gmt: '2012-11-22 15:59:15 +0100'
  content: ! "http://learnyousomeerlang.com/\r\n\r\nBeen following this and it's a
    good (and fun) way to learn Erlang."
- id: 2945
  author: Thomas Järvstrand
  author_email: tjarvstrand@gmail.com
  author_url: ''
  date: '2012-11-23 11:08:59 +0100'
  date_gmt: '2012-11-23 10:08:59 +0100'
  content: ! "I'll take this opportunity to make a shameless plug for my Erlang Development
    Tool Suite (EDTS). It's a really nice package that makes your Erlang life a lot
    easier if you're using Emacs (of course you are!).\r\n\r\nhttps://github.com/tjarvstrand/edts"
- id: 2947
  author: Freddy
  author_email: freddy@freddiesfavoritewebsite.co.uk
  author_url: ''
  date: '2012-11-23 13:50:29 +0100'
  date_gmt: '2012-11-23 12:50:29 +0100'
  content: When I tried to use Erlang for web development I had to stop because its
    support for string handling was so horrible. Is there a good library that will
    let me work with UTF-8 strings?
- id: 4161
  author: Peter Bruinsma
  author_email: peter@23min.com
  author_url: ''
  date: '2013-01-15 21:39:32 +0100'
  date_gmt: '2013-01-15 20:39:32 +0100'
  content: ! "I see the folks at 99s used <a href=\"https://github.com/dluna/chaos_monkey\"
    rel=\"nofollow\">https://github.com/dluna/chaos_monkey</a> for stability testing
    of Ranch. Interesting project!\r\n\r\n\"The purpose of The Chaos Monkey is to
    find out if your system is\r\nstable or not.  What will your system do when things
    start to go wrong\r\nand your processes die randomly?  The Chaos Monkey will show
    you.\r\nWith a stick.\""
- id: 9098
  author: ! '@domnikl'
  author_email: domnikl@twitter.com
  author_url: http://twitter.com/domnikl/status/319044457603411969/
  date: '2013-04-02 12:11:40 +0200'
  date_gmt: '2013-04-02 11:11:40 +0200'
  content: ! 'the #erlang stack - http://t.co/IKzGvXVNZM'
- id: 10052
  author: ! '@SeanTAllen'
  author_email: SeanTAllen@twitter.com
  author_url: http://twitter.com/SeanTAllen/status/320507582651437056/
  date: '2013-04-06 13:05:37 +0200'
  date_gmt: '2013-04-06 12:05:37 +0200'
  content: ! '"The #Erlang stack" =&gt; http://t.co/Q7ZkoLsiC2 &lt;= a handy list
    of stuff to get you going with erlang'
- id: 42467
  author: ! '@pyotrgalois'
  author_email: pyotrgalois@twitter.com
  author_url: http://twitter.com/pyotrgalois/status/403362999001296896/
  date: '2013-11-21 04:23:27 +0100'
  date_gmt: '2013-11-21 03:23:27 +0100'
  content: The Erlang stack | the web dev http://t.co/kUoWVQjg0Z
- id: 42468
  author: ! '@martuvetter'
  author_email: martuvetter@twitter.com
  author_url: http://twitter.com/martuvetter/status/403362668842475522/
  date: '2013-11-21 04:22:09 +0100'
  date_gmt: '2013-11-21 03:22:09 +0100'
  content: The Erlang stack | the web dev http://t.co/mrLNwGNNsx
- id: 52777
  author: ! 'Erlang: Links, News And Resources (5) | Angel "Java" Lopez on Blog'
  author_email: ''
  author_url: http://ajlopez.wordpress.com/2014/01/10/erlang-links-news-and-resources-5/
  date: '2014-01-10 15:28:33 +0100'
  date_gmt: '2014-01-10 14:28:33 +0100'
  content: ! '[&#8230;] The Erlang stack | the web dev http://thewebdev.de/the-erlang-stack/
    [&#8230;]'
---
<p>I am learning Erlang for a little to a year now, not constantly but every now and then and a little more in the last 2-3 months. As I dug deeper and deeper in the language I started looking for the typical stack for Erlang programs. That means tools to develop and run a Erlang/OTP application and here is a (not yet complete) list of what I have found.</p>
<p>Erlang is a language that has been and is used for <a href="http://programmers.stackexchange.com/questions/112417/real-world-applications-of-erlang" target="_blank">various types of applications</a>. Unfortunately many developers don't feel comfortable with the functional programming paradigm that Erlang is built upon. To help you get started on your way as a to-be Erlang developer here are some tools that may help you:</p>
<ul>
<li><strong><a href="http://veldstra.org/whyerlang/" target="_blank">why erlang?</a></strong> reasons to use the language and runtime environment for your projects</li>
<li><strong><a href="http://learnyousomeerlang.com/">Learn you some Erlang (for Gread Good)</a></strong>: a very good (and fun) way to learn Erlang</li>
<li><strong><a href="http://www.tryerlang.org/" target="_blank">try-erlang</a></strong>: an in-browser interactive tutorial to Erlang</li>
<li><strong><a href="http://www.erlang.org/doc/apps/edoc/index.html" target="_blank">edoc</a></strong>: generates HTML documentation from .erl source files, comes with standard distribution</li>
<li><a href="http://www.erlang.org/doc/apps/eunit/chapter.html" target="_blank"><strong>eunit</strong></a>: unit testing framework, comes with the standard installation of Erlang</li>
<li><strong><a href="http://www.erlang.org/doc/apps/common_test/index.html" target="_blank">common test</a></strong>: also ships with standard installation</li>
<li><a href="https://github.com/basho/rebar" target="_blank"><strong>rebar</strong></a>: a popular build tool for erlang programs developed by Basho</li>
<li><a href="https://github.com/erlware/sinan" target="_blank"><strong>sinan</strong></a>: an alternative to rebar with a stronger focus on OTP</li>
<li><a href="https://github.com/spawngrid/kerl" target="_blank"><strong>kerl</strong></a>: manages installations of Erlang/OTP, like RVM does for Ruby</li>
<li><strong><a href="http://rashkovskii.com/2012/10/01/expm-or-meet-agner-2/">EXPM</a></strong>: a package index and manager for Erlang (supersedes <a href="http://erlagner.org" target="_blank">agner</a>)</li>
<li><a href="http://www.erlang.org/doc/man/dialyzer.html" target="_blank"><strong>dialyzer</strong></a>: a static code analysis tool (<a href="http://www.erlang.org/doc/man/dialyzer.html" target="_blank">standard dist</a>)</li>
<li><a href="https://github.com/eproxus/meck" target="_blank"><strong>meck</strong></a>: a mock library for Erlang, works perfectly with eunit</li>
<li><a href="http://basho.com/blog/technical/2011/07/20/Introducing-Lager-A-New-Logging-Framework-for-ErlangOTP/" target="_blank"><strong>lager</strong></a>: a logging framework developed @ Basho, <a href="http://theschemeway.blogspot.de/2012/10/lager-is-cool.html" target="_blank">Lager is cool!</a></li>
<li><a href="http://erldocs.com" target="_blank"><strong>erldocs</strong></a>: a nicer manual than the original docs, you can find it on <a href="http://erldocs.com" target="_blank">erldocs.com</a></li>
<li><a href="http://www.erlang.org/doc/apps/debugger/debugger_chapter.html" target="_blank"><strong>debugger</strong></a>: <a href="http://www.erlang.org/doc/apps/debugger/debugger_chapter.html" target="_blank">built-in</a> graphical debugging tool, just start it with <em>debugger:start/0</em></li>
<li><strong><a href="http://www.erlang.org/doc/man/observer.html" target="_blank">observer</a></strong>: a graphical node and application process tree viewer, also <a href="http://www.erlang.org/doc/man/appmon.html" target="_blank">built-in</a>, start it with observer<em>:start/0 (supersedes <a href="http://www.erlang.org/doc/man/appmon.html" target="_blank"><strong>appmon</strong></a>)</em></li>
<li><a href="http://www.erlang.org/doc/man/pman.html" target="_blank"><strong>pmon</strong></a>: a <a href="http://www.erlang.org/doc/man/pman.html" target="_blank">built-in</a> graphical process manager, run it with <em>pmon:start/0</em></li>
<li><strong><a href="https://github.com/extend/cowboy" target="_blank">cowboy</a></strong>: a fast and easy to use web server</li>
<li><a href="http://www.erlang.org/documentation/doc-5.7.4/lib/et-1.3.3/doc/html/et_intro.html" target="_blank"><strong>et</strong></a>: built-in and easy to use event tracer for Erlang: <a href="http://jlouisramblings.blogspot.com/2011/10/using-event-tracer-tool-set-in-erlang.html" rel="bookmark">Using the Event Tracer tool set in Erlang</a>, <a href="http://souja.net/2009/04/making-sense-of-erlangs-event-tracer" target="_blank">Making Sense of Erlang's Event Tracer</a></li>
<li><strong><a href="http://yaws.hyber.org/" target="_blank">yaws</a></strong>: a high-performance web server primarily suited for dynamic content</li>
<li><a href="https://github.com/ferd/erlang-history" target="_blank"><strong>erlang-history</strong></a>: adds history to the erlang shell</li>
<li><strong><a href="https://github.com/ferd/vmstats">vmstats</a>: </strong>monitor Erlang VMs via<strong> <a href="https://github.com/lpgauth/statsderl">statsderl</a></strong></li>
<li><strong><a href="http://elixir-lang.org/" target="_blank">Elixir</a></strong>: a functional and meta-programming aware language that runs on the Erlang VM</li>
<li><strong><a href="http://lenary.co.uk/erlang/2011/08/erlang-web-libraries/" target="_blank">Web frameworks</a></strong>: a list of web frameworks for Erlang</li>
<li><strong><a href="https://github.com/flashingpumpkin/spooky" target="_blank">Spooky</a></strong>: a RESTful request handler for Erlang</li>
<li><a href="http://www.erlang.se/doc/programming_rules.shtml" target="_blank">Erlang Programming Rules</a></li>
</ul>
<p>I'll write separate articles for each of the tools in the future, this post will just be a pointing in the right direction for lost Erlang developers ;-) Please, if you know any other helpful tools, don't hesitate to post it in the comments and I will add them to the list. I know that this is just a very small overview, but these are all tools that helped me get a better Erlang developer, either by using them and/or by reading their code.</p>
<p>Happy Erlang'ing ;-)</p>
