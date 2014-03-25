---
layout: post
status: publish
published: true
title: highscore - a lightweight ruby library that finds and ranks keywords in a string
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 320
wordpress_url: http://thewebdev.de/?p=320
date: '2012-02-05 13:39:17 +0100'
date_gmt: '2012-02-05 12:39:17 +0100'
categories:
- Uncategorized
tags:
- github
- ruby
- open source
- gem
- highscore
- keywords
comments:
- id: 416
  author: Jim Gay
  author_email: Jim@saturnflyer.com
  author_url: ''
  date: '2012-02-05 15:51:41 +0100'
  date_gmt: '2012-02-05 14:51:41 +0100'
  content: Great work! I've been intending to build something like this for a few
    years but haven't ever tried. Can't wait to try it out
- id: 417
  author: Robert Head
  author_email: robert.head@gmail.com
  author_url: ''
  date: '2012-02-05 18:16:30 +0100'
  date_gmt: '2012-02-05 17:16:30 +0100'
  content: ! "NoMethodError: undefined method `upcase' for 98:Fixnum\r\n\tfrom /Users/roberthead/.rvm/gems/ree-1.8.7-2011.03@shopdragon/gems/highscore-0.4.0/lib/highscore/content.rb:52:in
    `keywords'"
- id: 418
  author: Dominik Liebler
  author_email: liebler.dominik@googlemail.com
  author_url: ''
  date: '2012-02-05 18:52:20 +0100'
  date_gmt: '2012-02-05 17:52:20 +0100'
  content: Thanks for the bug report, will fix that as soon as possible and release
    a new version :)
- id: 483
  author: Jeroen van Ingen
  author_email: vingen@zonnet.nl
  author_url: ''
  date: '2012-02-19 01:08:16 +0100'
  date_gmt: '2012-02-19 00:08:16 +0100'
  content: Nice, but I miss the 'whitelist' a little bit. This is because I need to
    search just ONLY for the keywords on the 'whitelist' instead of 'skipping the
    words on the blacklist'.
- id: 487
  author: Dominik Liebler
  author_email: liebler.dominik@googlemail.com
  author_url: ''
  date: '2012-02-19 10:25:15 +0100'
  date_gmt: '2012-02-19 09:25:15 +0100'
  content: Hi Jeroen, I already filed an issue on github for this and will implement
    this feature as soon as possible. Thanks for your feedback :)
- id: 498
  author: Dominik Liebler
  author_email: liebler.dominik@googlemail.com
  author_url: ''
  date: '2012-02-20 21:21:28 +0100'
  date_gmt: '2012-02-20 20:21:28 +0100'
  content: Hey Jeroen, I just released highscore 0.5.0 and you can now use a whitelist
    instead of a blacklist! You can simply get it via ruby gems.
- id: 3525
  author: Augury &#8211; Tools &laquo; Danny
  author_email: ''
  author_url: http://dannyneil.com/2012/12/24/augury-tools/
  date: '2012-12-24 16:29:34 +0100'
  date_gmt: '2012-12-24 15:29:34 +0100'
  content: ! '[...] of pre-existing tools. The rather aging mediawiki library for
    Ruby nonetheless still works, and Highscore does good enough text summarization.
    Combine that with the Crunchbase API snapshot in 2009 and we [...]'
---
<p>I wrote about <a title="messie – a web crawler written in Ruby" href="http://thewebdev.de/messie-a-web-crawler-written-in-ruby/">messie</a> here the other day and what I use it for is that I want to automatically download pages and find keywords in their content. Say for instance, this article should have the keywords "keywords, highscore, ruby" and so on. Just a list of tags that describe this page's content.</p>
<p><a href="https://github.com/domnikl/highscore" target="_blank">Highscore</a> exactly does that. Give it a string and a blacklist (you don't want to have words like "like, you, want" in your keywords or would you?) and it gives you all the important words back. You can configure highscore to rate words based on their characteristics, e.g. upper case words should have a double weight, longs words (say, the threshold is 20 chars) should have half, and so on.</p>
<h2>Features</h2>
<ul>
<li>get the top n words</li>
<li>blacklist words via a file, array or string</li>
<li>default blacklist in the gem</li>
<li>merge different Keywords objects (e.g. from different sources)</li>
<li>configureable to rank different types of words differently (uppercase, long words, etc.)</li>
<li>String has it's own keywords method that you can use</li>
</ul>
<h2>Roadmap</h2>
<ul>
<li>detect the language of a string via "indicator words"</li>
<li>define a blacklist file per language (based on language detection)</li>
<li>fine grain the default blacklist (just a few words atm)</li>
</ul>
<h2>Example</h2>
<p>[code lang="ruby"]<br />
keywords = &quot;This is just a very basic example,<br />
  look at the readme to see what's<br />
  possible using highscore.&quot;.keywords</p>
<p>keywords.rank.each do |word|<br />
  puts word.text<br />
end<br />
[/code]</p>
<h2>Try it!</h2>
<p>[code lang="bash"]</p>
<p>gem install highscore</p>
<p>[/code]</p>
<p>You can find <a href="https://rubygems.org/gems/highscore" target="_blank">highscore on rubygems.org</a> and the sources and bug tracker are on <a href="https://github.com/domnikl/highscore" target="_blank">Github</a>. If you want to add features, feel free to fork the repository and send me a pull request :)</p>
