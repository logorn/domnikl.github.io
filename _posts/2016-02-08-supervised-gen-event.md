---
layout: post
title: Supervised GenEvent in Elixir
---
Lately I was playing around with [GenEvent](http://elixir-lang.org/docs/v1.2/elixir/GenEvent.html) in Elixir. To getting into the concept of it, I built a simple Logger, that would listen for events and log the message from the event to the console:

{% highlight elixir %}
defmodule LoggerHandler do
  use GenEvent
  require Logger

  def handle_event({:log, x}, messages) do
    Logger.info(x)
    {:ok, [x|messages]}
  end
end
{% endhighlight %}

I opened `iex` and tested my code:

![iex session](/images/supervised-gen-event-iex-session.gif)


{% highlight elixir %}
iex -S mix
{:ok, pid} = GenEvent.start_link([])
GenEvent.add_mon_handler(pid, LoggerHandler, [])
GenEvent.notify(pid, {:log, "It works!"})
GenEvent.notify(pid, %{log: "That won't work!"})
{% endhighlight %}

As you can see, the `%{log: "That won't work!"}` crashes the LoggerHandler as there is no code to handle this event; pattern matching for `{:log, x}` fails. The handler is then down when I call `GenEvent.notify(pid, {:log, "It works!"})` again.

So how do we ensure that the GenEvent gets restarted when an error occurs? I searched some time for it and had a look at the `Logger.Watcher` from the [Elixir repo](https://github.com/elixir-lang/elixir/blob/master/lib/logger/lib/logger/watcher.ex) which does basically the same. I also found a very basic solution in Rodney Norris' blog post ["Event handling in Elixir"](http://www.tattdcodemonkey.com/blog/2015/4/24/event-handling-in-elixir).

To sum it all up: a GenServer can be supervised, so it is the best solution to ensure that an Event handler is up and running even if it fails to handle an event. This is a simple example how one could implement it:

{% highlight elixir %}
defmodule LoggerHandlerWatcher do
  use GenServer

  @doc """
    starts the GenServer, this should be done by a Supervisor to ensure
    restarts if it itself goes down
  """
  def start_link(logger_pid) do
    GenServer.start_link(__MODULE__, logger_pid)
  end

  @doc """
    inits the GenServer by starting a new handler
  """
  def init(logger_pid) do
    start_handler(logger_pid)
  end

  @doc """
    handles EXIT messages from the GenEvent handler and restarts it
  """
  def handle_info({:gen_event_EXIT, _handler, _reason}, logger_pid) do
    {:ok, logger_pid} = start_handler(logger_pid)
    {:noreply, logger_pid}
  end

  @doc """
    starts a new handler listening for events on `logger_pid`
  """
  defp start_handler(logger_pid) do
    case GenEvent.add_mon_handler(logger_pid, LoggerHandler, []) do
     :ok ->
       {:ok, logger_pid}
     {:error, reason}  ->
       {:stop, reason}
    end
  end
end
{% endhighlight %}

Now to sum things up, this is what happens with the restartable GenEvent LoggerHandler:

{% highlight elixir %}
iex -S mix
{:ok, logger_pid} = GenEvent.start_link([])
{:ok, _} = LoggerHandlerWatcher.start_link(logger_pid)
GenEvent.notify(logger_pid, {:log,  "message"})
GenEvent.notify(logger_pid, %{log: "message"}) # this will fail again
GenEvent.notify(logger_pid, {:log,  "message"}) # this will log again into the restarted handler
{% endhighlight%}

The implementation shown above will need some more fine-tuning and testing (what if the handler fails to start?), but I hope I made my point clear: GenEvent is a great implementation for everything that behaves like real events but supervising it is important and can be done with the help of a GenServer implementation that watches the GenEvent.
