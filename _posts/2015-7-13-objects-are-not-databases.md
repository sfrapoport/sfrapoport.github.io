---
layout: post
title: Objects are NOT databases
---

My goal for this week is to get my hands a dirty with databases. I have managed for the most part to avoid them entirely, and RC is a great place to dive into things I've been avoiding. 

 I was really happy when during checkins, Liz mentioned that she had a yelp dataset that she wanted to work with, in database form. This meant I wouldn't have to set up PostgreSQL alone! I find getting set up with new frameworks pretty frustrating. I don't usually have a mental model of the thing I am setting up, so it's very hard to understand why things go wrong, as they inevitably do. I really appreciate having an expert on hand to field questions, or a partner to wade through the configuration quagmire with me.

Our task for today: Get PostgreSQL and SQLAlchemy set up, and convert a bunch of JSON data into a format usable in SQLAlchemy. The second task, is way harder than it seems. Cleaning up data is *always* annoying. It requires more time than you think it should, and it's absolutely necessary. But converting objects to relational data is a whole different ballgame. It requires rethinking the data model, not surface cleaning.

Things I learned:

+  (From Yaron Minsky's talk this evening). Distributed systems are cool! Another thing to add to my list of 'things I want to learn more about... later.' Note to self: Bring pen and paper to talks so I can draw diagrams. 
+  I still find pair programming way more exhausting than coding on my own - explaining all of my thoughts takes energy. But I'm starting to find it easier.
+  [This paper](https://www.cl.cam.ac.uk/~fms27/db/tr-98-2.pdf) looks like a good introduction to the way relational databases think different from object-oriented databases. Hope to read it tomorrow.
+  The docs and tutorials for SQLAlchemy were much easier to read through after having spent some time playing around with a database and engine. Learning-by-poking-around and learning-by-reading-about-the-system-as-a-whole feed off each other quite well. I definitely need to do both. 