---
layout: post
status: publish
published: true
title: messin' around with PHP
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
date: '2011-09-19 19:21:44 +0200'
date_gmt: '2011-09-19 18:21:44 +0200'
---
<p>When you're using PHP you might know that there are a few boundaries when it comes to variable names. Every language has a set of rules for this and the interpreter simply needs them to determine if the actual token is a variable name or not. For PHP, there are few rules: the name must start with a dollar sign ($) followed by either a underscore (_) or a letter a-z (or, of course A-Z), followed by letters, numbers and underscores.</p>
<p>However it is possible to use whatever you want, even whitespace chars! Just consider the following example:</p>
<p>[code lang="php"]<br />
${'1 foo bar'} = 'baz';<br />
echo ${'1 foo bar'}; // will output: baz<br />
[/code]</p>
<p>As you can see, the rules don't apply to variable variables. Now that you know this I have a final advice for you. <strong>Don't ever use this in production code!</strong> It's hard to read, hard to understand and not maintainable! It's good to know one can do this using PHP, but there are always better ways to solve problems than this way.</p>
