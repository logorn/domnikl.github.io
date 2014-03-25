---
layout: post
status: publish
published: true
title: advanced sprintf() for PHP
author: Dominik Liebler
author_login: domnikl
author_email: liebler.dominik@googlemail.com
wordpress_id: 201
wordpress_url: http://thewebdev.de/?p=201
date: '2011-10-12 13:45:48 +0200'
date_gmt: '2011-10-12 12:45:48 +0200'
categories:
- Uncategorized
tags:
- php
- programming
- function
- sprintf
comments:
- id: 161
  author: Phil
  author_email: philippe@bigwhoop.ch
  author_url: http://bigwhoop.ch
  date: '2011-10-12 20:47:18 +0200'
  date_gmt: '2011-10-12 19:47:18 +0200'
  content: ! 'Or: Build your $params array in the first step and then use http://php.net/manual/en/function.vsprintf.php
    :)'
- id: 162
  author: domnikl
  author_email: dominik@liebler-web.de
  author_url: ''
  date: '2011-10-12 20:57:54 +0200'
  date_gmt: '2011-10-12 19:57:54 +0200'
  content: ! "Good hint and I had a first version of this article with a big disclaimer
    in it that one also could use vsprintf() ;). In my particular case I had to evaluate
    XPath expressions defined by the user and fill a string with the results (format
    also defined by the user), and it's possible that the user defines more or less
    placeholders in the format string than XPath expressions. Then vsprintf() would
    also raise a warning and the format would be empty afterwards.\r\n\r\nI guess
    in most cases you are right and vsprintf() fits perfectly. :)"
- id: 191
  author: John Doe
  author_email: mail@example.com
  author_url: ''
  date: '2011-10-27 11:14:24 +0200'
  date_gmt: '2011-10-27 10:14:24 +0200'
  content: ! "Alternatively, you could use the ugly solution and double the amount
    of percentage signs for each additional parameter, alike so:\r\n\r\n$foobar =
    array('foo', 'bar', 'baz');\r\n$format = '%s%%s%%%%s';\r\nforeach ($foobar as
    $f) {\r\n    $format = sprintf($format, $f);\r\n}"
---
<p>Have you ever had the need to use sprintf in a loop and replace the placeholders sequentially loop cycle by loop cycle? I recently had but there is a big problem in this use case: sprintf() (or the printf() family in general) can't do this. PHP will raise a warning "Too few arguments" when there's two placeholders in the format string, but only one additional parameter has been given to it.</p>
<p>Consider the following example:</p>
<p>[code lang="php"]<br />
$foobar = array('foo', 'bar');</p>
<p>$format = '%s%s';<br />
foreach ($foobar as $f) {<br />
    $format = sprintf($format, $f);<br />
}</p>
<p>echo $format;<br />
[/code]</p>
<p><strong>This won't work!</strong> So what I did was defining a new function asprintf() that could deal with too few arguments, replacing just the first placeholder when a scalar type was given. If you give it an array, it will call itself recursively extracting the first element and replace the placeholder with it.</p>
<p>Here's how it looks:</p>
<p>[code lang="php"]<br />
&lt;?php<br />
/**<br />
 * advanced sprintf() - doesn't complain about too few arguments<br />
 *<br />
 * @param string $format<br />
 * @param array|mixed $data<br />
 * @return string<br />
 */<br />
function asprintf($format, $data = array())<br />
{<br />
    $matches = array();<br />
    $regEx = '/\%[0-9\.]{0,}[b|c|d|e|E|u|f|F|g|G|s|x|X]/';</p>
<p>    if (preg_match($regEx, $format, $matches) &amp;&amp; 0 !== count($data)) {<br />
        $dataElement = is_array($data) ? array_shift($data) : $data;</p>
<p>        // replace the placeholder using sprintf<br />
        $format = preg_replace(<br />
            $regEx,<br />
            sprintf($matches[0], $dataElement),<br />
            $format,<br />
            1<br />
        );</p>
<p>        if (is_array($data)) {<br />
            return asprintf($format, $data);<br />
        } else {<br />
            return $format;<br />
        }<br />
    } else {<br />
        return $format;<br />
    }<br />
}<br />
[/code]</p>
<p>I also created a <a href="https://gist.github.com/1277874" target="_blank">gist on github</a> for it, so you can fork it and do whatever you like with it ;)</p>
