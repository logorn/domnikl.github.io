---
layout: post
status: publish
published: true
title: messie - a web crawler written in Ruby
author: Dominik Liebler
author_email: liebler.dominik@googlemail.com
date: '2012-02-03 19:35:23 +0100'
date_gmt: '2012-02-03 18:35:23 +0100'
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
