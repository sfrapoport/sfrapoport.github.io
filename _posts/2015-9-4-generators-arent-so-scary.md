---
layout: post
title: Generators aren't so scary: Some lessons from Python
---

I've been working through (Fluent Python) [http://www.amazon.com/Fluent-Python-Luciano-Ramalho/dp/1491946008] for the past week or so. Today, as I was finishing the chapter on Iterators, Iterables and Generators, I came across the following slide from David Beazley's presentation: 'A Curious Course on Coroutines and Concurrency':

+ Generators produce data for iteration
+ Coroutines are consumers of data
+ *To keep your brain from exploding, you don't mix the two concepts together*
+ Coroutines are not related to iteration

Right away I thought: 'damn, I wish I had read this when I tried to grok JavaScript generators!' I googled 'JavaScript generators' to see whether the results would pass the third of these principles.

The (first)[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators] (two) [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*] results, from MDN, explained iterators and generators, and only then got into passing data into generators (er, coroutines). Nice!

Result three is a four-part series on generators from Kyle Simpson, whose explanations of JavaScript closures and this helped me a ton. Here's a code snippet:

	function *foo() {
	    var x = 1 + (yield "foo"); 
  	  // This line PRODUCES 'foo' and CONSUMES whatever is passed in
 	   console.log(x);
	}

YIKES! (And this is the first example in the *basics of generators* post).

Then, I saw an addendum to (a post)[http://tobyho.com/2013/06/16/what-are-generators/] lower in the results listing:

Update: since this article was first published, the send() method* has been removed from the spec. *send(value) was replaced with calling next with a parameter value, i.e. next(value).* 

*send() is used in Python to send data back, coroutine style

Separation of generators and coroutines fail!

The rest of the posts focused on using generators to clean up asynchronous code. And this use case totally makes sense! Yielding to an asynchronous call lets you to pass results back to the caller with next(). No ugly nested callbacks, no weird promises syntax! 

But I think the elegance of this use case has come at the expense of brain explosions, especially for developers who don't already understand generators. 

For folks who are still mystified by generators: There are plenty of great resources for learning about generators and coroutines (I recommend (MDN) [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators] and (Mozilla Hacks) [https://hacks.mozilla.org/2015/05/es6-in-depth-generators/]), but it's easier to make sense of these concepts if you master them separately! And when you do master these tools, you may find that they are useful in other contexts!

PS: The SoapBox section at the end of this Learning Python chapter has a fun exploration of the history of generators in Python. Some folks tried to argue for a special generator keyword instead of the generic function def keyword, but they lost that battle. The author is in favor of lots of syntactic sugar to make things easy to understand. This may well color my thoughts here.


