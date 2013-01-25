---
layout: post
title: "Some tips to improve your codes readability"
description: "Code readability it's one of the mostimportant part of the code, there are some tips to help you improve your code readability"
category: php
tags: [code readability]
---
{% include JB/setup %}

What about code readability, from my point of view is one of the most important thing in the code. Who writes code that is easy to read, writes good code.
Probably reading code is where you spent most part of your time, and not only **your** code, probably code of your team mates, or maybe code from the open source community, so write code that is simple and is easy to understand it's really important.

## How write code that is easily to read?

Well, it's not that simple, but there are some tips, that you can follow, I'll try summarize some of these tips, to help you to write better code, and increase the code redability of your code.

### Tip 0: Comment before write your code (DocBlock)

What? Before?? YES! let me say why...

When you came with the idea that is needed a new method or a new class, we normally starts create the code for this class/method, but probably the main idea of what your method or class will do, you already have in mind, so why not describe in a comment what the method/class will do, before you start write real code.

#### Some of advatanges that you will get putting this in pratice:

- You will be avoinding that your method or class do more that it is suppose to do
- You will always have a clue of what is wanted in this method or class
- You will decouple more your code, because if something else is needed in your method or class to do, you will be able to create another method to handle

### Tip 1: Return frequently, Return early

This tip is quite simple and help a lot increase the readability.

#### What does it means? 

It means that always when possible, you will be returning something from your method.

#### Some of advantages that you will get putting this in pratice:

- You will be avoiding the use of the conditional "else"
- You will be writing methods that does not have so much logic
- You will be forced to split the code into minor parts
- You will be avoiding the quantity of blocks identantions in your code

#### Example

<script src="https://gist.github.com/95607d5da660610bceb1.js?file=return.php"></script>

<script src="https://gist.github.com/95607d5da660610bceb1.js?file=return1.php"></script>

### Tip 2: Break, Continue 

Loop, we <a href="http://www.youtube.com/watch?v=Pb6GdFr-0bE">love repetitions</a>, but a good tip is leave early from a loop.

To do such a thing we have the <code>break</code> and <code>continue</code>, so always that is possible try to use these commands, these commands will help avoid the usage of the else condition, and it will also help you split into other pieces your code... You will be able to delegate code for other methods. Your code maybe will be also fast, as the fact that probably it won't be needed to pass all the block of the loop, it will leave the block early.

<script src="https://gist.github.com/95607d5da660610bceb1.js?file=loop1.php"></script>

We can do:

<script src="https://gist.github.com/95607d5da660610bceb1.js?file=loop2.php"></script>

<script src="https://gist.github.com/95607d5da660610bceb1.js?file=loop3.php"></script>

### Tip 3: Code Standard / Name conventions

Use code standard, follow rules in all your project, it does not matter what code standard you will pick, but follow the rules. It also applies for the Name Conventions, try follow a name convention, not use abbreviations, pick good names for your variables and methods.

Define how will be indent the code, define a column limiter, and follow those rules... You can check a bit more about code standard, <a href="http://cobaia.net/php/2012/05/21/use-code-standard-that-forces-you-to-write-better-code/">in my other post</a>.

Try to keep some standards, like set and get, normally when we see set and get in the code, we think that this method will access properties of the class, so try to not use these prefixes, when your method will not just accessing the properties of class, use other more descriptive names.

A good way to think, is read the action. For example:

<script src="https://gist.github.com/95607d5da660610bceb1.js?file=cs.php"></script>

Try read the code... "User get the User 1" sounds strange... so when you are reading the code, you will get a good overview, try approximate as maximum as possible of our natural language.

So for the example, given the example before, we can read as: "User retrive to me user X"

<script src="https://gist.github.com/95607d5da660610bceb1.js?file=cs2.php"></script>

Or

"User get user X"

<script src="https://gist.github.com/95607d5da660610bceb1.js?file=cs1.php"></script>

Try to avoid replicated the name of the instance class, that you are using in the methods, when you have the instance of the class (the object), you will already have the user, so no make sense repeats the user nomenclature a long of the methods...

Other things that you can take care is the prefix/suffix:

<script src="https://gist.github.com/95607d5da660610bceb1.js?file=cs3.php"></script>

Try keep consistence between the methods... if you use has and is, try follow in all other classes that nomenclature and also the kind of data that it will return.

### Tip 4: Throw Exception

Try throw one exception always that it's possible, some advantages of this is that you can stop your code, so if you have a big block of code when you throw the exception, the code will stop there.

Another advantage of Exception, is that you can write in natural language, instead of use boolean, true or false, when you are using one exception you can say exactly what was that happend when the exception was trigged, so when you are reading the code you can quickly identify what happend, and you also gives the possibility to handle that exception in the way that you want to.

<script src="https://gist.github.com/95607d5da660610bceb1.js?file=exception.php"></script>

### Tip 5: Comment often, but not write stupid comments

Comment the code, as mention in the Tip #0, it's good, not only in the Doc Block, but all over your code, it gives for the programmer a good overview of what the follow code will be doing... 

But please, you don't need to comment everything and also you don't need to be stupid.

<script src="https://gist.github.com/95607d5da660610bceb1.js?file=comments.php"></script>

You don't need to write stupid comments, put your comment where is needed! In complex logics, or big blocks of conditionals. But always try to summarize the points, try think in a way that when somebody reads your comment this person will really get a good insight of what will happen in the follow lines.

### Tip 6: Methods can be always smaller than they are

Try always to break into minor pieces your method, decouple your code, reduces the complexibility, delegate logic for other objects, for other methods, it will help a lot in the readability, instead of a complexly block of code you will be able to just ask something for a method... Try to not create magical methods that does everything, each method, each object can do a part of the whole process...

Using this in pratice, it will help to test your code, it will be more simple to guarantee that a specific thing is working, because each method and object will have a properly role, not a super magic one...


## To summarize

Take care of what you are writing, try always to think if another person reads your code if they will understood, try to make consistent code, a consistent API, follow the rules.

And I recommend to read <a href="http://www.bennadel.com/resources/uploads/2012/ObjectCalisthenics.pdf">Object Calisthenics</a>, it will help you write better OOP code, and also code that it's more easy to read.

