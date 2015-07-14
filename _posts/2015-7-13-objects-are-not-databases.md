---
layout: post
title: Objects are NOT databases
---

My goal for this week is to get my hands a dirty with databases. I have managed for the most part to avoid them entirely. RC is a great place to dive into things that I have been avoiding, so it was time. 

 I was really happy when during checkins, Liz announced that she had a yelp dataset that she wanted to work with, in database form. This meant I would have a buddy to set up databases with! Configuring things is a serious pain, there are so many little things that can go wrong. I don't usually have a mental model of the thing I am setting up for the first time, so it's very hard to understand why things go wrong, as they inevitably do. I really appreciate having an expert on hand to field questions, or a partner to wade through the configuration quagmire with me.

Our task for today: Get PostgreSQL and SQLAlchemy set up, and convert a bunch of JSON data into a format usable in SQLAlchemy. The second task, is way harder than it seems. First of all, cleaning up data is *always* annoying. It requires more time than you think it should, and it's absolutely necessary. But converting objects to relational data is a whole different ballgame. It requires rethinking the data model, not surface cleaning.

Things I learned:

+  (From the talk this evening). Distributed systems are cool! Another thing to add to my list of 'things I want to learn more about... later.' Note to self: Bring pen and paper to talks so I can draw things.
+  [This paper](https://www.cl.cam.ac.uk/~fms27/db/tr-98-2.pdf) looks like a good introduction to the way relational databases think different from object-oriented databases. Hope to read it tomorrow.
+  The docs and tutorials for SQLAlchemy were much easier to read through after having spent some time playing around with a database and engine. There's a back and forth between learning-by-poking-around and learning-by-reading-about-the-system-as-a-whole. I definitely need to do both. 