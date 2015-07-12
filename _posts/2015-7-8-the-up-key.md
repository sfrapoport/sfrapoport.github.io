---
layout: post
title: UP!
---

After fixing the bug that had kept me enthralled for days on end, I decided to add history to my shell. Like how in a normal terminal, when you press the UP key, it lets you walk through a whole bunch of earlier commands, to save yourself the typing. (Really smart shells have tab-autocompletion as well, but that's another project for another day).

The first step was to capture a key press on the <UP> key. I had been relying on `sys.stdin.readline()` and that wouldn't work anymore, since it only captured whole lines of input.

That sounded easy enough, but when I started googling around, it was surprisingly difficult to find things! There were a few libraries referenced - `curses`, `curtsies`, and `PyGame` (since games require a lot of instantaneous key presses). I tried `curses`, but the defaults required recreating the screen in a way that didn't interface naturally with the shell I already wrote. That was a no-go. So I tried `curtsies`, and lucky me, I spend most of my day in the same room as its [author](https://github.com/thomasballinger/curtsies), so I knew I could get help if I needed it.

Amazingly, the very first example on the `curtsies` docs page was very easy to adapt to my purposes:

{% highlight python %}
def read_char_curtsies():
    with Input(keyname='curtsies') as input_generator:
        for e in Input():
            if e == u'<UP>':
                return 'up'
            else:
                return e
{% endhighlight python %}

This succeeded in capturing input, but it did not get along very well with my shell prompt, which wouldn't print on the screen until after my first key press, and the two different streams of input seemed to be randomly deciding what line they wanted to go on. I asked Tom for help, and he told me I needed to flush the buffer. So I did that, and it worked, but I didn't like how I was using two different interfaces to capture the first character and the rest of the line, so I asked him for help in thinking through other ways of approaching the problem.

He sent me in the direction of the termios and tty modules, which are OS/Python built-ins that I had stumbled upon in my research into this problem, but was scared off by the sparse Python documentation. Tom said that they required spending time in man pages, and so I went back to my programming cave, prepared to dive into the Linux man pages, which gave me some clues about the flags I needed to set in order to capture input. The man pages don't, however, help you with syntax, especially in python. I managed to find enough examples online of Python for raw I/O to hack out this function: 

{% highlight python %}
def read_char_raw():
    #Get the file descriptor for STDIN and copy its settings
    fd = sys.stdin.fileno() 
    old_settings = termios.tcgetattr(fd)
    new = termios.tcgetattr(fd) 
    #Set terminal to immediately execute commands and echo bytes that come in			
    new[3] = new[3] | termios.ECHO 		
    termios.tcsetattr(fd, termios.TCSANOW, new)	
    try:		
        #Collect bytes intead of unicode characters								
        tty.setraw(fd)						
        c = sys.stdin.read(1)				
        #If first byte matches first byte of UP character
        if c == '\x1b': 					
            n = sys.stdin.read(2) 			
            if n == '[A': 						
                return 'up'					
            else:
                return ''
        else:
            return c
    finally:								
        #Set STDIN back to normal
        termios.tcsetattr(fd, termios.TCSADRAIN, old_settings)
{% endhighlight %}

Things I learned while working on this:


+  Some characters are more bytes than other characters! (Apparently there is a magical flag on the shell that resolves these inconsistencies for back-space, because otherwise, you might delete only one byte and garble all the text). Which is to say that at some point, you have to deal with [character encodings](http://www.joelonsoftware.com/articles/Unicode.html). I still have to read that article.
+  Finding good code examples for systems-level programming when you don't know C is difficult.
+  The clean code implementation using curtsies is nice, and I may well use it for the final version of my shell, but I really do like understanding things under the hood!
+  Linux man pages are dense, but I find that I prefer reading the docs to following tutorials. 
+  Even though I want to learn C, I'm holding onto Mary's advice from the 1st day of RC: Learn one programming language *really* well. I can't say I'm there yet with Python OR Javascript.
+  I'm still working on getting pygments and code formatting up and running, so it's ugly right now. 


