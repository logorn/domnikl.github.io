---
layout: post
title: highscore - a lightweight ruby library that finds and ranks keywords in a string
---
I wrote about [messie](/messie-a-web-crawler-written-in-ruby/) here the other day and what I use it for is that I want to automatically download pages and find keywords in their content. Say for instance, this article should have the keywords "keywords, highscore, ruby" and so on. Just a list of tags that describe this page's content.

[Highscore](https://github.com/domnikl/highscore) exactly does that. Give it a string and a blacklist (you don't want to have words like "like, you, want" in your keywords or would you?) and it gives you all the important words back. You can configure highscore to rate words based on their characteristics, e.g. upper case words should have a double weight, longs words (say, the threshold is 20 chars) should have half, and so on.

### Features


* get the top n words
* blacklist words via a file, array or string
* default blacklist in the gem
* merge different Keywords objects (e.g. from different sources)
* configureable to rank different types of words differently (uppercase, long words, etc.)
* String has it's own keywords method that you can use 

### Roadmap


* detect the language of a string via "indicator words"
* define a blacklist file per language (based on language detection)
* fine grain the default blacklist (just a few words atm)
* a.s.o.

### Example


```ruby
keywords = "This is just a very basic example,
  look at the readme to see what's
  possible using highscore.".keywords

keywords.rank.each do |word|
  puts word.text
end
```

### Try it!


```ruby
gem install highscore
```

You can find [highscore on rubygems.org](https://rubygems.org/gems/highscore) and the sources and bug tracker are on [Github](https://github.com/domnikl/highscore). If you want to add features, feel free to fork the repository and send me a pull request :)

