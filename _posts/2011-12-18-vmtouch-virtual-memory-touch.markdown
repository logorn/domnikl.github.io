---
layout: post
status: publish
published: true
title: vmtouch - virtual memory touch
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 268
wordpress_url: http://thewebdev.de/?p=268
date: '2011-12-18 22:17:42 +0100'
date_gmt: '2011-12-18 21:17:42 +0100'
categories:
- Uncategorized
tags:
- linux
- performance
- cache
comments:
- id: 457
  author: Johnnie Yankovitz
  author_email: Cantave7236@hotmail.com
  author_url: ''
  date: '2012-02-15 06:17:56 +0100'
  date_gmt: '2012-02-15 05:17:56 +0100'
  content: Appreciate it for helping out, excellent information.
- id: 7425
  author: knight
  author_email: equibrilium@gmail.com
  author_url: ''
  date: '2013-03-25 16:25:09 +0100'
  date_gmt: '2013-03-25 15:25:09 +0100'
  content: best vmtouch tutorial
---
<p>vmtouch is a tiny little tool that could be very useful to you if you want to improve performance on a low level basis or just learn something about the file system cache in Linux.</p>
<p>Database indices are most useful when they are in the RAM, but on large databases this often isn't the case. So index files that are stored on the hard disk are used. To get better performance, this files should be held in the file system cache. Of course, this doesn't only apply to database systems. You can touch all types of files to get them into the cache and get them loaded fast.</p>
<h2>Installation</h2>
<p>Installing <a href="http://hoytech.com/vmtouch/" target="_blank">vmtouch</a> isn't that complicated. It comes as a single C file without any dependency. Just make sure gcc is installed on your target system. Download the C file:</p>
<p>[code lang="bash"]<br />
wget http://hoytech.com/vmtouch/vmtouch.c<br />
[/code]</p>
<p>and compile it using gcc:</p>
<p>[code lang="bash"]<br />
 gcc -Wall -O3 -o vmtouch vmtouch.c<br />
 [/code]</p>
<p>This will (if all goes well) create an executable file vmtouch, which we will then use to get information about the file system cache and load files into it.</p>
<h2>Using vmtouch</h2>
<p>First of all, I want to now how much of my machine's /bin directory is in the cache. Simply run</p>
<p>[code lang="bash"]vmtouch /bin[/code]</p>
<p>and you will see something like this:</p>
<p>[code lang="bash"]</p>
<p>Files: 44<br />
 Directories: 1<br />
 Resident Pages: 715/3948 2M/15M 18.1%<br />
 Elapsed: 0.34154 seconds</p>
<p>[/code]</p>
<p>The important part in the output is the Resident Pages, you see 18.1% of my /bin directory is currently in the file system cache. Note that on large directories it will shurely run longer than under one second and that you can run vmtouch on both files and directories.</p>
<p>Now that we have found out that git (which is in /bin) isn't in the cache, but our application heavily relies on it and we want to improve performance, we want to get that file into the cache. (Note: this is a fictional use case!)</p>
<p>[code lang="bash"]</p>
<p>$ vmtouch -vt /bin/git</p>
<p>/bin/git<br />
[OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO] 344/344</p>
<p>Files: 1<br />
 Directories: 0<br />
 Touched Pages: 344 (1M)<br />
 Elapsed: 0.1636 seconds</p>
<p>[/code]</p>
<p>Voilá! git is now in the file system cache and if you run vmtouch /bin/git you will see that 100% are in the cache. I encourage you to experiment with that tool, e.g. use tail/head/cat and see how much of the files you are viewing are loaded in the cache, etc. Have fun!</p>
