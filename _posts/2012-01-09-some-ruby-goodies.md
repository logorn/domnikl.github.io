---
layout: post
title: some Ruby goodies
---
<p>Hey guys, I've been tooling around with Ruby the last days/weeks and I have learned some little lessons in general Ruby programming. These are some small tipps that I find very useful, especially for Ruby newcomers.</p>
<h2>enhance the load path</h2>
<p>These are 2 equally suited ways to put a folder in the load path. You may use it in your application to avoid using absolute paths.</p>
<p>[code lang="ruby"]<br />
$:.unshift File.join(File.dirname(__FILE__), '..', 'lib')<br />
$LOAD_PATH &lt;&lt; File.join(File.dirname(__FILE__), '..', 'lib')<br />
[/code]</p>
<h2>use OptionParser for CLI apps</h2>
<p>Option Parser is very useful if you need to evaluate CLI parameters in your script.</p>
<p>[code lang="ruby"]<br />
opts = OptionParser.new<br />
opts.on('-h', '--help') { RDoc::usage }<br />
opts.on('-f', '--file FILEPATH') { |filepath| process(filepath) }<br />
[/code]</p>
<h2>RDoc</h2>
<p>You should always use RDoc to comment your classes and methods but you can also use it to automatically create a help message for your CLI app. <strong>RDoc::usage</strong> will read and output it (see OptionParser example).</p>
<p>[code lang="ruby"]<br />
# == Synopsis<br />
#<br />
# This is a sample app comment.<br />
#<br />
# == Usage<br />
#   app [ -h |--help ] [ -f | --file filepath ]<br />
#<br />
# filepath::<br />
#   a valid file path<br />
#<br />
# == Author<br />
# John Doe<br />
#<br />
# == Copyright<br />
# Copyright (c) 2011 John Doe<br />
class Foo<br />
    ...<br />
end<br />
[/code]</p>
