---
layout: post
title: I was wrong... but not about that
---

Yesterday, I got stuck on pipes. And after poking away at it for hours and watching NOTHING happen, having no tools for communicating with the system to give me clues about why, I was convinced that I had a bad mental model for pipes.

I revisited that code this morning, got my 2 pipes in a row working after talking it over with Laura, and started to think that I actually *did* understand pipes (and Mark confirmed this on Zulip). What I didn't understand was reading and writing to them. More specifically, I didn't understand what stdin and stdout were, and I kept going in circles about which end of each pipe I was supposed to be reading from and writing to at any given moment. 

After talking this over for the fifth or sixth time today, and really struggling to explain the problem to Tom, something clicked. I was thinking of stdin (file descriptor 0) as the 'read' end of the terminal, and stdout as the 'write' end of the terminal. This was a pretty unhelpful model, it turns out.

1) 'Reading' and 'writing' are relativtely accurate terms from the vantage point of the process, not from the vantage point of the user of the result of that process. Whatever the shell/terminal writes is what *I* read. 

2) Stdin and Stdout are only linked to the terminal/shell when that is the active process. EVERY SINGLE PROCESS automatically has a magical communication channel between input and output, which links the process and its environment at start-time. (Apparently, this was a huge development in Unix)[https://en.wikipedia.org/wiki/Standard_streams]. It's just that I only see the results of this process from the terminal, so I think of them as belonging to the terminal. Letting this sink in helped me figure out how to use stdin and stdout to get output from one pipe, transform it with an arbitrary command, and write that to the next pipe in the series. And then, after some little tweaks, I had a working pipe! I could run ls -la | head | head | head | head | wc and it worked! (The repetition of head is a clear indication that I need to learn more bash commands, but that's another project for another day).





