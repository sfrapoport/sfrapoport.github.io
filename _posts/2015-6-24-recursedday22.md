---
layout: post
title: RC Day 22 
---

Today I woke up early, so I got to take a bit of an extended coffee walk through the village and NYU's campus. Before check-ins I had culled a subset of Project Gutenberg data to play with for the Twitter Literature bot I'm hoping to unleash next week (@ILitYou has claimed the Twiterature name, sadly). [John](https://github.com/jdherg) also helped me iron out some tricky shell parameter expansion, which led me to the zsh docs. 

[Jesse Chen](https://github.com/jessechen) and I finished our work through Data Science from scratch - looking at some network analysis algorithms, including a naive implementation of PageRank. It's amazing how simple the ideas at the core of some of these algorithms are (this is as much a comment on the clarity of Joel Grus' writing and code as on the simplicity of the algorithms themselves). As an aside, PageRank is totally dependent on the uni-directionality of the links that make up the internet.  I recall from The Innovators that Tim Berners-Lee wanted links to be bidirectional, and that Walter Isaacson mused that the internet would have been a very different place in a world where all links point both directions.

In the afternoon, after a delicious vegan dim sum fest, I dove into some APIs that will make dealing with the Project Gutenberg data easier and wrote up the guts of the bot implementation. At the end of the day, I paired with April on getting a Django server set up. Much better to follow tutorials together than alone! One thing I like about Django is its natural integration with databases, which is not present in node. That makes it easier to think about actually using a database to store things, which is good.  
