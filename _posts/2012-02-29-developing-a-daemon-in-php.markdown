---
layout: post
status: publish
published: true
title: Developing a daemon in PHP
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 407
wordpress_url: http://thewebdev.de/?p=407
date: '2012-02-29 19:02:53 +0100'
date_gmt: '2012-02-29 18:02:53 +0100'
categories:
- Uncategorized
tags:
- shell
- php
- unix
- daemon
comments:
- id: 585
  author: Jeremy Harris
  author_email: cillosis@gmail.com
  author_url: http://www.jeremyharris.me
  date: '2012-03-01 00:13:36 +0100'
  date_gmt: '2012-02-29 23:13:36 +0100'
  content: ! "What do you suppose would happen if PHP threw a fatal error? With it
    being output to /dev/null you wouldn't immediately know a problem occurred, right?\r\n\r\nAnyway,
    interesting read. I rarely get a chance to think about PHP outside of the typical
    web development arena and this has given me a few ideas."
- id: 586
  author: Dominik Liebler
  author_email: liebler.dominik@googlemail.com
  author_url: ''
  date: '2012-03-01 06:58:09 +0100'
  date_gmt: '2012-03-01 05:58:09 +0100'
  content: I suggest you use set_error_handler() (http://php.net/manual/de/function.set-error-handler.php)
    to define a handler that logs the error to a file before it exits the script.
    Either this or use the error_log() function and set error_log in your php.ini
    config file.
- id: 606
  author: Peter Voringer
  author_email: voringer@businesslogic.de
  author_url: ''
  date: '2012-03-02 15:13:11 +0100'
  date_gmt: '2012-03-02 14:13:11 +0100'
  content: ! "A PHP Daemon is something technical beautiful, but not more than something
    to play with, because in relaity (productive systems) it has a lot of disadvantages,
    that avoid using it.\r\n\r\n- Debugging is still not possible (yeah, you can use
    var_dump, but i mean real debugging with e.g. your IDE). Ever tried to do this?\r\n\r\n-
    Garbage Collection implementation in PHP is buggy/crashy, because it's not designed
    that scripts run over a long time. Therefore the invest of time in this part of
    php was not that large. After some time you get memory leaks and the process crashes,
    because there is not enough memory left. If you use it in scenarios where a large
    amount of data is handled in the daemon and/or the forked childs you will restart
    the daemon each day. There is no possibility to bypass this problem, it happens
    sooner or later.\r\n\r\n- Connection handling: What is the intention of using
    a daemon? How do you interact with it or communicate with it? If you want to write
    a server with it that accepts connections and forks the requests to a child process
    you will get in trouble with script runtimes. In an apache the script stops e.g.
    after 60s (or how you did configure it), but as a child process you have to implement
    logic, that can kill a child process by the parent after a certain time, if you
    have an error in your code (e.g. endless loop or something, that takes too long
    and has no timeout like a wrong DB Query or whatever can happen in large app-environments).
    Otherwise have fun restarting the daemon every hour - saves the restart for memory
    leaks every day ;)\r\n\r\n- No monitoring. There is no monitoring solution. Yes,
    you can implement it, but i think this is a) complex, b) error prone. Productive
    solutions are not available, because the named disadvantages are enough to not
    use it productive.\r\n\r\n\r\nSo can you please tell me, what are the operation
    purposes for a php daemon? I can not find any. Therefore for me it's only something
    to play with, but with no practical benefit. \r\n\r\nIf you want a long running
    application/daemon please use a language, that's designed for these scenario,
    like Java or C/C++ (or whatever that has a good memory management and a language
    internal thread/process handling by design), but never ever use PHP for this.\r\n\r\nBest
    regards\r\n\r\nPeter\r\n\r\nYou can send me a (good) bootle of wine if you read
    this comment and it prevents your company of using a php daemon ;)"
- id: 609
  author: Dominik Liebler
  author_email: liebler.dominik@googlemail.com
  author_url: ''
  date: '2012-03-02 18:42:28 +0100'
  date_gmt: '2012-03-02 17:42:28 +0100'
  content: ! "I already wrote it in reddit, now here again: This is meant be a teaching
    example for PHP developers to understand the Big Picture. I could've done this
    with Ruby, C, Java or whatever but I chose PHP for two reasons: first, there is
    a Ruby example in the post that I mentioned at the beginning of the article and
    second: to show that you could do it in PHP, even if I won't recommend that.\r\n\r\n@Peter
    you are right, it's only meant to be something to play with, so no bottle of wine
    for you, sorry ;-)"
- id: 666
  author: mdpatrick
  author_email: dan@mdpatrick.com
  author_url: http://www.mdpatrick.com/
  date: '2012-03-08 19:18:39 +0100'
  date_gmt: '2012-03-08 18:18:39 +0100'
  content: Are you sure that "." is getting printed to /dev/null? What makes $STDOUT
    the new *real* stdout? So far as I can tell it's just a *variable* (emphasis added)
    with a new open stream on it that has the same name as the constant you closed.
    The behavior is clearly adequate, but I'm just questioning if the specifics are
    accurate. Correct me if I've missed something. :)
- id: 667
  author: Dominik Liebler
  author_email: liebler.dominik@googlemail.com
  author_url: ''
  date: '2012-03-08 20:13:32 +0100'
  date_gmt: '2012-03-08 19:13:32 +0100'
  content: It's just the special name of $STDOUT that makes it the new *real* stdout.
    I've tested this script omitting the reopen step and it won't work, as the echo
    would then write on a closed file descripter. Redefining the constant doesn't
    work either (as far as I know), so I think this is the appropriate way to do this.
- id: 758
  author: Pacifier
  author_email: logslogs@gmail.com
  author_url: ''
  date: '2012-03-21 00:37:48 +0100'
  date_gmt: '2012-03-20 23:37:48 +0100'
  content: Do you even know of the garbage collection of PHP 5.3? Things have improved
    a lot since the last time you ever read about it (yes, you never actually experimented
    with it).
- id: 1701
  author: anon
  author_email: bill.g@hotmail.com
  author_url: http://dev.pedemont.com/sonic
  date: '2012-07-25 04:12:29 +0200'
  date_gmt: '2012-07-25 03:12:29 +0200'
  content: there is also sonic php daemon that might be worth a looksee
- id: 43022
  author: Hrishikesh
  author_email: sprt.email@gmail.com
  author_url: http://hrishikeshmishra.com
  date: '2013-11-25 17:28:50 +0100'
  date_gmt: '2013-11-25 16:28:50 +0100'
  content: ! "Hi Peter,\r\n\r\nI am working in of a large E-commerce company. And
    they have implemented the RabbitMQ consumers through the PHP daemons. And It's
    totally make sense to create daemon here. And there are a lot improvements in
    PHP 5.3 and  PHP 5.4."
---
<p>I've already talked about Unix programming <a title="Unix programming using Ruby" href="http://thewebdev.de/unix-programming-using-ruby/">here</a>, but today I want to go a step   ahead an really implement a daemon, this time I am going to use PHP. You may have already heard of daemons here or there, but I'll give you some facts about them anyway:</p>
<ol>
<li>daemons are long running processes,</li>
<li>they run in the background,</li>
<li>you can't interact with them via a TTY</li>
<li>originated from the Unix world</li>
<li>a common convention is to put a trailing "d" on their name, e.g. <em>http<strong>d</strong></em></li>
</ol>
<p>These are the more obvious attributes of a daemon, but there's a little more to say especially about 2. Let's start PHP in the terminal and put the process in the background:</p>
<p>[code lang="shell"]<br />
php -a &amp;<br />
[/code]</p>
<p>Now if you look through the processes on your system with <code>ps -fax | grep php</code> you will see something like that:</p>
<p>[gist id=1942496 file=psfax_php_a.sh]</p>
<p>The first number is of no interest for us, but the second and the third are. These are the process ID (pid) and the parent process ID (ppid) of our little PHP process. As you can see the parent process is (in my case) 480 and if you do another grep'ing for 480 you can see that this is the shell where you've typed <code>php -a &</code> in. What happens if you log off the shell? All child processes of the shell will die, so will your PHP process.</p>
<p>But daemons should not die when a user logs off, they should run forever! If you go the tree of processes up on your system you might find a process that has the ppid 1. It's the first process that is started when your OS starts and the last one to exit. So we should run our daemon as a child of that process.</p>
<h2>Preconditions</h2>
<p>Before we can implement our first daemon make sure you have the <em>pcntl</em> extension for PHP installed. Most Unix-based programming languages have the necessary functions implemented in the core, but not PHP. Just search for <em>pcntl</em> in your package manager and install the package.</p>
<h2>Our first daemon: mattd</h2>
<p>It does nothing, except printing dots to /dev/null, but that shouldn't matter. It's a demonstration daemon. Here's the dump, I'll go through it and explain what and why we need each line of code in it and what it does:</p>
<p>[gist id=1942496 file=mattd.php]</p>
<p>These are the steps we need to do in the daemon:</p>
<p>&nbsp;</p>
<ol>
<li>fork a new child process</li>
<li><code>pcntl_fork()</code> returns two times, the PID of the parent process and with a 0 for the forked child process</li>
<li>so there are two ways the code runs from here, one is the parent, the other is the child process (if forking was possible)</li>
<li>the parent immediately exits (it's ppid is the shell you started the daemon from)</li>
<li>the child goes in the else branch</li>
<li>a daemon has now working directory, so reset it to /</li>
<li>close all the file descriptors that are bound to the shell used, that is STDIN/OUT/ERR</li>
<li>start a forever-running loop that does something useful</li>
</ol>
<div><span style="font-size: small;"><span style="line-height: 24px;"><br />
</span></span></div>
<p>As I said before we need to run our daemon as a child of the pid 1. We can do this by forking and the exiting the parent process. The then new process runs as a child of our php process first but as this process exits, it has no parent anymore.<br />
But having no parent is not possible, so it will get the new ppid 1.</p>
<h2>Daemon != Cronjob</h2>
<p>Typically, PHP developers are more familiar with developing cronjobs than with daemons and although both are used for similar tasks, they don't share a common idiom. The main difference is that cronjobs are mostly <strong>long</strong>-running processes whereas daemons are <strong>forever</strong>-running processes.</p>
<p>The other thing is that cronjobs are always started in the context of a shell. Daemons don't run in any context, their parent process ID is always 1, the first process started on the system. You can easily test this: create a small PHP script that has an endless loop in it and put it in your crontab. Now wait until the script gets started and do <code>ps -fax | grep you_cronjob</code> and you'll see that your cronjob has a PPID other than 1.</p>
<h2>That's it for now ...</h2>
<p>A short disclaimer to the end: I have not tested this daemon in production nor will I. I am just keen to learn what goes on in the background of Unix programs and I love to share my knowledge to my readers. If I am wrong and you know better, please leave a comment here, thanks :)</p>
