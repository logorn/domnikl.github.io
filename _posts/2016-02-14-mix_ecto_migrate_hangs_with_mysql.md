---
layout: post
title: "mix ecto.migrate hangs with MySQL and runs forever"
---
Recently I began learning the [Phoenix web framework](http://www.phoenixframework.org/) for Elixir. I explored controllers, views and templates. Then I came to use Ecto and migrations. I am a long-time user of MySQL, so I created a MySQL database using `mix ecto.create` and it just worked. After adding a migration I ran `mix ecto.migrate` to setup the new table.

Currently there is a bug in MySQL and it will never create anything except the `schema_migrations` table but will run forever and do nothing instead. I found an issue in the Ecto Github repo for it [here](https://github.com/elixir-lang/ecto/issues/1130).

The solution is to change the `mariadb` dependency in `mix.exs`:

{% highlight elixir %}
defp deps do
  [
    {:phoenix, "~> 1.1.4"},
    # old
    {:mariaex, ">= 0.0.0"},
    # new
    {:mariaex, "~> 0.6.1", override: true},
    {:phoenix_ecto, "~> 2.0"},
    {:phoenix_html, "~> 2.4"},
    {:phoenix_live_reload, "~> 1.0", only: :dev},
    {:gettext, "~> 0.9"},
    {:cowboy, "~> 1.0"}
  ]
end
{% endhighlight %}
