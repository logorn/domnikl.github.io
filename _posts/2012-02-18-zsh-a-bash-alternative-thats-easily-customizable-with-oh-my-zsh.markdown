---
layout: post
status: publish
published: true
title: zsh - a bash alternative that's easily customizable with oh-my-zsh
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
excerpt: ! "I think I now what you are thinking right now: \"Why do I even NEED an
  alternative to bash?\". And I can tell you I thought the same, too. Bash is perfect,
  there's auto completion, a command history and all those neat things that help you
  being productive when using the shell.\r\n\r\nAnd then one day in mid-2011 I discovered
  the Z shell and once I read about all the nice features it has, I started being
  even more productive and I fell in love with this tool.\r\n\r\n"
date: '2012-02-18 17:14:55 +0100'
date_gmt: '2012-02-18 16:14:55 +0100'
---
<p>I think I now what you are thinking right now: "Why do I even NEED an alternative to bash?". And I can tell you I thought the same, too. Bash is perfect, there's auto completion, a command history and all those neat things that help you being productive when using the shell.</p>
<p>And then one day in mid-2011 I discovered the Z shell and once I read about all the nice features it has, I started being even more productive and I fell in love with this tool.</p>
<p><a id="more"></a><a id="more-344"></a></p>
<p>In this tutorial, I will guide you through the installation of zsh, show you some of the many awesome features that this shell brings to your terminal and I'll give you some tips on how to use this shell with your customizations on any machine that you use.</p>
<h2>Installation</h2>
<p>On Debian and Ubuntu, you only need to install the <strong>zsh</strong> package via apt, MacPorts and Homebrew both also provide a package <strong>zsh</strong>. For other systems, please have a look at the <a href="http://www.zsh.org" target="_blank">official project homepage</a>.</p>
<p>You can start the Z shell with <code>zsh</code> and just play around with it. To make it your default shell (<em>and say goodbye to the bash</em>) run:</p>
<p>[code lang="bash"]<br />
$&gt; chsh -s `which zsh`<br />
[/code]</p>
<h2>Features</h2>
<p>The zsh is based on the bash, so if you work with it, you may be familiar with many features. The Z shell is still in active development and provides many functions that power users of the bash may miss in it. I'm going to show you some of them here.</p>
<h3>Spelling correction</h3>
<p>Zsh tries to help you when you send an unknown command and performs spelling correction on your input. Consider this example:</p>
<p>[code lang="bash"]<br />
$&gt; cta foobar<br />
zsh: correct 'cta' to 'cat' [nyae]?<br />
[/code]</p>
<h3>Suffix aliases</h3>
<p>You may know aliases from bash, but zsh gives aliases even more power: you can assign aliases for prefixes, e.g. if you want to open all files with the suffix .rb in vim do the following:</p>
<p>[code lang="bash"]<br />
$&gt; alias -s rb=vim<br />
$&gt; foo.rb<br />
[/code]</p>
<p>You don't have to type <strong><em>vim foo.rb</em></strong> just <strong><em>foo.rb</em></strong> will then do just the same.</p>
<h3>Hashes</h3>
<p>On my day-to-day work, I use mostly three or four directories (or subdirectories of them) where I do all programming stuff. One of them is ~/Workspace. To go there, regardless of where I am at the moment, I set up a hash alias that points there. It's simple but saves me a lot of typing.</p>
<p>[code lang="bash"]<br />
$&gt; hash w=~/Workspace<br />
[/code]</p>
<p>It's just another form of an alias and now I only have to do <strong><em>cd ~w</em></strong> to go there. Awesome, isn't it?</p>
<h3>auto cd</h3>
<p>I think cd is one of the most used commands in any shell and it can be annoying to type that two letters (and the blank) over and over again. zsh allows you to simply leave them and will detect if what you want to cd to is a directory and do the change.</p>
<p>[code lang="bash"]<br />
$&gt; /usr/local<br />
$&gt; pwd<br />
/usr/local<br />
$&gt; ~w &amp;&amp; pwd<br />
/home/domnikl/Workspace<br />
[/code]</p>
<h3>history</h3>
<p>The history in zsh is even more powerful than that in the bash. You may already know CTRL-R to search in the history, zsh has this too. But consider this: you type "ruby" and want to have all commands that started with that term. Just press arrow up and you will only see entries from the history that started with "ruby".</p>
<p>[code lang="bash"]<br />
$&gt; ruby<br />
$&gt; ruby foobar.rb<br />
$&gt; ruby test.rb<br />
[/code]</p>
<h3>autocompletion</h3>
<p>The auto completion features are one of the main causes why I love zsh. I find it very annoying, that autocompletion in bash is case-sensitive. This is not the case in zsh. And zsh allows programmatic autocompletion, so there's even <em>autocompletion for kill(1)</em> and you can chose the PID with your arrow keys!</p>
<p style="text-align: center;"><a href="zsh_kill_autocompletion.png"><img class="aligncenter  wp-image-375" title="zsh kill(1) auto-completion" src="zsh_kill_autocompletion.png" alt="" width="482" height="256" /></a></p>
<h3>globbing</h3>
<p>zsh supports advanced globbing, e.g. if you use <code>ls **/*.html</code>, the shell will list you all files in any directory under . that has the suffix html.</p>
<h3>advanced cd</h3>
<p>cd in the zsh has another nice feature: you can use it to change the directory by substituting parts of the current working directory with a new part. Let's say you are in <em>/usr/local/bin</em> and want to go to <em>/usr/lib/bin</em>, just do this:</p>
<p>[code lang="bash"]<br />
 $&gt; cd local lib<br />
 $&gt; pwd<br />
 /usr/lib/bin<br />
 [/code]</p>
<p>These are just the most important features for me. I use them really often in my day-to-day work, if you want get more details have a look at <a href="http://zsh.sourceforge.net/Guide/zshguide.html" target="_blank">the ZSH guide</a>.</p>
<h2>Using zsh from more than one machine</h2>
<p>If you own more than one machine, you might want to have all you customizations (aliases and such) on all your machines. I solved this problem with git. Versionize your customizations and put them on github (or another provider). Take a look at my <a title=".home" href="https://github.com/domnikl/.home" target="_blank">.home</a> repository, it contains all my basic settings.</p>
<p>Feel free to fork and add your own settings :)</p>
<h2>using oh-my-zsh</h2>
<p><a href="http://robbyonrails.com/" target="_blank">Robby Russell</a> started an interesting project named oh-my-zsh, where zsh lovers share plugins, settings and themes that help you being even more productive on the shell. <span style="color: #3366ff;">EDIT: don't use the original as it introduces some bugs and is said to be very slow. Use the fork from <a title="oh-my-zsh" href="https://github.com/sorin-ionescu/oh-my-zsh" target="_blank"><span style="color: #3366ff;">sorin-ionescu</span></a> instead.</span> You can find it <a href="https://github.com/robbyrussell/oh-my-zsh" target="_blank">here on github</a>. It also allows you easy customization of your shell prompt. Here's mine:</p>
<p><a href="zsh_prompt.png"><img class="aligncenter size-full wp-image-379" title="zsh_prompt" src="zsh_prompt.png" alt="" width="506" height="39" /></a></p>
<p>As you can see, when I am in directories that contain a git repository, the shell shows me <strong><span style="color: #339966;">which branch I'm on (develop)</span></strong>. The blue part is the<strong><span style="color: #00ccff;"> directory I'm in</span></strong> (last part of the path only) and the yellow chars are <strong><span style="color: #ffcc00;">the hostname</span></strong>. When I am working as root, a <strong><span style="color: #ff0000;">bold red label "root"</span></strong> would warn me of that fact.</p>
<p>That's the end of my little overview on zsh, but I hope you liked it. Try the Z shell and you'll see that it's fun and easy. Have fun! :)</p>
