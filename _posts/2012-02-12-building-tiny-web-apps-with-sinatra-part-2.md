---
layout: post
title: building tiny web apps with Sinatra part 2
---
<p>It's been a while since <a title="building tiny web apps with Sinatra Part 1" href="http://thewebdev.de/building-tiny-web-apps-with-sinatra-part1/">Part 1</a> but I'm here again to implement the outstanding two features. That is: showing an article and creating new articles.</p>
<h2>Feature 2: show a single article per page</h2>
<p>We'll start with showing a single article per page, the routing for this will be /posts/:id, so that the first article will be /posts/1 etc. I started with implementing a method in the Post class that will load one single file, given the id of the post:</p>
<p>[gist id=1808449 file=sinatra_part2_post.rb]</p>
<p><a id="more"></a><a id="more-341"></a></p>
<p>Then we need a method in the blog.rb that responds to the route <em>/post/:id</em>, loads the post and serves the view. This is actually very straight-forward:</p>
<p>[gist id=1808449 file=sinatrag_part2_blog.rb]</p>
<p>The only magic here (if one would say so) is, that we get all parameters in a Hash called <strong>params</strong>. All we need to complete this feature is a view that displays the article of course. But this is now up to you, it shouldn't be very difficult if you read part 1 of this tutorial.</p>
<p>The last step of this feature is then to add a link from the homepage to each article. That too shouldn't be very complicated for you ;-)</p>
<h2>Feature 3: create new articles</h2>
<p>For this feature, we need 2 routes: one to display a form and one to save the contents of the form to a new JSON file.</p>
<p>The first one again is simple. Just put it above the /post/:id route, otherwise it will never be matched and sinatra will display you an article with ID "new" that doesn't exist!</p>
<p>[gist id=1808449 file=sinatra_part2_blog_new.rb]</p>
<p>And the view for this is a form that contains fields for all the data we need for a new post:</p>
<p>[gist id=1808449 file=sinatrag_part2_blog_form.rb]</p>
<p>So we can now create new articles but they will not get saved when you hit the submit button. For this to happen, we need to extend the Post class again and add a method to save a post in a JSON file:</p>
<p>[gist id=1808449 file=sinatra_part2_blog_post.rb]</p>
<p>By now, we've only handled GET requests, but you shouldn't use GET when data is being updated or created. So our new method to save the post is a bit different from what we've done before:</p>
<p>[gist id=1808449 file=sinatra_part2_blog_create.rb]</p>
<p>Again, put that new method above the /post/:id route! Since we implemented the save method in the Post class, there's not much to see here.</p>
<p>So that's it. We've implemented all core features of the blog and you can now create and read posts on your shiny new blog. There are still features that I would miss on a good blog system, but that's just the start.</p>
<p>Just remember: Sinatra is very lightweight but you can implement a small system like this blog in a short time. Many people use it for small REST services, simple Web frontends and things like this. Github uses Sinatra and git for their lightweight wiki <a href="https://github.com/github/gollum" target="_blank">gollum</a>, a web crawler that I implemented called <a title="messie – a web crawler written in Ruby" href="http://thewebdev.de/messie-a-web-crawler-written-in-ruby/" target="_blank">messie</a> uses it for it's unit tests to be independent of an internet connection.</p>
<p>Sinatra is so cool, because it's just a thin layer on top of HTTP, that will not stand in your way, regardless of what you want to accomplish. Have fun building tiny web apps with it! :)</p>
