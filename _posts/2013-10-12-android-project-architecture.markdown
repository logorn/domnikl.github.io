---
layout: post
status: publish
published: true
title: Android project architecture
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 592
wordpress_url: http://thewebdev.de/?p=592
date: '2013-10-12 10:30:49 +0200'
date_gmt: '2013-10-12 09:30:49 +0200'
categories:
- Uncategorized
tags:
- android
- java
- singleton
- dependency injection
comments:
- id: 35831
  author: Dominik Liebler (@domnikl)
  author_email: domnikl@twitter.com
  author_url: http://twitter.com/domnikl/status/389023468441706496/
  date: '2013-10-12 14:43:17 +0200'
  date_gmt: '2013-10-12 13:43:17 +0200'
  content: ! '#Android project architecture - http://t.co/FrFnNfvpnq'
- id: 35974
  author: Sebastian Greatful
  author_email: sebastianthegreatful@gmail.com
  author_url: ''
  date: '2013-10-14 12:21:02 +0200'
  date_gmt: '2013-10-14 11:21:02 +0200'
  content: ! "I see you have a activity package/folder. Would you place your main
    activity in there as well?\r\n\r\nI usually have several fragment classes with
    a corresponding  activity which does nothing more then add that fragment as it
    sole content. Would you place each in either fragment or activity?"
- id: 35987
  author: Dominik Liebler
  author_email: liebler.dominik@googlemail.com
  author_url: http://thewebdev.de
  date: '2013-10-14 15:23:20 +0200'
  date_gmt: '2013-10-14 14:23:20 +0200'
  content: ! "I would definitely place my Main activity in the activity package, yes.
    I think this should be consistent with all the other activities.\r\n\r\nAnd I
    would place that fragments into the fragment package to make that consistent,
    too. I mean it does not hurt to have them there especially if they do not contain
    much logic in them. \r\n\r\nBut what about adding the fragments as inner classes
    of their corresponding activity if they are that small?"
---
<p>A very important topic when writing Android applications is how to structure your code so that it remains maintainable and extendable while the project grows.</p>
<p>While the <a href="http://developer.android.com/guide/components/index.html">Android SDK documentation</a> will help you with everything you need regarding UI Architecture, there is nothing there to read about software architecture. The following guidelines will help you on your way to a great architecture.</p>
<h2>Folders</h2>
<p>On the very bottom of an architecture is always naming and structuring code into classes and packages. I use the following structure of folders to organize my code:</p>
<pre><code>- com.activeio.&lt;project&gt; # contains only my GlobalState class (Application)
  - activity             # all activities go here
  - fragment             # all fragments
  - database             # Database helper and migration classes
  - entity               # contains entities (simple value objects)
  - service              # services to save and retrieve entities from the database
</code></pre>
<h2>Application class vs. Singletons</h2>
<p>I don't like Singletons (I would even say that this is an anti-pattern) so you already might know my answer to this question. Every Android application I build consists of a custom Application class that acts as a global state object and holds references to e.g. the database layer or adapters that need to be refreshed from the outside (e.g. when data was saved in another activity).</p>
<p>This is what my <code>GlobalState</code>-object looks like in a current project:</p>
<pre lang="java"><code>package com.activeio.&lt;project&gt;;

import android.database.sqlite.SQLiteOpenHelper;
import android.app.Application;
import android.widget.ArrayAdapter;

public class GlobalState extends Application {
    private SQLiteOpenHelper databaseHelper;
    private ArrayAdapter&lt;Word&gt; wordAdapter;

    public void setWordAdapter(ArrayAdapter&lt;Word&gt; wordAdapter) {
        this.wordAdapter = wordAdapter;
    }

    public ArrayAdapter&lt;Word&gt; getWordAdapter() {
        return wordAdapter;
    }

    public void setDatabase(SQLiteOpenHelper database) {
        this.databaseHelper = database;
    }

    public SQLiteOpenHelper getDatabase() {
        return databaseHelper;
    }
}
</code></pre>
<p>As you can see, the application object is just a simple value object with setters and getters for global objects. Register it in you project (<code>AndroidManifest.xml</code>):</p>
<pre lang="xml"><code>&lt;application
        android:name="GlobalState"
        ...
        &gt;
    ...
&lt;/application&gt;
</code></pre>
<h2>Missing dependency injection</h2>
<p><img class="aligncenter" title="I find your lack of dependency injection disturbing" alt="I find your lack of dependency injection disturbing" src="http://thewebdev.de/wp-content/uploads/2013/10/i-find-your-lack-of-faith-disturbing.jpg" /></p>
<p>I must say I find the lack of dependency injection in the Android SDK disturbing and it would be a much cleaner way if I could simply inject global objects in activities and other views. I'll have a look into <a href="http://square.github.io/dagger">Dagger</a> soon and write about it here in my blog.</p>
<p>Please tell me how you solved that issue in the comments, I would very appreciate it!</p>
