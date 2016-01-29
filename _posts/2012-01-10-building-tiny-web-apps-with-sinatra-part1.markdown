---
layout: post
status: publish
published: true
title: building tiny web apps with Sinatra Part 1
author: Dominik Liebler
author_email: liebler.dominik@googlemail.com
date: '2012-01-10 22:32:59 +0100'
date_gmt: '2012-01-10 21:32:59 +0100'
---
<p>Sinatra is an awesome, lightweight and easy to learn little web framework written in Ruby. You may want to use it for projects when Rails is just too much, e.g. for small webservices or small web apps. It will run with many great Ruby webservers, such as Webrick, Mongrel (recommended), thin or Puma (which I prefer).</p>
<p>To get started, you have to install the gem.</p>
<p>[code lang="bash"]<br />
gem install sinatra<br />
[/code]</p>
<p>We will create a little and very basic blog app, and our backlog contains only 3 features: to view the front page that shows us all articles, create new articles and view them. A little disclaimer here: It will be a oldschool web application: no AJAX, no javascript at all. Building RESTful services with Sinatra isn't that complicated and I will show you in a future article how to build a service.</p>
<p>First, we need a file that acts as the controller for Sinatra. You may be used to create multiple controllers classes in their respective file (e.g. in Rails), but Sinatra only needs this single file and we will put all our actions in there. Sinatra merely uses a router inspired pattern. So we only need a new file <strong>blog.rb</strong>.</p>
<p>[code lang="ruby"]<br />
require 'rubygems'<br />
require 'sinatra'</p>
<p>get '/' do<br />
&quot;Hello World!&quot;<br />
end<br />
[/code]</p>
<p>Now just run this file with</p>
<p>[code lang="bash"]ruby blog.rb[/code]</p>
<p>I prefer to chmod +x it and run it directly but I guess that's just a matter of taste. Now if you point your browser to <a href="http://localhost:4567">http://localhost:4567/</a> you should see <em>Hello World!</em></p>
<p>This is the simplest action that you can do in Sinatra. As you can see, it has it's own DSL that is really pretty straightforward and easy to use. "<strong>get</strong>" indicates it matches GET requests. <strong>'/'</strong> is the route that will be matched and the return value of the block ("Hello World!" will get returned if you are not so familiar with Ruby) will be sent to the browser.</p>
<p>Now wasn't that fast? 5 lines of code to display a hello world and run it on a webserver? That's what I call rapid protoyping ;-) But let's move on writing our blog app.</p>
<h2>using Rack</h2>
<p>You could of course run your app just as we did using Sinatra with Mongrel. But it's better (and more fun) to run it with <a href="http://rack.rubyforge.org/" target="_blank">rack</a>, a webserver interface for Ruby. It's lightweight and very to get started with. First of all we refactor our existing blog.rb and define a class for our app.</p>
<p>[code lang="ruby"]<br />
class MyBlog &lt; Sinatra::Base<br />
  get '/' do<br />
    &quot;Hello World!&quot;<br />
  end<br />
end<br />
[/code]</p>
<p>Then you need a <strong>config.ru</strong> file that contains the config for the server:</p>
<p>[code lang="ruby"]<br />
require 'blog'<br />
run MyBlog.new<br />
[/code]</p>
<p>Now I recommend you to use shotgun, a webserver especially for development purposes. <strong><em>gem install shotgun</em></strong> and <em><strong>shotgun config.ru </strong></em>and your server is up and running again. If you want to use a Sinatra application in production, better use Puma instead. It supports a thread pool that you can configure.</p>
<h2>1st Feature: show all articles on the front page</h2>
<p>So our base system is running and we can go on and finally implement the blog system. I decided to stay lightweight and not use a database at all. If you insist on using a database system, I'll recommend you to use SQLite3 with ActiveRecord but that would just be a bit too much for that tutorial, so we'll use single JSON files. Create a new <strong>data</strong> folder in the app's root path where we will put our posts in. Then create our first post in a new JSON file <strong>data/1.json</strong>:</p>
<p>[code lang="json"]<br />
{<br />
	&quot;title&quot;: &quot;Sinatra is great!&quot;,<br />
	&quot;body&quot;: &quot;Yeah!&quot;<br />
}<br />
[/code]</p>
<p>It's a very basic format and you'll add some more fields but for now that's enough. Now we need to load this file (and hopefully many more to come) to display them on the start page. The convention is to have a <strong>lib</strong> folder where you have all your library stuff in, so create it in your app's path. I've written a basic class that loads all JSON files and creates an array of Post objects, just save it as <strong>lib/post.rb</strong> and add a require statement in your blog.rb file.</p>
<p>[code lang="ruby"]<br />
require 'json'</p>
<p>class Post<br />
  def self.load_files(directory = 'data/')<br />
    posts = []<br />
    Dir.glob(directory + '*.json').each do |file|<br />
      post = JSON.load(File.read(file))<br />
      id = File.basename(file, '.json')</p>
<p>      posts &lt;&lt; self.new(:id =&gt; id, :body =&gt; post['body'], :title =&gt; post['title'])<br />
    end</p>
<p>    posts<br />
  end</p>
<p>  attr_reader :id, :title, :body</p>
<p>  def initialize(options)<br />
    @id = options[:id]<br />
    @body = options[:body]<br />
    @title = options[:title]<br />
  end<br />
end<br />
[/code]</p>
<p>We just need to run Post.load_files in our little app. Sinatra has it's own method before here, that will be run before each request is handled:</p>
<p>[code lang="ruby"]<br />
require 'lib/post'</p>
<p>class MyBlog &lt; Sinatra::Base<br />
  before do<br />
    @posts = Post.load_files<br />
  end</p>
<p>  ...<br />
end<br />
[/code]</p>
<p>@posts will now contain an array of Post objects that were loaded from our data folder. Now change the action to render a erb (embedded Ruby) template instead of just plain text.</p>
<p>[code lang="ruby"]<br />
get '/' do<br />
  erb :home, :locals =&gt; {:posts =&gt; @posts}<br />
end<br />
[/code]</p>
<p>What we are doing in here is just calling a Sinatra helper <strong>erb</strong> and give it our @<strong>posts</strong> instance variable that will be available in the template as a local variable <strong>posts</strong>.<br />
Sinatra will now look for a home.erb file in the directory views/, so create it and put the view code in it:</p>
<p>[code lang="ruby"]<br />
&lt;h1&gt;my blog&lt;/h1&gt;</p>
<p>&lt;% posts.each do |post| %&gt;<br />
	&lt;h2&gt;&lt;%= post.title %&gt;&lt;/h2&gt;<br />
&lt;% end %&gt;<br />
[/code]</p>
<p>This is pretty simple, just a little ruby code embedded in HTML fragments and we only show the post's title.</p>
<p>So that's it for today and I hope you had much fun! There are plenty of other cool things to learn regarding Sinatra and we'll implement the outstanding two features in the next article.</p>
