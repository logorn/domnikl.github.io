---
layout: post
title: Developing a daemon in PHP
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
