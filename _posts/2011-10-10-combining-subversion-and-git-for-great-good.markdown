---
layout: post
status: publish
published: true
title: combining Subversion and git for great good!
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 175
wordpress_url: http://thewebdev.de/?p=175
date: '2011-10-10 12:00:34 +0200'
date_gmt: '2011-10-10 11:00:34 +0200'
categories:
- Uncategorized
tags:
- subversion
- git
comments:
- id: 163
  author: ! 'Top New Features in Subversion 1.7: WC-NG &amp; Pristines | Subversion
    Web 2.0 News'
  author_email: ''
  author_url: http://daily20.info/subversion/blog/2011/10/13/top-new-features-in-subversion-1-7-wc-ng-pristines-2/
  date: '2011-10-13 17:39:10 +0200'
  date_gmt: '2011-10-13 16:39:10 +0200'
  content: ! '[...] combining Subversion and git for great good! « the web dev [...]'
---
<p>Sometimes in a project you want to save a state of your code but don't want to commit it because things are broken and you're not sure if it's the right way you are going. Let's say you want to refactor a very large code base. Your team is using a Subversion server and you don't want to commit your single steps in refactoring.<br />
This recently happened to me and I decided to use git while doing the refactoring. Just go to your project dir, git init a new git repo, create a <strong>.gitignore</strong> file and add those lines:</p>
<p><strong>.gitignore</strong></p>
<p>[code]<br />
**/.svn/<br />
.svn/<br />
[/code]</p>
<p>All .svn folders will now be ignored on git commits. Then commit your first step of the refactoring, change some more code and you can easily go back to every step. When you've finished, just commit the last step to the svn repository and delete your git repo (<code>rm -R .git .gitignore</code>). You might not want to commit your .gitignore file to the Subversion repository, so setting the <em>svn:ignore keyword</em> on it will be a good idea.</p>
<p>Done! :)</p>
