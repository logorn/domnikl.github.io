---
layout: post
status: publish
published: true
title: messie - a web crawler written in Ruby
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 303
wordpress_url: http://thewebdev.de/?p=303
date: '2012-02-03 19:35:23 +0100'
date_gmt: '2012-02-03 18:35:23 +0100'
categories:
- Uncategorized
tags:
- github
- ruby
- messie
- open source
- gem
comments:
- id: 403
  author: liliff
  author_email: icelandisbeingcolouredbywrens@gmail.com
  author_url: http://nia.teppel.in
  date: '2012-02-04 11:21:47 +0100'
  date_gmt: '2012-02-04 10:21:47 +0100'
  content: You should probably add a link to the GitHub page. :)
- id: 404
  author: Dominik Liebler
  author_email: liebler.dominik@googlemail.com
  author_url: ''
  date: '2012-02-04 11:26:40 +0100'
  date_gmt: '2012-02-04 10:26:40 +0100'
  content: Yes, you're right, I added the link. Thanks :)
- id: 405
  author: mehdi
  author_email: mehdi.adda@gmail.com
  author_url: ''
  date: '2012-02-04 13:38:24 +0100'
  date_gmt: '2012-02-04 12:38:24 +0100'
  content: Hi, have you looked at anemone (https://github.com/chriskite/anemone)?
- id: 406
  author: Dominik Liebler
  author_email: liebler.dominik@googlemail.com
  author_url: ''
  date: '2012-02-04 13:58:24 +0100'
  date_gmt: '2012-02-04 12:58:24 +0100'
  content: Yes, I first thought of using anemone, but then decided it's not as lightweight
    as I need it to be. It relies on a complete stack with Redis, MongoDB and so on
    to run and I just don't wanted that. Messie is a lot more flexible, it just gives
    a nice API and you can do whatever you want with it. Anemone is a full stack,
    while messie is just a lightweight API on top of Net::HTTP.
- id: 407
  author: Dan F
  author_email: dan@danfinnie.com
  author_url: http://danfinnie.com
  date: '2012-02-04 18:13:41 +0100'
  date_gmt: '2012-02-04 17:13:41 +0100'
  content: ! "Hey, this actually looks really cool &amp; useful for a sideproject
    I wanted to complete.  One question though, does it automatically visit all the
    links?  Or if I wanted to spider a page would I have to do something like this?\r\n\r\nseen
    = Set.new\r\n\r\ndef visit_page(url)\r\n  page = Messie::Page.crawl(url) do \r\n
    \  ...\r\n  end\r\n\r\n  (page.links.to_set - seen).each {|x| visit_page(x) }\r\n
    \ seen += page.links\r\nend\r\n\r\nvisit_page(\"google.com\")"
- id: 408
  author: Eric Hodel
  author_email: drbrain@segment7.net
  author_url: http://blog.segment7.net
  date: '2012-02-04 18:39:10 +0100'
  date_gmt: '2012-02-04 17:39:10 +0100'
  content: ! "Why not use mechanize instead of reinventing the wheel?  Looking through
    your code, mechanize supports the following features that you'll spend days reimplementing:\r\n\r\nPersistent
    connections for improved speed\r\n\r\nValidated SSL connections for proper security
    (you're lacking  VERIFY_PEER)\r\n\r\nrobots.txt parsing (mechanize uses webrobots)\r\n\r\nCorrect
    handling of links (normalization, base element, HTTPS scheme capitalization)\r\n\r\nBroken
    page encodings and content encodings.\r\n\r\nThe refresh header\r\n\r\nAnd many,
    many more workarounds for minor bugs in servers and pages."
- id: 409
  author: Dominik Liebler
  author_email: liebler.dominik@googlemail.com
  author_url: ''
  date: '2012-02-04 19:00:28 +0100'
  date_gmt: '2012-02-04 18:00:28 +0100'
  content: ! "Hey Dan F,\r\n\r\nat the moment you have to do this but I will add support
    for such scenarios in the future :)"
- id: 410
  author: Dominik Liebler
  author_email: liebler.dominik@googlemail.com
  author_url: ''
  date: '2012-02-04 19:02:54 +0100'
  date_gmt: '2012-02-04 18:02:54 +0100'
  content: ! "Hi Eric,\r\n\r\nyes you are right, but I just found mechanize a couple
    of days after I started to develop messie. I'll have a look at it :)"
- id: 412
  author: dchuk
  author_email: me@dchuk.com
  author_url: http://layeredthoughts.com
  date: '2012-02-05 04:12:02 +0100'
  date_gmt: '2012-02-05 03:12:02 +0100'
  content: Hey, good stuff making your own scraper gem, they're fun to build. I built
    http://github.com/dchuk/Arachnid might want to check it out to see how I implemented
    bloom filters in my recursive crawling system. Hope it helps.
- id: 414
  author: highscore &#8211; a lightweight ruby library that finds and ranks keywords
    in a string
  author_email: ''
  author_url: http://thewebdev.de/highscore-a-lightweight-ruby-library-that-finds-and-ranks-keywords-in-a-string/
  date: '2012-02-05 13:39:20 +0100'
  date_gmt: '2012-02-05 12:39:20 +0100'
  content: ! '[...] wrote about messie here the other day and what I use it for is
    that I want to automatically download pages and find [...]'
- id: 458
  author: Felipe Lima
  author_email: felipe.lima@gmail.com
  author_url: http://felipecsl.com
  date: '2012-02-15 07:53:22 +0100'
  date_gmt: '2012-02-15 06:53:22 +0100'
  content: You might also want to check out wombat (http://github.com/felipecsl/wombat)
    that I built on top of Nokogiri. It is a Ruby DSL to specify web crawlers.
- id: 42350
  author: 格安通販 スニーカー 最高級
  author_email: anitra_gutierrez@gmail.com
  author_url: ''
  date: '2013-11-20 08:11:31 +0100'
  date_gmt: '2013-11-20 07:11:31 +0100'
  content: I like it when folks get together and share ideas. Great blog, continue
    the good work!
---
<p>A few weeks ago I wrote my first two gems and released them on <a href="https://rubygems.org/profiles/7069" target="_blank">rubygems.org</a>. The first one about I will talk today is <strong><em>messie</em></strong>. I often want to crawl web pages in tiny little projects I do, so I thought: "Why not write a gem that I can use for every project and that handles crawling of web pages in an abstract manner".</p>
<h2>Features</h2>
<p>By now, messie is still &lt; 1.0 (currently 0.3.2) so it shurely isn't perfect yet, but it already has a lot of features that might be very useful to you.</p>
<ul>
<li>set your own User Agent header</li>
<li>set other custom headers via a fancy API</li>
<li>messie will follow a HTTP redirection max. 3 levels deep</li>
<li>HTTPS is supported</li>
<li>get the full HTML or just a text version</li>
<li>records the response time of the page</li>
</ul>
<h2>Roadmap</h2>
<ul>
<li>get a array of links on the page to continue crawling recursively</li>
<li>enable caching support (304 Not modified)</li>
<li>read binary data and convert it to text (e.g. PDFs)</li>
</ul>
<h2>Try it!</h2>
<p>To install it, just use gem:</p>
<p>[code lang="bash"]</p>
<p>gem install messie</p>
<p>[/code]</p>
<p>Read the README.md at <a href="https://github.com/domnikl/messie" target="_blank">github.com</a> to get on from here. If you need help just file an issue on github or fork the repository and send me a pull request, I'd be happy about it :)</p>
