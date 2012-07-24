---
layout: post
title: "Make code that tells about your business logic"
description: ""
category: php
tags: [cakephp, software engineer, software architecture]
---
{% include JB/setup %}

#What about your business logic, where are you written this?

It's quite common when we use frameworks, we try to fetch our business logic of our application inside the framework structure and rules.

###But, the question is all your application have the same needs? 

What about your lastest applications, are all of these application equals, the logic was always the same, the business was the same?

I think no, normally each application has the own needs, the own logic... and probably will not feet in the same structure one of another...

So the question is with frameworks obstructives such as CakePHP, we try to feet all our needs in a same strucutre?

**For example the structure below that CakePHP provide for us:**

<div style="text-align:left;">
<img src="/assets/img/cakephp-tree.png" />
</div>
<span style="clear:both;"><!-- --></span>
    
What this structure tells about your business logic, about your project? It feets all your needs? Where are you written your business logic?

Are you written your logic in your controller? No, controller it's bad! I write my logic in my models!

But your models use the active record, so they are related with database... so you write your logic in database?

And when you need related informations what do you do? You use a lot of differents models in your controller? do you call differents models at differents times at differents controllers to do what you need?

So cool MVC ahmm? You have your model, that works with your database and you write your logic there and you have also your controller that tries to handle everything, handle the request, call models to validate, call models to get data, call models to make the logic and send all the data needed for the view, so the view take care of get dynamic data from the controller, try present it together with your HTML, mustashe, haml, twig... and get it's back and send for the browser...

Uhhhh! Controller you are my super hero!

###So what about your business logic?

The business logic is the principal part of your application, it's what make distinct one application of another, is what make the application exclusive. It is the thing that you really want to take care a long of your development, where you should spend all the time making better, architecturing to attend your needs and your specifications.

Your business logic must be flexible, the business logic probably don't want to know about where comes the input, it just handle the input and deliver some output, your business logic don't want to know if you wanna store your data into your database, our in a flat file, our in a MongoDB, it just handle data, inputs and outputs.

Your business logic don't care if you use CakePHP, Symfony 2, Zend Framework, Koahana or whatever, your business logic it's not about framwork, it's about logic and logic it's not acouple with a framework.

### so how we can handle that?

Well PHP... yes, PHP do your business logic, you should write PHP code, that handles yours input and delivers your inputs, and make your logic happens...

All the frameworks proving a way to you use your library... and that library is where you should have your business logic...

You will have the freedom to organize and handle your code in the way that you want, not with a predefined structure of folders like CakePHP provide for you... for several websites maybe the structure of CakePHP is just enough for you, but probably not all of your projects...

So the idea behind this post was to open a bit a mind, there is no cake recipe for all the projects, each project has own needs, and a different logic.

In the nexts post I'll approach some examples of structure to be used in projects where you can do your own structure, your own way to handle and organize your logic of projects, doing exactly your application needs and also make using of frameworks, in the case CakePHP.

By the way for who is intersting in this post I'd recommend to check this video:


<iframe width="560" height="315" src="http://www.youtube.com/embed/WpkDN78P884" frameborder="0" allowfullscreen="true">
    
</iframe>

It's a lecture of <a href="https://sites.google.com/site/unclebobconsultingllc/">Robert Martin</a>, in a ruby conf where he talks also about the Architecture of your project, it's a great video with a great thougths. I strongly recommend to you check this video.
