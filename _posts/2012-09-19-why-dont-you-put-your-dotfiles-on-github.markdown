---
layout: post
title: Why don't you put your dotfiles on Github?
---
<p>What exactly are dotfiles some of you might ask? It's those little settings file that swirl around in your $HOME directory (~) on your Linux or Mac OS X machine and sometime you have to change them to adjust your configuration with them.</p>
<h2>What are dotfiles?</h2>
<p>These might include settings for vim, screen, tmux, bash, <a title="zsh – a bash alternative that’s easily customizable with oh-my-zsh" href="http://thewebdev.de/zsh-a-bash-alternative-thats-easily-customizable-with-oh-my-zsh/" target="_blank">zsh</a> or aliases you use for your daily work on these systems. Or some tools you have written to automate tasks that would otherwise include a list of commands but is now down to a single command.</p>
<h2>How I came to put them there ...</h2>
<p>I had a fairly big amount of these settings and tools that I carried with me. I used to copy them from machine to machine, whether new physical machines or VMs. It was hilarious! I often forgot some and some were lost - forever - till I packed them all in a git repository and put them on <a href="https://github.com/domnikl/.home" target="_blank">Github</a>. Needless to say I didn't put any sensitive data up there ...</p>
<p>Turned out I am not the only one doing this, in fact, there is already an unofficial guide about dotfiles on github out there: <a href="http://dotfiles.github.com" target="_blank">dotfiles.github.com</a>. And many software developers share their settings, aliases and small tools there, too. I advise you to look at their configurations and tools. You can learn a lot from them and of course get some of their tools and use it yourself. These are very interesting setups:</p>
<ul>
<li><a href="http://github.com/ryanb/dotfiles" target="_blank">ryanb/dotfiles</a></li>
<li><a href="http://github.com/rtomayko/dotfiles" target="_blank">rtomayko/dotfiles</a></li>
<li><a href="http://github.com/holman/dotfiles" target="_blank">holman/dotfiles</a></li>
<li><a href="http://github.com/mathiasbynens/dotfiles" target="_blank">mathiasbynens/dotfiles</a></li>
</ul>
<h2>Frameworks</h2>
<p>Many of those use frameworks to build upon for their configuration. I am using <a href="https://github.com/sorin-ionescu/prezto" target="_blank">prezto</a>, which is a fork of oh my zsh, but with better performance and some more features. It allows you to add plugins for git, syntax highlighting, tmux, screen and many, many others very easily and gets you going in no time.</p>
<h2>Sharing</h2>
<p>Github calls itself a social coding platform and I think it's a very good aspect to share also some tools and settings we use for our daily work. My dotfile repository was to this date forked by five other people and everyone picked the things they liked and threw away the other stuff and added their configurations. And I love that, because I learned some new tools, too :)</p>
<p>I would love to see a link to your Github dotfiles repository in the comments. Come on, it's easy and you will earn a lot from it!</p>
