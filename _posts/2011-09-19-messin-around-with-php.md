---
layout: post
title: messin' around with PHP
---
When you're using PHP you might know that there are a few boundaries when it comes to variable names. Every language has a set of rules for this and the interpreter simply needs them to determine if the actual token is a variable name or not. For PHP, there are few rules: the name must start with a dollar sign ($) followed by either a underscore (_) or a letter a-z (or, of course A-Z), followed by letters, numbers and underscores.

However it is possible to use whatever you want, even whitespace chars! Just consider the following example:

```php
${'1 foo bar'} = 'baz';
echo ${'1 foo bar'}; // will output: baz
```

As you can see, the rules don't apply to variable variables. Now that you know this I have a final advice for you. *Don't ever use this in production code!* It's hard to read, hard to understand and not maintainable! It's good to know one can do this using PHP, but there are always better ways to solve problems than this way.
