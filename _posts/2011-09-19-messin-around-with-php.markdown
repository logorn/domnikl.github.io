---
layout: post
status: publish
published: true
title: messin' around with PHP
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 153
wordpress_url: http://thewebdev.de/?p=153
date: '2011-09-19 19:21:44 +0200'
date_gmt: '2011-09-19 18:21:44 +0200'
categories:
- Uncategorized
tags:
- fun
- php
- codingstyle
comments:
- id: 151
  author: DreamHost Reviews
  author_email: rkneyewq@gmail.com
  author_url: http://www.cheapwebsitehostingreviews.net
  date: '2011-09-29 02:23:07 +0200'
  date_gmt: '2011-09-29 01:23:07 +0200'
  content: ! "I think other web site proprietors should take this site as an model,
    very clean and great user friendly style and design, as well as the content. You’re
    an expert at this stuff!   \r\nMy blog is about <a href=\"http://www.cheapwebsitehostingreviews.net\"
    rel=\"nofollow\">DreamHost Reviews</a>."
- id: 157
  author: Nancy
  author_email: slimnancy@gmx.com
  author_url: ''
  date: '2011-10-03 17:46:38 +0200'
  date_gmt: '2011-10-03 16:46:38 +0200'
  content: ! "Thanks for  the share!   \nNancy.R"
---
<p>When you're using PHP you might know that there are a few boundaries when it comes to variable names. Every language has a set of rules for this and the interpreter simply needs them to determine if the actual token is a variable name or not. For PHP, there are few rules: the name must start with a dollar sign ($) followed by either a underscore (_) or a letter a-z (or, of course A-Z), followed by letters, numbers and underscores.</p>
<p>However it is possible to use whatever you want, even whitespace chars! Just consider the following example:</p>
<p>[code lang="php"]<br />
${'1 foo bar'} = 'baz';<br />
echo ${'1 foo bar'}; // will output: baz<br />
[/code]</p>
<p>As you can see, the rules don't apply to variable variables. Now that you know this I have a final advice for you. <strong>Don't ever use this in production code!</strong> It's hard to read, hard to understand and not maintainable! It's good to know one can do this using PHP, but there are always better ways to solve problems than this way.</p>
