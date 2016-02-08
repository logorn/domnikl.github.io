---
layout: post
title: Having fun with Elixir's macros
---
I already wrote about Elixir [last October](/meet-elixir/). For those who haven't followed my blog since then, here's the short story for you: Elixir is a functional programming language that is built upon the Erlang VM and also supports metaprogramming.

The core language is built heavily on macros which enables some nice syntactic sugar on the language level and supports building nice [domain-specific languages](/think-of-apis-as-domain-specific-languages-dsl/). A often seen example of this is also a very simple example. The ExUnit framework provides a simple `test` macro that let's you write tests like this:

```elixir
test "the truth" do
  assert(true)
end
```

You can also basically inspect all expressions and constructs with the `quote do ... end` construct. Just start Elixir's interactive tool `iex` and play around with it:

```elixir
iex(5)> quote do
...(5)> 9 - 8 * 3 + 34
...(5)> end
{:+, [context: Elixir, import: Kernel],
 [{:-, [context: Elixir, import: Kernel],
   [9, {:*, [context: Elixir, import: Kernel], [8, 3]}]}, 34]}
```

It's those little things that I love Elixir for. Everything seems so well designed on it and although it's a young language, there's already so much features in it.

If you are interested, Chris McCord has a nice presentation about macros in Elixir [over there](http://chrismccord.com/blog/2014/03/13/write-less-do-more-and-have-fun-with-elixir-macros/). Enjoy!
