---
layout: post
status: publish
published: true
title: big O notation for the rest of us
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 227
wordpress_url: http://thewebdev.de/?p=227
date: '2011-11-02 22:19:06 +0100'
date_gmt: '2011-11-02 21:19:06 +0100'
categories:
- Uncategorized
tags:
- ruby
- databases
- theory
- datastructures
- algorithms
comments:
- id: 199
  author: Pedro
  author_email: pmelendezu@gmail.com
  author_url: ''
  date: '2011-11-03 14:09:09 +0100'
  date_gmt: '2011-11-03 13:09:09 +0100'
  content: ! "Hi,\r\n\r\nI am glad you are explaining algorithm complexity to the
    masses, that's a pretty noble idea.\r\n\r\nHowever, I disagree about your implementation
    of fibonacci being O(2N). An intuition for that is that if you build the tree
    for Fib(5) you would have 8 nodes, where fib(2) is calculated 3 times. \r\n\r\nHere
    you can see people talking about this : http://stackoverflow.com/questions/360748/computational-complexity-of-fibonacci-sequence\r\n\r\nA
    better example for O(2N) would be any algorithm that goes for an entire list twice.
    Let's say Sum(Sum(N,1) , 2)\r\n\r\n\r\nWhere N is a list and Sum(N, 1)  return
    a list with each element of N plus 1\r\n \r\nCheers,"
- id: 202
  author: Dominik Liebler
  author_email: liebler.dominik@googlemail.com
  author_url: ''
  date: '2011-11-03 19:35:34 +0100'
  date_gmt: '2011-11-03 18:35:34 +0100'
  content: Hi Pedro and thanks for your help. I just copied that fibonacci example
    from another site without even thinking about it. I added a new example in the
    text like the one you wrote here.
- id: 51028
  author: ! '@RobinHealey'
  author_email: RobinHealey@twitter.com
  author_url: http://twitter.com/RobinHealey/status/418941182308122626/
  date: '2014-01-03 04:05:36 +0100'
  date_gmt: '2014-01-03 03:05:36 +0100'
  content: To all my @CodeFellowsOrg friends, found a super sweet Big O study sheet
    written for Rubyists. http://t.co/o4uuxbmTbM.
- id: 51044
  author: ! '@ivanoats'
  author_email: ivanoats@twitter.com
  author_url: http://twitter.com/ivanoats/status/418976460284493825/
  date: '2014-01-03 06:25:47 +0100'
  date_gmt: '2014-01-03 05:25:47 +0100'
  content: ! 'RT @RobinHealey: To all my @CodeFellowsOrg friends, found a super sweet
    Big O study sheet written for Rubyists. http://t.co/o4uuxbmTbM.'
- id: 56361
  author: Ivan Storck (@ivanoats)
  author_email: ivanoats@twitter.com
  author_url: http://twitter.com/ivanoats/status/431291533951008768/
  date: '2014-02-06 06:01:29 +0100'
  date_gmt: '2014-02-06 05:01:29 +0100'
  content: ! 'RT @IrisSilverMoon: @ivanoats BigO notation article I mentioned last
    night: http://t.co/kMu4ZoNyTa'
---
<p>Have you ever stumbled upon something like <em>O(N log N)</em> and wondered what that means or what it is good for? I have and of course I wanted to know what that means. From the context I thought it must have something to do with algorithms and their execution times. So what did I do? Of course I went to Wikipedia and yeah I found a page about <a href="http://en.wikipedia.org/wiki/Big_O_notation" target="_blank">Big O notation</a> there. But as I am not that into mathematics I didn't understand very much. I guess so did you, else you weren't here but already on Wikipedia ;-)</p>
<p>The article looks so complex although the notation is not so complex at all. It turned out for me that the Big O notation is indeed a set of formulas to describe the behaviour and, with that, the speed of algorithms. If you want, you can think of it as a rating system. It is used mostly where big amounts of data are involved, e.g. in database systems.</p>
<p>I'll show you some forms of the notation, the following examples are in Ruby, but I think you will get the point even if you're not that into Ruby. You should notice, that the notation always assumes the worst case scenario and execution could be faster under good circumstances (e.g. on early returns).</p>
<h2></h2>
<h2>O(1)</h2>
<p>Algorithms marked with O(1) will always execute in the same time, the size of the dataset will not influence the execution time at all.</p>
<p>[code lang="ruby"]</p>
<p>def replace_first(ar, new_value)<br />
  ar[0] = new_value<br />
  ar<br />
end</p>
<p>[/code]</p>
<h2></h2>
<h2>O(N)</h2>
<p>O(N) says the algorithm will take a linear time range. So if the time is 1/1000 sec. for 1 item, it will take 1 sec. for 1000 items. An example function will iterate over the dataset like this:</p>
<p>[code lang="ruby"]</p>
<p>def greet(names)<br />
  names.each do |name|<br />
    puts &quot;hello, #{name}&quot;<br />
  end<br />
end</p>
<p>[/code]</p>
<h2></h2>
<h2>O(N<sup>2</sup>)</h2>
<p>O(N<sup>2</sup>) means the function will perform proportionally to the square of the input data size. This often is the case if nested loops are running over the input data performing some tasks on it. A commonly known example for this is the Bubblesort, which uses two loops that iterate over the dataset.</p>
<p>[code lang="ruby"]<br />
class Array<br />
  def bubblesort!<br />
    length.times do |j| # iterates over the dataset<br />
      for i in 1...(length - j) # nested iteration<br />
        if self[i] &lt; self[i - 1]<br />
          self[i], self[i - 1] = self[i - 1], self[i]<br />
        end<br />
      end<br />
    end<br />
    self<br />
  end<br />
end<br />
[/code]</p>
<h2></h2>
<h2>O(2<sup>N</sup>)</h2>
<p>On O(2<sup>N</sup>) algorithms execution time will double with each new element. Beware of these as they can get very fast very costly! The example illustrates nicely why that is so, for every method call, there are two new calls to the method itself (only if n &gt; 1):</p>
<p>[code lang="ruby"]<br />
def sum(list, n)<br />
  list.map {|x| x += n}<br />
end</p>
<p>def double_sum(list, n1, n2)<br />
  sum(sum(list, n1), n2)<br />
end<br />
[/code]</p>
<h2></h2>
<h2>O(log N)</h2>
<p>As of here I think the notations were pretty easy to understand, but logarithms are not that easy to explain. So I'll show you the graph for this function first.</p>
<p><img class="alignleft" style="margin: 10px;" src="http://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Binary_logarithm_plot_with_ticks.svg/300px-Binary_logarithm_plot_with_ticks.svg.png" alt="" width="300" height="239" /> As you can see, the curve starts pretty steep but flattens more and more on higher values. Thats why O(log N) functions are very effective on large datasets. A very good example for this is the <a href="http://en.wikipedia.org/wiki/Binary_search_algorithm" target="_blank">Binary Search</a> algorithm, which you might have heard of.</p>
<p>And that's it! These are the commonly used big O notations and if you watch out you will find them just about everywhere :-)</p>
