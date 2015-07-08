---
layout: post
title: Just test it!
---

Where I left my shell yesterday, I knew that I had a problem, and I had spent hours tinkering with the code to diagnose the error. Why did single file redirects (`ls -la > lsa.txt`) and multiple pipes (`ls | wc | head`) work as expected, but piping & redirecting in the same command (`ls | wc > ls_wc.txt`) go nuts? 

At some point I had done so much tinkering that multiple pipes had stopped working too. And then I remembered Tom saying yesterday that writing tests was a really effective way to make changes bit by bit, but not break the working code. Except when I started to think about writing tests for my shell, it seemed impossible. There were no `return` statements and so I couldn't just test the value of a function against what I was expecting! And even if I could test against the 'return' value, how would I hard-code the formatting of the expected value to match that produced by the command line? So I went to talk to Tom... again... about tests. 

What I learned about writing unit-tests (tests that check one little piece of code or behavior):

+ When you've been running the same print statements over and over, it's probably a good idea to automate
+ Python's unittest module makes it easy to run lots ot tests quickly
+ There are libraries that emulate files and directories since you don't want to muck with your real files during testing. This sounded crazy to me when Tom first mentioned it, but it makes a lot of sense once I started wrapping my head around this new way of thinking.
+ There are tricks to get around ugly formatting and long output - like checking the first word, or the length of the output.
+ I need to explore mock. It has MAGIC METHODS! And it looks promising for integration testing (testing whether the pieces fit together).

So I spent a long while writing tests. When I got home, I decided to implement Tom's other suggestion from yesterday: When you have a problem case, isolate it by stripping out all the rest of the code! I sat down to do this, and figured out the problem! I had hard-coded file-redirection to always read from STDOUT, but when working with pipes, I needed to read from the write-end of the last pipe! And once I changed that behavior and made sure that all pipes were being properly closed, IT WORKED!  

One thing I realized: I was so hyper-focused on finding this bug that I totally forgot to `git commit` as I went along, so when I went to Tom to talk debugging strategies, and he asked me if I could revert to working code... I could not. (Note to self: Commit all the things! JUST DO IT! Until it's automatic and I don't have to think about it anymore). 



