---
layout: post
status: publish
published: true
title: why auto_increments and sequences are anti patterns
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
excerpt: One of the first things every Junior Developer learns regarding relational
  database systems is that storing integers is fast, it doesn't take much space and
   in general, you should favor an integer over a character field if you've got the
  choice.
wordpress_id: 328
wordpress_url: http://thewebdev.de/?p=328
date: '2012-02-07 19:20:30 +0100'
date_gmt: '2012-02-07 18:20:30 +0100'
categories:
- Uncategorized
tags:
- mysql
- databases
- postgresql
- antipattern
- auto_increment
- serial
- sequence
- nosql
- rant
- uuid
comments:
- id: 429
  author: Florian
  author_email: fa@codeschmie.de
  author_url: http://f5n.org
  date: '2012-02-08 19:25:36 +0100'
  date_gmt: '2012-02-08 18:25:36 +0100'
  content: ! "CLI uuidgen? slooow :(\r\nI like the compound primary key solution of
    \"auto_increment + dbhost\" better :)"
- id: 430
  author: Dominik Liebler
  author_email: liebler.dominik@googlemail.com
  author_url: ''
  date: '2012-02-08 19:57:49 +0100'
  date_gmt: '2012-02-08 18:57:49 +0100'
  content: Ok, the CLI uuidgen is the last of all possible alternatives I would use.
    Auto increment + db host sounds good :)
- id: 452
  author: richard
  author_email: richard@bucker.net
  author_url: http://richardbucker.com
  date: '2012-02-13 16:31:09 +0100'
  date_gmt: '2012-02-13 15:31:09 +0100'
  content: ! "On the one-hand you are very right. Using integers or sequences as the
    PK is going to fail in these scenarios, however, using UUIDs as the PK are also
    going to fail but for a different reason. Many DBs evaluate the interval between
    key values and attempt to identify the amount of freespace(extents) needed between
    \ keys....\r\n\r\n... most databases sort their records in physical order based
    on their PK. That means that if you are using a sequence number that the records
    are simply appended to the end of the table file.\r\n\r\n... if you use a string
    or a UUID then the database needs to allocate freespace between records because
    the next insert might put the new record between two existing records. And the
    last thing you want to happen is a reballancing of all of the tables records.
    (This was a huge problem for Oracle many years ago and it could cause lock escalation
    to the table and database level).\r\n\r\n... so a combination is probably best.
    Use the sequence number locally, and create unique secondary index for the UUID.\r\n\r\nPS:
    I do not know what instagram did, but it sounds like something similar to a UUID."
- id: 1151
  author: 分布式环境下ID生成方法总结 | Day Day Up
  author_email: ''
  author_url: http://blog.ddup.us/?p=302
  date: '2012-05-24 08:39:21 +0200'
  date_gmt: '2012-05-24 07:39:21 +0200'
  content: ! '[...] http://code.flickr.com/blog/2010/02/08/ticket-servers-distributed-unique-primary-keys-on-the-cheap/
    http://thewebdev.de/why-auto_increments-and-sequences-are-anti-patterns/   此条目发表在
    分布式系统 分类目录，贴了 distributed-system, uuid [...]'
---
<p>One of the first things every Junior Developer learns regarding relational database systems is that storing integers is fast, it doesn't take much space and  in general, you should favor an integer over a character field if you've got the choice.<a id="more"></a><a id="more-328"></a></p>
<p>There's nothing wrong about that, just remember that a database system can handle values that have a fixed length much faster than values that have a variable length. So naturally it would be a good choice to auto generate an unique sequential integer and store it as the primary key to identify the row in the table.</p>
<p>But there's a reason that most NoSQL data stores don't use sequential IDs. And that's a lession that RDBMS can learn from these. If you take a look around there are SHA1 hashes, "natural" data like the URL as the primary key in Google's Bigtable and you wouldn't use a sequential integer to identify key-value pairs in Redis or Memcache, or would you?</p>
<h2>Scenario 1</h2>
<p>All will be good until the day when your database server is just too slow to handle all incoming requests and you have to scale to a second. Most likely, you implement a sharding algorithm that will distribute the data equally on your two servers and if you need it, on a third one. You can't do that with your auto generated primary key.</p>
<p>Just think of this scenario: Server1 creates a new Invoice row and assigns the ID 1. In the same time, Server2 also creates a new Invoice row and assigns ID 1. How would you know which is which?</p>
<p><a href="http://instagram-engineering.tumblr.com/post/10853187575/sharding-ids-at-instagram" target="_blank">Instagram solved this issue</a> by generating (big integer) IDs that are not sequential but hold a lot of information in it, e.g. a shard number and the current timestamp.</p>
<h2>Scenario 2</h2>
<p>Your app needs a mobile frontend that could also be used when being offline and that syncs all the content to the server when the mobile device is back online again. You would need to identify the new items and the ones that still exist. This is not going to happen well if you use auto-increment values in the database.</p>
<h2>The solution</h2>
<p>Don't rely on auto-generated sequential values in your database. In general don't rely on sequential values. Better use UUIDs instead. PostgreSQL already comes with a <a href="http://www.postgresql.org/docs/9.1/static/datatype-uuid.html" target="_blank">uuid type</a>, or you can generate a unique ID in your application or via a short PLSQL function as Instagram did.</p>
<p>For other RDBMS, generate the UUID in your application, every language has it's own library (or several) to do that. Or you could simply use the <a title="man 1 uuidgen" href="http://manpages.sgvulcan.com/uuidgen.1.php" target="_blank">uuidgen</a> tool on Linux/Mac to do that (ONLY IF YOU DON'T HAVE ANY OTHER FASTER POSSIBILITY).</p>
<p>Use a fixed length character column in your database and set the primary key on it and you'll have a much more flexible solution :)</p>
