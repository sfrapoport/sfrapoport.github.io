---
layout: post
title: Enter, history, and a backspace problem
---

After finally getting my shell to respond to the up key, I needed to be able to integrate a history interface, so that instead of writing 'get previous in history,' the up key would print the *actual* history. Writing the history interface was actually pretty easy - and I got it working with no snags. Then I needed to figure out how get raw bytes in order to respond to key presses, without losing the ease of use of python's sys.stdin.readline() function in order to handle each complete line of input correctly.

My first appraoch was to give up on the convenience of readline and implement a raw-byte-line reader. I was already storing and printing the first character of the line, so why not just add a buffer to hold all the text of the line internally, print the rest of the characters to the line, and then respond to the enter key?! I had to figure out a few things about how to manage the control flow for this line-getting loop, but one I wrapped my head around that, it seemed straightforward enough. Problem: I couldn't figure out how to get match the bytes for the <ENTER> key! 

I checked the key-bindings from a few libraries. Curtsies has `<ctrl-j>` for enter, but that didn't work. I read up on unicode strings, but that wasn't really what I needed either. I was just about ready to give up when I stumbled across the docs for the Python 3 bytes module, and recognizd the author's name! Jason Orendorff had given a talk at NashJS in May and I had talked to him after, so I figured, why not, I'll just ping him on slack and see if he gets back to me! Lo and behold, I had a reply within minutes, and we figured out that it was just `\r.` This made me feel kind of silly, but I was really happy to be able to move forward.

I got enter working, and so I could type commands, execute them, type `<UP>` and get previous command entries written at the command line, and type `<DOWN>` and navigate back to the most recent command. The problem now? I haven't implemented backspace. Furthermore, since the input is captured and written from stdin, it's not directly modifiable, and so not only can I not delete my typos, when I run through the command history, it adds a whole series of calls one after the other, which effectively means I can only acces the most recent command.

It might be time to latch onto a terminal wrapping library for the purpose of wrapping up this project. Tom blogged a while back about alternatives to curtsies, which should make it *much* easier to write/delete from the terminal in a more flexible way than either sys.stdin.readline() or the readline module. I do want to do some more work on the web framework I started and some machine learning/algorithm-y stuff. So much to learn! So not enough time to learn it all! 

Things I learned:

+  People love to help! Obviously this is true for people at RC, but I've also had really good luck emailing/pinging people outside for help. Some people I know from Nashville, others whose email addresses I found on websites. I'm still a little bit starry eyed that I just emailed Pragmatic Dave for permission to use the tips from his book for a publicly available command line tool, and that he emailed me back!
+  Sometimes the solution is simple beyond belief  (the enter key)
+  Sometimes solving one problem gives rise to another
+  Writing tests for 'normal' things like a command history class is WAY easier than writing tests for a terminal

