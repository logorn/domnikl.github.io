---
layout: post
title: type-safe collections in PHP
---
Yes, you've read the headline correctly, although PHP is a weakly-typed language, sometimes you just need to make sure, that an argument to a method is of a certain type. As of PHP 5.3 you can use type-hinting to ensure this situation.

Image you were implementing a simple blog system. Every post can have a collection of comments associated to it and you don't want to have trackbacks in this collection. And the list of comments should be distinct. You don't want that spam comment over and over again in this list.

PHP already provides a type for this task in the SPL: SplObjectStorage is the best way to storage a list of unique objects that can be iterated over and provides array-like access. Here's a basic example:


```php
<?php

class Post
{
	/**
	 * @var SplObjectStorage
	 */
	protected $comments;
	
	public function __construct()
	{
		$this->comments = new SplObjectStorage();
	}
	
	/**
	 * adds a new comment
	 *
	 * @param Comment $comment
	 * 
	 * @return void
	 */
	public function addComment(Comment $comment)
	{
		$this->comments->attach($comment);
	}
	
        /**
         * get all comments for this post
         *
         * @return SplObjectStorage
         */
	public function getComments()
	{
	        return $this->comments;
	}
}
```
