---
layout: post
title: Android project architecture
---
A very important topic when writing Android applications is how to structure your code so that it remains maintainable and extendable while the project grows.

While the [Android SDK documentation](http://developer.android.com/guide/components/index.html) will help you with everything you need regarding UI Architecture, there is nothing there to read about software architecture. The following guidelines will help you on your way to a great architecture.

## Folders

On the very bottom of an architecture is always naming and structuring code into classes and packages. I use the following structure of folders to organize my code:

```
- com.activeio.<project> # contains only my GlobalState class (Application)
  - activity             # all activities go here
  - fragment             # all fragments
  - database             # Database helper and migration classes
  - entity               # contains entities (simple value objects)
  - service              # services to save and retrieve entities from the database
```

## Application class vs. Singletons

I don't like Singletons (I would even say that this is an anti-pattern) so you already might know my answer to this question. Every Android application I build consists of a custom Application class that acts as a global state object and holds references to e.g. the database layer or adapters that need to be refreshed from the outside (e.g. when data was saved in another activity).

This is what my `GlobalState`-object looks like in a current project:

```java
package com.activeio.<project>;

import android.database.sqlite.SQLiteOpenHelper;
import android.app.Application;
import android.widget.ArrayAdapter;

public class GlobalState extends Application {
    private SQLiteOpenHelper databaseHelper;
    private ArrayAdapter<Word> wordAdapter;

    public void setWordAdapter(ArrayAdapter<Word> wordAdapter) {
        this.wordAdapter = wordAdapter;
    }

    public ArrayAdapter<Word> getWordAdapter() {
        return wordAdapter;
    }

    public void setDatabase(SQLiteOpenHelper database) {
        this.databaseHelper = database;
    }

    public SQLiteOpenHelper getDatabase() {
        return databaseHelper;
    }
}
```

As you can see, the application object is just a simple value object with setters and getters for global objects. Register it in you project (`AndroidManifest.xml`):

```
<application
        android:name="GlobalState"
        ...
        >
    ...
</application>
```

## Missing dependency injection

![I find your lack of dependency injection disturbing](/images/i-find-your-lack-of-faith-disturbing.jpg "I find your lack of dependency injection disturbing")

I must say I find the lack of dependency injection in the Android SDK disturbing and it would be a much cleaner way if I could simply inject global objects in activities and other views. I'll have a look into [Dagger](http://square.github.io/dagger) soon and write about it here in my blog.

Please tell me how you solved that issue in the comments, I would very appreciate it!
