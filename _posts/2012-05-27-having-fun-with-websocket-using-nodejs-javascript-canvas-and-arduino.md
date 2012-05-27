---
layout: post
title: "Having fun with Websocket using Node.js, Javascript, Canvas and Arduino"
description: ""
category: projects  
tags: [socket.io, express, canvas, serial]
---
{% include JB/setup %}

Last year, I have developed two demo applications using Node.js and Javascript, both were more to have fun.

One of them I have developed with my friend Lucas Texeira, it was a project where we would make use of Webscoket and Canvas to make real time iteration between the browsers.

## Ball.js

*Github:* <a href="https://github.com/krolow/ball.js">https://github.com/krolow/ball.js</a>

The ideia is really simple, we want to drag one ball between differents screens, one user connect and so he comes up inside one queue, the client that has the ball in the screen is able to drag and drop this ball in the area of his browser, if the ball go to left or right this ball should appears in the next or previous screen of the queue...

*The result is possible to see in youtube:*

<iframe width="560" height="315" src="http://www.youtube.com/embed/NgA5EvOryU0" frameborder="0" allowfullscreen></iframe>

To make this possible, we have used:

* Node.js
* Websocket module
* Javascript
* Canvas
 
 
 The second Project I did by self, I was doing one new version of my site and in the same I was planning to use a particle system to make some explosion when the user hit some area of the site... But as I'm not so familiar in front-end development I have to develop some demos to know how to develop a particle system, so I decided to make one interation between my arduino and one javascript canvas page where show one particle system in action:
 
## ArduinoParticles

*Github:* <a href="https://github.com/krolow/ArduinoParticles">https://github.com/krolow/ArduinoParticles</a>

The idea behind is quite simple, instead of make iteration using one mouse I choose to make iteration using a push button in arduino, so if you push the button the arduino communicate via serial port with a Node.js, and this node.js talks via web socket with the front-end client of particle system, the amount of particles is based in the time that you push the button and the frequency...

*The result is possible to see in youtube:*

<iframe width="420" height="315" src="http://www.youtube.com/embed/6yl_jmYQLhM" frameborder="0" allowfullscreen></iframe>

To make this possible, I have used:

* Node.js
* SerialPort module
* Socket.io
* Express 
* Arduino duemilanove
* Javascript
* Canvas
* Canvas.js

As result of this development I have created a simple lib to make easy I start my Canvas projects... it's the <a href="https://github.com/krolow/Canvas.js">Canvas.js</a>. It gives for you a startup canvas, with full size, and also the center points, it also already implements the resize of window, it's simple but helps to start the projects using Canvas.