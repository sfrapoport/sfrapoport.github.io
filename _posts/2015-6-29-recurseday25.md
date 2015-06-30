---
layout: post
title: RC Day 26 
---

Today was a find-my-groove-back kind of day. At the end of last week I had been feeling like I wasn't making meaningful progress, and I found myself jealous of people who were pairing a lot, getting help from lots of folks and making REAL THINGS. 

So I decided that today I would pair with folks and get help instead of moping helplessly about some amorphous goal I wasn't meeting.

After check-ins, I started with a code-kata workshop run by Jesse Chen - who is a TDD rockstar. Got to pair with Tim Sell, review Object-Oriented Python and test conventions. Pairing is always a great reminder that there are so many ways of solving a problem different from the path I would originally have taken. But 35 minutes is a very short time... And boy is it weird to hit delete without finishing the code.
My afternoon project was to keep working on Kamal's shell workshop, picking up where I got stuck last time. And so, I asked Kamal for help implementing pipe in my python shell. This turned out to be a rather complicated problem, and we went down a lot of rabbit holes to diagnose some unexpected behavior. The first problems had to do with my not quite understanding file descriptors, and the inability to predict the order in which the kernel will execute the system calls that you've sent off!

The second problem, which we did not succeed in fixing, shows up with the following command: '''yes | head'''. This ought to print yes 10 times and exit (yes is a crazy command that prints the input indefinitely. It takes a ton of CPU power. Make sure to kill it properly). The 'head' command prints the first 10 lines of its input, and when it's done, it should kill the read stream coming from the pipe, which should result in killing the write stream coming into the pipe. But while that *does* happen in my zsh shell, it does not happen in my Python shell. We haven't yet figured out how to fix this.

I learned a lot about shells, processes, and forks. I also learned a lot of tools for exploring processes from the command line (pgrep, pstree, lsof).

Bottom line: RC is filled with such awesome people. The more you ask for help, the more help you get and the more you learn. So 



*A shell is a container for a process
*You cannot understand processes without understanding pointers


