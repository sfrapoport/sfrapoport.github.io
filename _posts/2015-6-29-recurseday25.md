---
layout: post
title: RC Day 26 
---

Today was a find-my-groove-back kind of day. At the end of last week I had been feeling like I wasn't making meaningful progress, and I found myself jealous of people who were pairing a lot, getting help from lots of folks and making REAL THINGS. 

So I decided that today I would pair with folks and get help instead of moping helplessly about some amorphous goal I wasn't meeting.

After check-ins, I started with a code-kata workshop run by Jesse Chen - who is a TDD rockstar. Got to pair with Tim, review Object-Oriented Python and test conventions. Pairing is always a great reminder that there are so many ways of solving a problem different from the path I would originally have taken. But 35 minutes is a very short time... And boy is it weird to hit delete without finishing the code.

My afternoon project was to keep working on Kamal's shell workshop, picking up where I got stuck last time. And so, I asked Kamal for help implementing pipe in my python shell. This turned out to be a rather complicated problem, and we went down a lot of rabbit holes to diagnose some unexpected behavior. The first problems had to do with my not quite understanding file descriptors, and the inability to predict the order in which the kernel will execute the system calls that you've sent off!

The second problem, which we did not succeed in fixing, shows up with the following command: ```yes | head```. This ought to print yes 10 times and exit, but in my shell, it prints 10 'y's, but the yes command continues to run, and wastes a ton of CPU power. 

This bug forced me to more clearly articulate what pipe actually does. Any command before a pipe is a write stream. Pipe allows the stream that is being written to on one end to be read by the command on the other side of the pipe. In our case, the 'head' command prints the first 10 lines of its input, and when it's done, it closes the stream from which it reads. The implementation of pipe should guarantee that when one end of the pipe is closed, the other end should be automatically closed as well - in this case, killing the infinite stream of 'y'. The standard shells all do this, but my shell does not (yet). 

Bottom line: RC is filled with such awesome people. The more you ask for help, the more help you get and the more you learn. Also, bugs can be great learning opportunities!



