---
layout: post
title: "EEx - Templating for Elixir"
published: false
---
tssdfs

{% highlight elixir %}
defmodule Render do
  require EEx

  EEx.function_from_file(:def, :base, "example.eex", [:name])
end
{% endhighlight %}


I am digging deeper and deeper into Elixir and recently I have been using Phoenix to play around with some web apps. Soon I was to deal with EEx, which stands for Evaluated Elixir and is a templating engine for Elixir. It works like Jinja for Python and ERB for Ruby.

EEx has a wonderful feature that is also used in Phoenix where the template is available as a function in the View module. It then gets called with the assigns as a parameter and returns just a binary with the content.

I wondered how this was implemented internally and of course you can invoke it also outside of the framework (and use it as a template for e.g. configruation files):

{% highlight elixir %}
defmacro function_from_file(kind, name, file, args \\ [], options \\ []) do
  quote bind_quoted: binding do
    info = Keyword.merge options, [file: file, line: 1]
    args = Enum.map args, fn arg -> {arg, [line: 1], nil} end
    compiled = EEx.compile_file(file, info)

    @external_resource file
    @file file
    case kind do
      :def  -> def(unquote(name)(unquote_splicing(args)), do: unquote(compiled))
      :defp -> defp(unquote(name)(unquote_splicing(args)), do: unquote(compiled))
    end
  end
end
{% endhighlight %}
Source: [https://github.com/elixir-lang/elixir/blob/master/lib/eex/lib/eex.ex](https://github.com/elixir-lang/elixir/blob/master/lib/eex/lib/eex.ex)

The code behind this makes heavy use of meta programming features in Elixir. There is a `defmacro` that loads and compiles the template and then defines a function for the given name that returns the compiled template as a string.

## Read more

* [Notes on Elixir templating with EEx](http://bordeltabernacle.github.io/2016/02/12/notes-on-elixir-templating-with-eex.html)
* [EEx.function_from_file/5](http://elixir-lang.org/docs/stable/eex/EEx.html#function_from_file/5)