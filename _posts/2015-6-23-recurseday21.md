---
layout: post
title: Week 4 - On cleaning up
---

I have been working through [Data Science from Scratch](http://joelgrus.com/2015/04/26/data-science-from-scratch-first-principles-with-python/) with Jesse Chen. Every day we read through and implement a chapter, and usually extend the work in some way. The algorithms are pretty straightforward, and the code is very clean. I highly recommend the book to folks who are interested in the basics of Data Science. 

Today we did the chapter on natural language processing, both with Markov chains and with grammars. Natural language processing is fun, so I decided this afternoon to use it to imitate famous authors, whose texts are in the public domain courtesy of Project Gutenberg.

See if you can guess the works that produced each of the following sentences:


1) Where are these Gentlemen ? Come bring me where they are.
2) And every thing ye did not stand up in order upon the earth be removed for ever , even great and strong : for we must be an abomination
3) You know , among the failures which the wind changed into a thin quarto of hot - pressed paper , or of mind , he was sorry , sir .

The main takeaway from this project: Most of the work is in cleaning up the data. Commas (and other non-period punctuation) are treated as words in the naive algorithm. This makes for some surprising transitions, where three words appear together only because the comma has pivoted from one word to the next. I suppose this mirrors work in the real world, where the first 80% of the job can be done in 20% of the time.  

Answers: 1 - William Shakespeare's Macbeth. 2 - Bible - King James. 3 - Jane Austen's Emma.