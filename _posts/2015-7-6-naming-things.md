---
layout: post
title: Naming Things
---

Today I added input redirection to my shell (`cat < ls.txt`). This actually went more smoothly than any previous redirect handling, YAY! BUT... when I tried to enable piping from an input redirect, I realized that the program was going in all sorts of circles. The 'MUST REFACTOR' this bells went off in my head. One problem: the only thing I knew about refactoring is that it's what you're supposed to do when your code is repetitive and/or hard to follow. I had no clue how you're supposed to go about DOING it.

First - I tried to draw out the relationships between all the different functions in my code. The arrows were *still* taking me in circles. But I could see the source of some of my problems, and so I knew where to focus my energy.

Next - I wrote out the various variable names I was using to see where I was being inconsistent.

Finally - I wanted to know if there were best practices for refactoring, so I talked to Tom. I learned a lot from this conversation:


+Names are REALLY important:
	-Function names should describe what functions DO (`convert_filename_to_file_descriptor`). Not the ROLE they play in the code (`handle_filename`).
	-CONSTANTS should be declared globally and NEVER CHANGE
	-Be careful when changing variable names. They need to change EVERYWHERE. This is easier with specific names like `convert_filename_to_file_descriptor` than with generic names like `command`
	-Short names are useful for loop parameters and indices, but consistency is still super important 
+It's ok to repeat yourself if it makes the control flow clearer. 
+You can pass information onto a new scope (e.g. a child process) using function parameters (this fixed a really ugly control flow problem)
+Talking about your code in words (and not just pictures) is very helpful. I need to get in the habit of rubber ducking a problem in words BEFORE I approach a facilitator for help, so that I can more quickly zero in on a problem.
+Writing good tests is a really good way to refactor (and to reduce the need for large-scale refactoring). I don't know how to approach about writing tests for this shell, though, because there aren't so many return values to check against!

I spent the rest of the afternoon refactoring, and cut my code from 230 to 150 lines. It was much easier after talking through the refactor. But... renaming everything consistently turned out to be rather a pain in the neck, and I hope that next time I write anything longer than 20 lines of code, I think through my naming conventions before I start!