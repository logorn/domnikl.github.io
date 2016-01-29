---
layout: post
status: publish
published: true
title: Running make in parallel
author: Dominik Liebler
date: '2014-06-12 08:00:00 +0100'
---
I bet you all heard about make before, the wonderfully simple but versatile build tool that origins from the age of dinosaurs and that has been an inspiration for almost any other build tool out there like ant, grunt, you name it.

But it was just recently and by accident, that I got to know that you can run multiple build tasks in parallel!

Suppose you have the following Makefile:

```make
default: build logs

build: *.go
	GOPATH=$(PWD) go build

logs:
	touch log/production.log
```

As you can get, the two tasks `build` and `log` are not dependent on each other, so why not run these in parallel? The `-j2` flag tells make to use two jobs, the default is therefor `-j1`.

```bash
make -j2 build logs
```

With a little rewrite of the Makefile you can make this the default:

```make
default:
	make -j2 build logs

...
```
