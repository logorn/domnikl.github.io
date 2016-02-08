---
layout: post
title: The Erlang stack
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
