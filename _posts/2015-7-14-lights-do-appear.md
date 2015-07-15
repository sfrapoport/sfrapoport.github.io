---
layout: post
title: Lights DO appear
---
This morning was pretty much a pool of frustration. Liz and I ran into errors using PostgreSQL & SQLAlchemy that we couldn't figure out. Error messages told us that column names didn't exist when we had definitely created them, and that tables were using conflicting types for the same key. Worst of all, the error messages persisted even after we fixed the code.

The fact that the error messages didn't match what we saw made us decide to actually look inside Postgres to understand why. Turns out, the database we made the first time we ran the code without errors was sitting there, blissfully ignorant of the improvements we had made. We had relied completely on SQLAlchemy to take care of the database end of things. BUT... it turns out that database engine only creates new tables if they don't exist. It LOOKED like we were changing the schema, but the tables stayed exactly the same. 

So, we deleted the tables in Postgres, and ran the database generation script again. The old error messages were replaced by new ones, and we began a cascade of progress, and now, we have a database, which has actual data in it! Whee!

Things I learned:

+  Walks around the block, coffee breaks, and ice cream are really good ways of getting unstuck.
+  Even when it feels like I'm going in circles and making no progress, mental models are being built and learning is happening. 
+  Read error messages closely. They are your friends, especially when they don't make sense.
+  When you're working with abstractions, it's worth looking under the hood. Code is not magic, and understanding what *actually* happens can help you understand and fix unexpected behavior.
