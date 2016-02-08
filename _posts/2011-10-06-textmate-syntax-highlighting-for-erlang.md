---
layout: post
title: ! 'TextMate: syntax highlighting for Erlang'
---
I've been learning a little Erlang in the last few weeks and sometimes I use my Macbook to write some small functions, libs and so on. But it seems that TextMate hasn't build-in support for Erlang, so all my pretty code was just black :-(

But that isn't that big a problem: I found a [bundle for Erlang on github](https://github.com/textmate/erlang.tmbundle) (man I love this site, makes finding those nice pieces of code even simpler) and added it. So you just have to do:

```
mkdir -p /Library/Application Support/TextMate/Bundles
```

then `cd` to this directory and clone the repo in there:

```bash
git clone https://github.com/textmate/erlang.tmbundle.git
```

Now when you restart TextMate and open a .erl file everything will be fine!
