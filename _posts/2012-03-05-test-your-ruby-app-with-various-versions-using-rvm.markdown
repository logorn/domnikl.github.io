---
layout: post
status: publish
published: true
title: test your Ruby app with various versions using rvm
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
date: '2012-03-05 22:52:23 +0100'
date_gmt: '2012-03-05 21:52:23 +0100'
---
<p>Recently I started to test my <a title="highscore – a lightweight ruby library that finds and ranks keywords in a string" href="http://thewebdev.de/highscore-a-lightweight-ruby-library-that-finds-and-ranks-keywords-in-a-string/" target="_blank">highscore</a> library on <a href="http://travis-ci.org/#!/domnikl/highscore" target="_blank">Travis CI</a> and they're using rvm on their test machines to easily switch the version and platforms. I only had <a title="Matz Ruby Interpreter" href="http://en.wikipedia.org/wiki/Ruby_MRI" target="_blank">MRI</a> 1.9.3 on my local machine, but had some problems on 1.8.7. Removing 1.9.3 and installing 1.8.7 was no option, so I installed <a href="http://beginrescueend.com/" target="_blank">rvm</a> (Ruby Version Manager) on my machine and I love it! So I am going to talk about it today, the benefits, going through the (easy) installation process and what you should be aware of.</p>
<p>First of all if you don't know it yet: there are several implementations of Ruby interpreters out there: the best known is MRI (Matz-Ruby-Interpreter), it's the first implementation and written in C, then there's <a href="http://www.rubyenterpriseedition.com/" title="REE" target="_blank">Ruby Enterprise Edition</a>, an improved version of the MRI. <a href="http://jruby.org/" title="JRuby" target="_blank">JRuby</a> runs on the Java Virtual Machine, <a href="http://rubini.us/" target="_blank">Rubinius</a> is also written in C, but younger implementation, <a href="http://ironruby.net/" target="_blank">IronRuby</a> runs on the .NET platform and <a href="http://www.macruby.org/" target="_blank">MacRuby</a> runs, well, only on Macs (who would've guessed it?).</p>
<h2>Setup rvm</h2>
<p>Installing rvm is a simple task, all you have to is that:</p>
<p><code>bash -s stable < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer)</code></p>
<p>This will install rvm in your <code>$HOME</code> directory and you should add the following line to your <code>.bashrc</code> (or in your <code>.zshrc</code> if you use the awesome <a title="zsh – a bash alternative that’s easily customizable with oh-my-zsh" href="http://thewebdev.de/zsh-a-bash-alternative-thats-easily-customizable-with-oh-my-zsh/" target="_blank">zsh</a>)</p>
<p><code>source $HOME/.rvm/scripts/rvm</code></p>
<h2>Installing rubies</h2>
<p>Now you have rvm on your system, but you don't have any Rubies in it. <code>rvm list known</code> will give you a list of all Rubies that are available. Start with installing the default Ruby, type <code>rvm install 1.9.3</code> followed by <code>rvm default 1.9.3</code>. Now if you do <code>ruby -v</code>, you should see the 1.9.3 version. If not, start a new shell session, the rvm script must be loaded for the session first.</p>
<p>To switch to another Version or platform, you need the <code>use</code> command: <code>rvm use jruby</code> will switch to the latest JRuby version that you installed.</p>
<h2>ruby gems</h2>
<p>You already may have noticed that all the Rubies are installed in your $HOME directory, in the folder <code>.rvm</code>. All gems that you install will be put in this directory, there's a gems folder for every Ruby that you installed via rvm there. So you need to install gems for every version that you want to use.</p>
<p>Rvm has a lot of functions that go beyond the scope of the article, you could run rake tasks on multiple Ruby versions in one step, install a gem on multiple platforms, run your unit tests on 1.8.7 and 1.9.3 in one step (<code>rvm 1.8.7,1.9.3 do rake task</code>) and much more.<br />
You should definitely check out the <a href="http://beginrescueend.com/set/" target="_blank">documentation</a>. </p>
<p>Playing around with different interpreters and building libraries that run on many Ruby platforms is fun with that wonderful piece of software. Have fun!</p>
