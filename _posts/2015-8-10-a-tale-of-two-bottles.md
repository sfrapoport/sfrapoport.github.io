---
layout: post
title: A tale of two bottles
---
I've been eager to spend time dissecting unfamiliar code-bases for a while, so I was excited about Tom's workshop today: code-reading the (bottle)[https://github.com/bottlepy/bottle] microframework. was excited about this workshop. I searched the RC chat system history to find Tom's message, but I couldn't find it anywhere, so I cloned the bottle repo and started browsing the ~4000 lines of code. The class names and error code made sense to me, but everything else seemed impenetrable - ugly regex matching and layers upon layers of abstraction. 

So I get to the workshop, and Tom mentions something about 500 lines of code is actually more like 300 if you cut out whitespace and some boilerplate. I was like... um, 500 lines of code?! I have 4000 lines of code here!

If I had known that Tom's message had been posted to the email list instead of the chat system, I would have known that we were meant to look at the (FIRST commit)[https://github.com/bottlepy/bottle/blob/4f50cece28b8ee3ff1c5bcf3f8a7bd1d3bbf6128/bottle.py] to bottle, from 2009. That code, I can wrap my head around! It has basic routing, a server built entirely from the Python standard library, and wrapper functions for turning route handler functions declared in the app into HTTP response texts. And all the regex were READABLE!

I was so relieved. It turns out the code I was so intimidated by started as something I could imagine myself writing, and took shape over 6 years of development!

And so I realized (for perhaps the gagillionth time this summer) - that smart abstractions come about by first building things stupidly, then noticing repetitive code and refactoring. If you're lucky, you can make this process faster by showing the code to someone with more experience, who can share the tools that they have learned for tackling them. And the nice thing about being at RC is that I'm in a room full of people like that. And even better, they tend to get really excited when I show them 100 lines of code that I *know* could be better, because they can play code golf, or share a clever functional way of dealing with the problem. And since they get really excited, it's much less scary to share the code that I know is going to be ripped to shreds over the course of the next 10 minutes.
