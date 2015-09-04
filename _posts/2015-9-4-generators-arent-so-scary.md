---
layout: post
title: Generators aren't so scary
---

I've been working through [ Fluent Python ](http://www.amazon.com/Fluent-Python-Luciano-Ramalho/dp/1491946008) for the past week or so. Today, as I was finishing Chapter 14: Iterators, Iterables and Generators, I came across the following slide from David Beazley's presentation: 'A Curious Course on Coroutines and Concurrency'

1. Generators produce data for iteration
2. Coroutines are consumers of data
3. *To keep your brain from exploding*, you don't mix the two concepts together
4. Coroutines are not related to iteration

My immediate reaction: Everyone writing about generators in JavaScript ignores the 3rd rule! Pedagogy fail! (I have a lot of 'bad pedagogy' reactions. I used to be a teacher).

I googled JavaScript generators to see if my reaction was grounded in reality.

The [first](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators) [two](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) results thoroughly explained iterators and generators in depth before discussing two way data passing. Nice! 

Result three was a [four-part series](http://davidwalsh.name/es6-generators) on generators from Kyle Simpson, whose explanations of JavaScript this and closures have helped me a ton. Here's a code snippet:

	function *foo() {
	  var x = 1 + (yield "foo"); 
	  // This line PRODUCES 'foo' 
	  // It CONSUMES whatever is passed in
	  console.log(x);
	}


YIKES! (And this is the first example in the *basics* of generators post).

Then, I saw an addendum to [a post](http://tobyho.com/2013/06/16/what-are-generators/) lower in the results listing:

> Update: since this article was first published, the send()* method has 
> been removed from the spec. send(value) was replaced with calling next 
> with a parameter value, i.e. next(value).

*send() is used in Python to send data back, coroutine style

ES2015 itself appears not to care so much about keeping generators and coroutines separate!

Several of the remaining top 10 results explained how to use generators to clean up node code. The takeaway: Generators (er, coroutines) let you pass results of asynchronous function calls back to a main function with next(). Goodbye ugly nested callbacks! No more weird promise syntax! Magic, clean JavaScript!

But I think this delightful use case has come at the expense of brain explosions, especially for developers who don't already understand generators. 

A note for folks who are still mystified: 

There are plenty of great resources out there. It's much easier to make sense of these concepts if you master them separately. I like [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators) and [Mozilla Hacks](https://hacks.mozilla.org/2015/05/es6-in-depth-generators/).  And when you do master these tools, you may find that they are useful in other contexts!

PS: The author of Learning Python is in favor of lots of syntactic sugar (extra keywords and the like) to make things easy to understand. This may color my thoughts here.


