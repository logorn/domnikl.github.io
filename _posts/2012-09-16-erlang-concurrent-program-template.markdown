---
layout: post
status: publish
published: true
title: Erlang Concurrent Program Template
author: Dominik Liebler
author_email: liebler.dominik@googlemail.com
date: '2012-09-16 07:36:11 +0200'
date_gmt: '2012-09-16 06:36:11 +0200'
---
To start development on a new Erlang module that supports concurrent processing, I wrote myself a template, that is mostly inspired by the template from Joe Armstrong and his book [Programming Erlang - Software for a Concurrent World](http://pragprog.com/book/jaerlang/programming-erlang).


```erlang
-module(ctemplate).
-compile(export_all).
 
%% start
%%
%% @spec start() -> pid()
start() ->
  % explicit MFA (module, function, args list) enables dynamic code upgrades
  spawn(ctemplate, loop, [[]]).
 
%% remote call
%%
%% @spec rpc(pid(), any()) -> any()
rpc(Pid, Request) ->
  Pid ! {self(), Request},
  
  receive
    % Pid is in the pattern match to avoid grabbing messages from all 
    % processes ...
    {Pid, Response} ->
      Response
  end.
 
%% receive loop handler
%%
%% @spec loop(any()) -> none()
loop(X) ->
  receive
    Any ->
      io:format("Received:~p~n", [Any]),
      
      % tail recursion: this should be the last call, 
      % so it won't consume any stack space
      loop(X)
  end.
```
I developed the template from the book a bit further and used *MFA* (Module, Function, Argument List) in the `spawn` call to enable dynamic code upgrades.
In the top you can see, that all functions will be exported (that means, callable from other modules or the shell). This is only for debugging purposes.
As a default, the loop will just print out, what has been received from the client process.

But in most cases, it would be much better to have a look at the OTP behaviours :)
