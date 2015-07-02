---
layout: post
title: What IS a pipe, anyway? 
---

Yesterday, Kamal and I got to the bottom of a fascinating bug (he wrote it up excellently [here](http://kamalmarhubi.com/blog/2015/06/30/my-favourite-bug-so-far-at-the-recurse-center/)). I read OS code for the first time, and it was super exciting. I felt like an OS ninja. 

So today was a day of little bug fixes to wrap up some old project loose ends:


1) I had added a database to my url-shortener. Retrieving a value from the database wasn't working, so Pietro and I used the Node debugger to try to diagnose the problem. The information it gave us seemed unhelpful, since it just spat back the state of our database for every query. We showed the problem to Ken, who helped me figure out that we needed to use callbacks to actually 'return' the data. Dear old Javascript.

2) I wanted to clean up the tweets that my twitter bot generated. Fix punctuation, make quotation marks work properly. I thought: 'This is a job for regular expressions!'But the regexp I was *sure* would work refused to cooperate. I asked Tom for help, and I learned that the \b character, which I thought signified 'Boundary between white-space and word' actually signifies 'boundary between non-letter and letter.' I realized that cleaning up this data would be a serious, long undertaking, and that learning regexp is not so high on my priority list. So the twitter bot will have to wait.

3) In light of yesterday's bug-fixing victory, I decided I would try to implement MULTIPLE pipes in my shell. I thought this would be a short project, but it took up the rest of my afternoon (though I spent some of that time watching Nat prototype an awesome recurse-social-network-list app). (And it doesn't work... yet).


Some things I figured out along the way:

-Better to sketch on paper than in code. I accidentally wrote five versions of the same function while drafting my first attempt in the text editor.

-When drawing pictures, it is important to slow down and articulate, in CLEAR SENTENCES, what the arrows pointing everywhere represent.

-In my universe of abstractions that don't reflect reality, a pipe can be capped. I should be able to write data to a pipe and read from it at some moment in the future. I think I got this from the first diagrams I drew, where a pipe was represented by a... pipe. The thing is that while metal pipes are containers (when capped) the pipe operator can't hold onto anything at all. Ever. (I think). It's just a connection between a write file in memory and a read file in memory, so that when data is written to the write file, it can be read out of the read file. There is no middle 'space' where the file 'lives' for even a second. And so, I can't use the pipe as a temporary storage container, which is exactly what the code I wrote today tried to do.

And so, I guess I'll have to reimplement the code. The way I tried to do it today seemed elegant, but I'm pretty sure that it relied on an untenable abstraction, and so it's doomed. 
