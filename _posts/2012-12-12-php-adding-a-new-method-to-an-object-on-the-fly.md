---
layout: post
title: "PHP: Adding a new method to an object on the fly"
description: "Meta Programming with PHP"
category: php
tags: [meta programming, oop]
---
{% include JB/setup %}

## PHP Meta Programming

What about adding methods to a object on the fly, if you comes from ruby language or you are familar with this language, you already know what is it... Ruby provides to you a way to get an instancied object and add a additional method to this object.

*OKAY! Stop Ruby*, let's talk about *PHP*

PHP does not provideo one "standard way" to do such a thing, it's also not part of core...

But anyway it does not say that we are not able to do such a thing.

So let's see the code, I'll show two aproaches one using PHP 5.3, and another using PHP 5.4, those examples take advantage of the <a href="http://br1.php.net/manual/en/functions.anonymous.php">anonymous function</a> (closure) added in the PHP 5.3 version, and also takes advantage of the <a href="http://php.net/manual/en/class.closure.php">Closure class</a> and the method <a href="http://php.net/manual/en/closure.bind.php">bind</a> added in the version 5.4

## Adding method in an object in PHP 5.3

<script src="https://gist.github.com/4189729.js">

</script>

### How it works?

It makes usage of the anonymous function and the magic method <a href="http://php.net/manual/en/language.oop5.overloading.php#object.call">__call</a>, the class Meta has the method <code>addMethod</code>, this method is waiting two params, the first, is the method name, the second one the callable anonymous function.

Each time you call a method that original object does not have (it was not declared in the class), the method call look for if you have register a new method with the given name, if yes, it calls your anonymous function, passing as param for this anonymous function the current object, so you are able to access the methods and properties of the class.

It has some limitations, you won't be able to access private methods and properties, but it's possible to handle this using some <code><a href="http://php.net/manual/en/class.reflectionclass.php">ReflectionClass</a></code>.

## Adding method in an object in PHP 5.4

<script src="https://gist.github.com/4264062.js">

</script>

As you can see the second example make usage of <a href="http://php.net/manual/en/language.oop5.traits.php">traits</a>, another new feature of PHP 5.4, this way we enable horizontal composition, that is always a good idea, decouple more your code.

The traits, it's quite similar with the class Meta.php of PHP 5.3, also the usage of the object, the difference here is that when you are adding the method your anonymous function no longer need to receive the object instance as parameter, as you can see in the test example, and you are able to access directly <code>$this</code> to reference the object methods, and properties, that is just possible because the <a href="http://php.net/manual/en/closure.bind.php">Closure::bind</a>, with this in hand we are able to inject the object and scope inside the anonymous function that was passed to add as a method, so once you call the method and it was created on the fly we call the closure that was stored in memory when you added the method and this closure is in the same scope of the instance, so now we are able to access private properties, protected, etc... and It also looks a bit better as we did not need to force the first parameter be the instance object.


## What hell I'd use it?

This kind of pratice of add methods on the fly, gives some flexibility to you when you are thinking to create something more generic, or create a nice interface to your code API, but it's important to take care when use it, probably bad programmers can do really crazy stuffs with something like this.