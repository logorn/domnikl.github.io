---
layout: post
title: Think of APIs as Domain-specific languages (DSL)
---
<p>Today's blog post is about why you should think of a DSL when building APIs. Don't be afraid, I am going to explain what a DSLs is if you don't know it by now and I will give you an overview of examples. You might already know them but most developers don't recognize them as domain-specific, but just another language.</p>
<h2>Definition</h2>
<p>First of all, what exactly is a DSL, what does the term domain-specific language stand for? The best way to explain this is by naming the opposite of it, which you already know because you do use it everyday: <em>General-purpose programming languages</em>. Whether it's PHP, Ruby, C(#), Java, ... you can do just about anything with them, that may be developing applications for the web, mobile devices or whatever. But what if you have a specific problem, a problem that has been solved like a thousand times before? For many problems like these, programming languages have been invented that perfectly fit the problem's domain and make it easy to solve it.</p>
<p><a href="http://martinfowler.com/dsl.html" target="_blank">Martin Fowler describes DSLs</a> like that:</p>
<blockquote><p>Domain-specific language: a computer programming language of limited expressiveness focused on a particular domain.</p></blockquote>
<p>He further names a distinction between internal and external languages which means:</p>
<ol>
<li>internal DSLs are built in a specific language and work only for that language</li>
<li>external languages which then need a full parser in the language you want the DSL to use in</li>
</ol>
<h2>Examples</h2>
<h3>external DSLs</h3>
<p>SQL is an external DSL and it's domain should be clear to anyone that ever used it: (relational) data. Another example you all should know is Cascading Stylesheets and it's domain is to style the representation of Markup, mostly used for HTML. Have you ever used a build system like make, rake or ant? These are all external Domain-specific languages which all define a set of commands. Redis (an in-memory database system) and the maintainer of the project, Salvatore Sanfilippo even defined the first of the project's goals in the <a href="http://antirez.com/post/redis-manifesto.html " target="_blank">Redis manifesto</a> as follows:</p>
<blockquote><p>A DSL for Abstract Data Types. Redis is a DSL (Domain Specific Language) that manipulates abstract data types and implemented as a TCP daemon.</p></blockquote>
<h3>internal Domain-specific languages</h3>
<p>I am pretty shure you already used some of the above examples, but what about internal languages? Have you ever come across one? I am sure you have, here are some examples for you:</p>
<p>Sinatra is a Ruby micro HTTP framework (I already <a title="building tiny web apps with Sinatra Part 1" href="http://thewebdev.de/building-tiny-web-apps-with-sinatra-part1/" target="_blank">blogged a tutorial series about Sinatra</a>) that defines a set of commands that help you to build more or less simple web applications or REST services. It's domain is HTTP and if you take a look at it, you will find that it's pretty close to the HTTP specification. Have you ever heard of <a title="learning some Erlang" href="http://thewebdev.de/learning-some-erlang/" target="_blank">Erlang</a>?  It once was an internal DSL at Ericsson, where they used it to build highly concurrent telecommunication applications. Later they open sourced it and now you can use it to build just about anything. It evolved from an internal Domain-specific to a general-purpose language. And JavaScript once has been a DSL to develop interactive web application frontends, but node.js took it out of the browser and made it a general-purpose language.</p>
<h2>What can we learn from DSLs when building APIs?</h2>
<p>Have a look at the above examples and you'll notice that they all share a few principles:</p>
<ul>
<li>define a rather small set of commands</li>
<li>ease of use</li>
<li>just fit the domain's needs - no more, no less</li>
</ul>
<p>And I think this essence should also apply if you build an API, no matter if it's external (say for example a REST interface) or internal. You should always keep it simple and easy to use and don't confuse the user of your API with domain-unrelated things.</p>
