---
layout: post
title: A tale of two bottles
---
I'm always eager to spend time dissecting unfamiliar code-bases, so I was excited about Tom's workshop today: code-reading the [ bottle ](https://github.com/bottlepy/bottle) microframework. I cloned the bottle repo and started browsing the ~4000 lines of code to prepare for the workshop. On first read, the classes and errors made sense to me, but everything else seemed impenetrable. 

I got to the workshop, and Tom mentioned that the code base is more like 300 lines if you cut out whitespace and boilerplate. 300 lines of code?! I had 4000!

If I had known that Tom's message had been posted to the email list instead of the chat system, I would have known that we were reading the [ FIRST commit ]( https://github.com/bottlepy/bottle/blob/4f50cece28b8ee3ff1c5bcf3f8a7bd1d3bbf6128/bottle.py ) to bottle, from 2009. Oops. And yay!

So I checked out that commit, and was instantly relieved. This code I could wrap my head around! I saw basic routing, a server built entirely from the Python standard library, and wrapper functions for turning route handlers declared in the app into HTTP responses. Even the regex were decipherable!

It turns out the code I was so intimidated by started out as something I could sort of imagine myself writing, and took shape over 6 years of development!

And so I was reminded (for perhaps the hundredth time this summer) - that smart abstractions come about by first building things stupidly, then noticing repetitive code and refactoring. If you're lucky, you can make this process faster by showing the code to someone who can share tools they have learned for tackling similar problems. 

The nice thing about being at RC is that I'm in a room full of those people. And they tend to get really excited when I show them 100 lines of code I want to improve, because they can play code golf, or share their favorite functional programming trick. And since they're so excited, it's much less scary to share the code that I know is going to be ripped to shreds over the course of the next 10 minutes.
