---
layout: post
title: Implementing GenServer in Elixir
---
I haven't for a long time, but the last few weeks I have been doing some Elixir again. I am still in love with it, although there is still a lot to learn for me. I had some trouble getting into the functional mindset in the past but as I picked up my copy of ["Programming Elixir"](https://pragprog.com/book/elixir/programming-elixir) again, this wasn't a problem at all.

Instead I had some trouble getting on with GenServer this time. My questions were very basic: When to use it? When to use Agents or Tasks instead? Where to put client vs. server code?

Let's first take a look at the alternatives:

## Agents

> Agents are a simple abstraction around state.

Source: [http://elixir-lang.org/docs/v1.2/elixir/Agent.html](http://elixir-lang.org/docs/v1.2/elixir/Agent.html)

That should already be enough for an explanation. Basically agents never do much stuff, they just store state to be shared and leave complex calculations to Tasks or GenServers.

## Tasks

> Conveniences for spawning and awaiting tasks.
> 
> Tasks are processes meant to execute one particular action throughout their life-cycle, often with little or no communication with other processes. The most common use case for tasks is to convert sequential code into concurrent code by computing a value asynchronously

Source: [http://elixir-lang.org/docs/v1.2/elixir/Task.html](http://elixir-lang.org/docs/v1.2/elixir/Task.html)

So Tasks are very lightweight in implementation but do not support storing a state. 

## GenServer

> A behaviour module for implementing the server of a client-server relation.

> A GenServer is a process like any other Elixir process and it can be used to keep state, execute code asynchronously and so on. The advantage of using a generic server process (GenServer) implemented using this module is that it will have a standard set of interface functions and include functionality for tracing and error reporting. It will also fit into a supervision tree.

Source: [http://elixir-lang.org/docs/v1.2/elixir/GenServer.html](http://elixir-lang.org/docs/v1.2/elixir/GenServer.html)

GenServer is the most complex implementation of the three alternatives described here but is also the most flexible. It is convenient to implement both _client and server code in the same module_ to keep it all in one place. GenServers can also work easily with a Supervisor, which will start/restart the GenServer.

## Conclusion

TL;DR: If you are not shure whether your implementation needs to store state, begin with GenServer as it the most flexible solution. Later on you can decide to use tasks (no state) or agents instead.
