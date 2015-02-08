---
layout: post
title: In which I code up a tic-tac-toe game
---

I've gotten very comfortable solving problems on CodeWars and Project Euler. This has been great for increasing my fluency in JavaScript, and helping me fine-tune my problem solving skills. But, all the code there is self-contained. No file systems, no servers, and no DOM model. So this week, I'm scaling back on algorithmic complexity and coding up simple interactive games, to help me review the native JS DOM model (for code this small, there is really no need for jQuery).

Two things I learned from writing this game:

1 HTML collections are not arrays. It took ages to figure out why the cells in my gameboard were not responding to the click handler I had set up with forEach. Once I realized that I could use Array.prototype.forEach.call on my HTML collection of cells, everything worked.

{% highlight js %}

var cells = document.getElementsByClassName("cell");
Array.prototype.forEach.call(cells, function(element) {
    element.addEventListener("click", cellClick, false);
});
{% endhighlight %}

2 Be careful with incrementors! I originally made incrementing the number of turns the last step in the turn handler, which resulted in the turn variable initializing to 1 in reset games.

{% highlight js %}

function cellClick() {
    gameCounter.turns++;
    if (this.classList.contains("o") || this.classList.contains("x")) {
        alert("Click a different cell");
    } else {
        if (gameCounter.turns % 2 === 0) {
            this.classList.add("o");
            gameCounter.olist.push(this.id);
            if (win(gameCounter.olist)) {
                alert("O has won the game! Click to restart!");
                reset(gameCounter);
            }

        } else {
            this.classList.add("x");
            gameCounter.xlist.push(this.id);
            if (win(gameCounter.xlist)) {
                alert("X has won the game! Click to restart!");
                reset(gameCounter);
            }

        }
        if (gameCounter.turns >= 9) {
            reset(gameCounter);
        }

    }
}

{% endhighlight %}
