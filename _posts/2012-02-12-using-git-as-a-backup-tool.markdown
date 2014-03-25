---
layout: post
status: publish
published: true
title: using git as a backup tool
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
excerpt: ! "I recently had the problem, that I did not do any kind of backup of this
  site. The blog has grown since I began blogging again about a year ago and especially
  in the past few weeks since I relased <a href=\"https://rubygems.org/gems/messie\"
  target=\"_blank\">messie</a> and <a href=\"https://rubygems.org/gems/highscore\"
  target=\"_blank\">highscore</a> under the MIT license.\r\n\r\nI don't wanted to
  loose all posts and backup at least the database (it's a MySQL system). In the past
  I dumped the complete schema and downloaded that via SFTP onto my local machine,
  but it's always the same: You set it up and all is ok and it runs for a few months.
  Then something unexpected happens and the dump is not downloaded but you don't have
  time nor want to do that whole thing again and see what failed and so on. That goes
  on and on and on.\r\n\r\n"
wordpress_id: 348
wordpress_url: http://thewebdev.de/?p=348
date: '2012-02-12 19:30:47 +0100'
date_gmt: '2012-02-12 18:30:47 +0100'
categories:
- Uncategorized
tags:
- mysql
- git
- backup
comments: []
---
<p>I recently had the problem, that I did not do any kind of backup of this site. The blog has grown since I began blogging again about a year ago and especially in the past few weeks since I relased <a href="https://rubygems.org/gems/messie" target="_blank">messie</a> and <a href="https://rubygems.org/gems/highscore" target="_blank">highscore</a> under the MIT license.</p>
<p>I don't wanted to loose all posts and backup at least the database (it's a MySQL system). In the past I dumped the complete schema and downloaded that via SFTP onto my local machine, but it's always the same: You set it up and all is ok and it runs for a few months. Then something unexpected happens and the dump is not downloaded but you don't have time nor want to do that whole thing again and see what failed and so on. That goes on and on and on.</p>
<p><a id="more"></a><a id="more-348"></a></p>
<p>The other day I read <a href="http://devsundar.github.com/2012/02/09/Uses-of-git/" target="_blank">this blog post about using git</a> for other solutions than only version control. And then it dawned on me: why not use git and push everything to a remote repository. Git only saves the diff between two versions, so it wouldn't cost that much if I want to have a backup made hourly.</p>
<p>I already had an account on <a href="https://bitbucket.org/" target="_blank">bitbucket.org</a> (check it out, it's free and you can have as much private repos as you want!), so I created a new for my backup.</p>
<p>A cronjob then dumps the database, commits the dump and pushes the new version to bitbucket. It's that easy and it just costed me 10 minutes to write a short bash script for that and check that it works.</p>
<p>Sometimes, the solution isn't that far away but one have to think outside the box to reach it :)</p>
