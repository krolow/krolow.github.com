---
layout: post
title: "PHP static analysis tools: PHP Code Standard the phpcs"
description: "A serie of PHP static analysis tool that will supports you in your daily work, in this post about a tool that check your code standard phpcs"
category: php
tags: [static analysis tool, code standard]
---
{% include JB/setup %}

I'd like to start a series of posts about PHP static analysis tool that will help you in your daily work, these tools will give you a better feeling of how your code is going, where you should improve and also it will keep you in constantly refactor/improvement in your code. To start this serie I chose the phpcs.

## PHP Code Standard: phpcs

I've written a post about code standard that forces you to write better code, and in this post I have mentioned a tool to make it possible, this tool is the <a href="http://pear.php.net/package/PHP_CodeSniffer/">PHP_Codesniffer, PHP Code Sniffer or phpcs</a>.

### What is a code standard sniffer?

Code standard sniffer is a tool that inspects into your source code looking for something that violates the PHP code standard that you have defined.

The idea is if you or/and your team uses a code standard to write your PHP code, the phpcs will be responsible to check if all the source code created keeps the usage of code standard that you have defined.

### How to install it?

PHP_Codestandar (phpcs), it's a pear package, so it's quite easy to install this static analysis tool. Assuming that you have the pear installed in your machine (case not <a href="http://pear.php.net/manual/en/installation.php">check here</a>), you should just write this in your console:

<pre>
    pear install PHP_CodeSniffer
</pre>

In case that you don't want to install pear, you are able to clone the project from github:

<pre>
    git clone git://github.com/squizlabs/PHP_CodeSniffer.git
    cd PHP_CodeSniffer
    php scripts/phpcs -h
</pre>

### How to use it?

Once you have it installed you are able to start making use of it, phpcs already comes with some options of code standards, and <a href="http://pear.php.net/manual/en/standards.php">PEAR</a> is the code standard used as default.

So you are already able to check code standard:

####Check a single file:

<pre>
    phpcs …/Lib/Gingo/Config.php
    
    FILE: …/Lib/Gingo/Config.php
    ----------------------------------------------------
    FOUND 37 ERROR(S) AFFECTING 19 LINE(S)
    ----------------------------------------------------
      2 | ERROR | Missing file doc comment
      4 | ERROR | Missing class doc comment
      4 | ERROR | Opening brace of a class must be on the line after the definition
      5 | ERROR | Spaces must be used to indent lines; tabs are not allowed
underscore
    ...
</pre>

####Check a folder:

<pre>
    phpcs checker/

    FILE: /path/checker/check.php
    ----------------------------------------------------
    FOUND 5 ERROR(S) AND 1 WARNING(S) AFFECTING 4 LINE(S)
    ----------------------------------------------------
      2 | ERROR   | Missing file doc comment
      2 | ERROR   | Missing class doc comment
      5 | ERROR   | Missing function doc comment
      5 | ERROR   | Private method name "Check::testingThisMethod" must be prefixed
        |         | with an underscore
     11 | ERROR   | Missing function doc comment
     13 | WARNING | Line exceeds 85 characters; contains 102 characters
    ----------------------------------------------------

    FILE: /path/checker/code.php
    ----------------------------------------------------
    FOUND 5 ERROR(S) AFFECTING 3 LINE(S)
    ----------------------------------------------------
     2 | ERROR | Missing file doc comment
     2 | ERROR | Missing class doc comment
     5 | ERROR | Class constants must be uppercase; expected TEST but found test
     7 | ERROR | Missing function doc comment
     7 | ERROR | Opening brace should be on a new line
     ----------------------------------------------------

    Time: 0 seconds, Memory: 4.75Mb
</pre>

####You are also able to get a summary:

<pre>
    
    phpcs -n --report=summary …/

    PHP CODE SNIFFER REPORT SUMMARY
    --------------------------------------------------------
    FILE                                    ERRORS  WARNINGS
    --------------------------------------------------------
    …/config/config.php                             3       0
    …/Development/webroot/css/style.css             5       0
    …/Development/webroot/index.php                 24      0
    …/Lib/Gingo/Config.php                          37      0
    …/Lib/Gingo/Exception/FileDoesNotExists.php     18      0
    …/Lib/Gingo/Exception/GingoException.php        16      0
    …/Lib/Gingo/Gingo.php                           35      0
    …/Lib/Gingo/Net/Cache.php                       106     0
    …/Lib/Gingo/Net/Handle.php                      3       0
    …/Lib/Gingo/Net/HandleCollection.php            1       0
    ...
    --------------------------------------------------------
    A TOTAL OF 1838 ERROR(S) AND 0 WARNING(S) WERE FOUND IN 27 FILE(S)
    --------------------------------------------------------

    Time: 1 second, Memory: 10.25Mb
</pre>

####You are able to choose a different standard:

<pre>
    phpcs checker/ --standard=Zend

    FILE: /path/checker/check.php
    ----------------------------------------------------
    FOUND 0 ERROR(S) AND 1 WARNING(S) AFFECTING 1 LINE(S)
    ----------------------------------------------------
     13 | WARNING | Line exceeds 80 characters; contains 102 characters
    ----------------------------------------------------

    FILE: /path/checker/code.php
    ----------------------------------------------------
    FOUND 1 ERROR(S) AFFECTING 1 LINE(S)
    ----------------------------------------------------
     7 | ERROR | Opening brace should be on a new line
    ----------------------------------------------------

    Time: 0 seconds, Memory: 3.50Mb    
</pre>

*List code standard installed:*

<pre>
    phpcs -i
    The installed coding standards are MySource, PEAR, PHPCS, Squiz and Zend
</pre>

####There are other several options:
    
*Restrict extensions:*

<pre>
    phpcs /path/Project --extensions=php
</pre>

*Ignore folders/files:*

<pre>
    phpcs /path/Project --ignore=*/tests/*,file.php
</pre>

*Replace tabs with spaces:*
<pre>
    phpcs --tab-width=4 /path/Project/
</pre>

And still having several other options that you can check in the <a href="http://pear.php.net/manual/en/package.php.php-codesniffer.advanced-usage.php">PHP Code Standard documentation</a>, I have just summarized up here the most used commands…

#### Write your own code standard

You are also able to write your own Code Standard definition as described <a href="http://pear.php.net/manual/en/package.php.php-codesniffer.coding-standard-tutorial.php">here</a>.

#### Automatize the checking process

You are also able to put phpcs to run with a Continous Integration such as Jenkins, and also set hook for your version control, for example <a href="http://pear.php.net/manual/en/package.php.php-codesniffer.svn-pre-commit.php">svn</a> and <a href="https://github.com/s0enke/git-hooks/tree/master/phpcs-pre-commit">git</a>.

#### To conclude

phpcs is a great tool to check if your team are keeping the usage of the code standard, it is also flexible enough for you to define your own code standard, and it is also possible to define automatic process to check that everyone is using the code standard, so do not hesitate to use this great tool, and as I have <a href="http://cobaia.net/php/2012/05/21/use-code-standard-that-forces-you-to-write-better-code/">posted before</a>, take advantage of a code standard that forces you write better code.

    
