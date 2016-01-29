---
layout: post
status: publish
published: true
title: combining Subversion and git for great good!
author: Dominik Liebler
author_email: liebler.dominik@googlemail.com
date: '2011-10-10 12:00:34 +0200'
date_gmt: '2011-10-10 11:00:34 +0200'
---
Sometimes in a project you want to save a state of your code but don't want to commit it because things are broken and you're not sure if it's the right way you are going. Let's say you want to refactor a very large code base. Your team is using a Subversion server and you don't want to commit your single steps in refactoring.

This recently happened to me and I decided to use git while doing the refactoring. Just go to your project dir, git init a new git repo, create a `.gitignore` file and add those lines:

```
.gitignore
**/.svn/
.svn/
```

All `.svn` folders will now be ignored on git commits. Then commit your first step of the refactoring, change some more code and you can easily go back to every step. When you've finished, just commit the last step to the svn repository and delete your git repo (`rm -R .git .gitignore`). You might not want to commit your .gitignore file to the Subversion repository, so setting the `svn:ignore` keyword on it will be a good idea.

Done! :)
