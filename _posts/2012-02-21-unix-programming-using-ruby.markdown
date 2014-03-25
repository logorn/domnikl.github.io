---
layout: post
status: publish
published: true
title: Unix programming using Ruby
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 396
wordpress_url: http://thewebdev.de/?p=396
date: '2012-02-21 18:55:18 +0100'
date_gmt: '2012-02-21 17:55:18 +0100'
categories:
- Uncategorized
tags:
- ruby
- unix
comments:
- id: 556
  author: Jesse Storimer
  author_email: jstorimer@gmail.com
  author_url: http://jstorimer.com
  date: '2012-02-27 16:09:30 +0100'
  date_gmt: '2012-02-27 15:09:30 +0100'
  content: Glad you're liking the series! You got it exactly, I think it's important
    to learn what's behind the tools we use everyday and demystify what we don't understand.
    Should be a fun ride :)
- id: 583
  author: Developing a daemon in PHP
  author_email: ''
  author_url: http://thewebdev.de/developing-a-daemon-in-php/
  date: '2012-02-29 19:02:55 +0100'
  date_gmt: '2012-02-29 18:02:55 +0100'
  content: ! '[...] already talked about Unix programming here, but today I want to
    go a step   ahead an really implement a daemon, this time I am going to use [...]'
---
<p>The other day I blogged about an alternative for bash, <a title="zsh – a bash alternative that’s easily customizable with oh-my-zsh" href="http://thewebdev.de/zsh-a-bash-alternative-thats-easily-customizable-with-oh-my-zsh/">zsh</a>. But what if you want to write your own shell that behaves exactly like you want it to?</p>
<p><a href="http://jstorimer.com/" target="_blank">Jesse Storimer</a> (the author of the truly great <a href="http://workingwithunixprocesses.com" target="_blank">Working with Unix Processes</a> and already working on his Unix beard ;-)) has just started a new <a href="http://jstorimer.com/2012/02/16/a-unix-shell-in-ruby.html" target="_blank">series of blog posts</a> in which he'll explain how to write the quintessential of a Unix program - a basic shell in Ruby.</p>
<p>Today most of the web development or software development in general happens on Unix machines, whether it's Linux, Mac OS or BSD. Personally I don't use any other systems, so why don't learn some of the basics and understand the big picture that's behind those architectures?</p>
<p>Of course, this is just a little project for demonstration and learning purpose but there really is an interactive shell written in Ruby and it also uses Ruby as it's input language. Say hello to <a href="http://rush.heroku.com" target="_blank">rush</a>.</p>
