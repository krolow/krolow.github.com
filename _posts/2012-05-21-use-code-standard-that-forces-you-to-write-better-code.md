---
layout: post
title: "Use Code Standard that forces you to write better code"
description: "How get advantage of a code standard that forces you to write a better code."
category: php 
tags: [code standard    ]
---
{% include JB/setup %}

It's been about 4 months that our backend team, has choice one code standard, for our PHP projects, before this time each programmer has written code in his own style, some of them with a similar approach, other with a totally different style...

So in our internal group, we have decided that it's time to write code in the same way.

# The Code Standard PHP Options

The first challenge was to decide how and why we will use one code standard, our main framework is <a href="http://cakephp.org">CakePHP</a> and CakePHP has <a href="http://book.cakephp.org/2.0/en/contributing/cakephp-coding-conventions.html">his own code</a> standard, it's a flexible code standard with not so much definitions, for me it looked like the good one, because it was the code standard that I was used to written my own code... so the changes wouldn't be so much for me. I just have to keep in mind some of the specifications that I was not using...

Anyway as we are a team, the best option is decide this as a team, so one of the guys of our team received the task to get all the most used code standards of PHP world over the web and list all of them and present for us, after that we would decide in one meeting what code standard to be used.

So we scheduled this meeting with all team, to start decide what code standard we would use, in this list we had these options:

* CakePHP <a href="http://book.cakephp.org/2.0/en/contributing/cakephp-coding-conventions.html">link</a>
* Zend <a href="http://framework.zend.com/manual/en/coding-standard.coding-style.html">link</a>
* Pear <a href="http://pear.php.net/manual/en/coding-standards.php">link</a>
* Symphony <a href="http://trac.symfony-project.org/wiki/HowToContributeToSymfony#CodingStandards">link</a>
* Facebook (Phabricator) <a href="http://www.phabricator.com/docs/phabricator/article/PHP_Coding_Standards.html">link</a>

So we check one by one of code standard at home before, to get prepared to not waste time in this meeting, so some of the person of team already had their own opinion, but in this meeting we opened one code standard each time, to check how is the documentation and how is the style...

###CakePHP

Like I have mentioned, it is the code standard that most of the guys were used, but we checking this code standard, we could see that is so much flexible, there is no so much definitions, it's totally different of some other style of other frameworks/code standard... So we concluded that even CakePHP is the our most widely used framework it not force us to write code in the same way, the code standard is flexible in the point of each one still write code in different styles... And it is possible to check inside the community, there is no standard between the plugins, components, helpers, each developers write the code in the way that he wants, and for sure that it's not good...

###Zend

So we have checked Zend code standard, that was a really good check very well written and good documented, it has not so much flexibility so we as a team would be forced to code similar, and in the same way have some features that we believe that are good, as the flexibly limit of columns line, and so on...

So we put this as our first option as the time...

###Pear

We checked the pear, and this one looks similar Zend, but this one force you so much more, all methods should be documented, variables assigned should be aligned, all class files should have phpDocument block to describe the class, the file... and so on...

It also has be marked in our list as a good code standard, and so we put it with Zend to be checked

###Symphony

We have just looked it, and because the poor documentation, and lack of definitions we did not like that so much, we have agree that for example instead of use this one we could use the CakePHP one as the fact that is the framework that we use more often...

###Facebook

Another one that we just have looked, it has also a poor documentation, just few definitions...


##How decide the code standard

So we have choose 2 of them *Zend* and *Pear*, and we have the third option that is *CakePHP*.

###First Option
Our first point was that CakePHP is the more often framework used, but it is not the only one, and the fact that brackets for methods in CakePHP normally are different of other frameworks/CMS it probably would impact in the way that we would write code in other frameworks, and also the habits would come back because the code standard has a lack of definitions, so the programmer would be free several times to write his own style...

###The second option

So we checked Zend and everyone in the team has agree with Zend code standard, there are a good documentation and it also forces a lot of code style and everything is well documented, so if a new person join the team it will be simple to this person learn the code style to be used...

We tried compare to Pear, but we have decided to Zend...

So after this meeting it was time to configure all machines with the <a href="http://pear.php.net/package/PHP_CodeSniffer/redirected">phpcs</a>, that is analytics tool that check your code to see if in somewhere it violates the code standard, so checking this tool we have noticed that CakePHP violates a lot the Zend code standard...

But anyway as we don't use just CakePHP, it would be better to have the Lib of CakePHP with a different code style, that our own APP with the different one. So we have decided to keep this anyway... When we started use the code standard in our App, we have noticed a new one problem, CakePHP uses method name with the first letter in caps, and Zend does not allow this... so we have to write our own code standard, we have just forked the Zend code standard and adapt that one to allow the attributes name with first letter in caps...

So was this we were using one code standard, in the meanwhile one of the guys of the team have tested the Pear code standard, with the phpcs tool, and Pear was so much more complete of definitions than Zend that he decided to write by his own the adaption of Pear for CakePHP, and the good point of this if you write your code in Pear, probably it pass in the Zend code standard, but it also gives to you so much more definitions and force to you document your code...

The team has seem this with good eyes, and slowly started adapt Pear as the code standard...

### Advantages of a code standard that forces you

So I could quickly check some advantages in write code in a code standard that forces you:

* You pay more attention in your code, gives the fact that you should keep in mind the code standard;
* You refactor more often your code, as you need to comment each method, it forces you always to split in more than one method your logic, otherwise it's really hard describe what each method does in your application;
* You feel uncomfortable to write bad code or workarounds, as the fact that you spent more time to put everything into the code standard and put the documentation, you feel really bad when you see a bad code, and normally you will avoid this;
* You start write vertical code, using 80 columns as a standard, you force to write vertical code, so you normally reduce the number of lines in your method otherwise you will need scroll to check what all the method does;
* You will see that other people that work in the same project that you also started code better, they feel uncomfortable to broke the standard, and the quality of code;


As you can see one code standard force to you a lot and you receive back a lot of benefices:

* better code quality
* well documented code
* normally it implies in a more decouple code;
* normally it implies in a more readable code...

And there a lot of other benefices...

To summarize, I think you have to always choose the code standard that fits better for your team, it must involved all the team in the choice and it's normally some of the persons avoid to use this new code standard, but it is one thing that we have to face it but in general you will be able to see soon several improves in the code quality of your team.

Code that forces the programmer are good, and you must always use tools that automatic your process of check like the phpcs, it's possible to configure the ide to use inside with phpcs, like the <a href="http://www.websitefactors.co.uk/php/2011/10/installing-php-codesniffer-properly-in-eclipse/">eclipse</a>, <a href="http://www.amaxus.com/cms-blog/coding-standards-netbeans-php-codesniffer">netbeans</a> or <a href="https://github.com/moacirosa/vim">vim</a>.

For who wants to use Pear code standard in CakePHP you can check this <a href="https://github.com/moacirosa/phpcs-pear-cakephp">repository.</a>

