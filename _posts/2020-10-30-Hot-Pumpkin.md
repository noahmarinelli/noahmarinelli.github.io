---
layout: post
title: Election Day / Beware the Hot Pumpkin
subtitle: Which holiday is spookier this year?
tags: [Riddler]
comments: true
---

## Riddler Express

While waiting in line to vote early last week, I overheard a discussion between election officials. Apparently, there may have been a political sign that was within 100 feet of the polling place, against [New York State law](https://www.nysenate.gov/legislation/laws/EDN/2031-A).

This got me thinking. Suppose a polling site is a square building whose sides are 100 feet in length. An election official takes a string that is also 100 feet long and ties one end to a door located in the middle of one of the building’s sides. She then holds the other end of the string in her hand.

What’s the area of the region outside of the building she can reach while holding the string?
 
**Riddler Express Solution:**
This puzzle is both easier to understand and easier to solve by just drawing it out, so excuse my poor PowerPoint skills and let's examine the following diagram to see how the election official draws out their "No Sign Zone"

><center><img src="/images/RiddlerVotingCircle.jpg" alt="No Sign Zone" style="width: 300px"/></center>

We can imagine our election official walking from the door of the polling place out 100 feet with their string, and sweeping left to right to form the dark grey semicircle with radius 100 feet directly south of the polling place.

The puzzle gets interesting when the election official reaches the points on either end of this semicircle, directly parallel to the southern wall of the polling place. If they attempt to continue to trace the semicircle, their string will run into the corner of the square polling place. For any area north of the southern wall of the polling place, we can see that the results are analogous to the election official tying a 50 foot string to the corner of the polling place, rather than a 100 foot string to the center of the southern wall. This will lead the election official to trace out two light gray semicircles with radius 50 feet.

The area of the "No Sign Zone" (in square feet) is then just the sum of these three areas:

$$\frac{\pi * 100^2} {2} + \frac{\pi * 50^2} {4} + \frac{\pi * 50^2} {4} \\
\approx 15708 + 1964 + 1964 \\
\approx 19635  $$


## Riddler Classic
Instead of playing hot potato, you and 60 of your closest friends decide to play a socially distanced game of hot pumpkin.

Before the game starts, you all sit in a circle and agree on a positive integer N. Once the number has been chosen, you (the leader of the group) start the game by counting “1” and passing the pumpkin to the person sitting directly to your left. She then declares “2” and passes the pumpkin one space to her left. This continues with each player saying the next number in the sequence, wrapping around the circle as many times as necessary, until the group has collectively counted up to N. At that point, the player who counted “N” is eliminated, and the player directly to his or her left starts the next round, again proceeding to the same value of N. The game continues until just one player remains, who is declared the victor.

In the game’s first round, the player 18 spaces to your left is the first to be eliminated. Ricky, the next player in the sequence, begins the next round. The second round sees the elimination of the player 31 spaces to Ricky’s left. Zach begins the third round, only to find himself eliminated in a cruel twist of fate. (Woe is Zach.)

What was the smallest value of N the group could have used for this game?

Extra credit: Suppose the players were numbered from 1 to 61, with you as Player No. 1, the player to your left as Player No. 2 and so on. Which player won the game?

Extra extra credit: What’s the smallest N that would have made you the winner?

**Riddler Classic Solution:**
The clue gives us three clues to the unknown integer N. Note first that if the player x spaces to the starter eliminated, N mod y = x+1, where N is the positive integer chosen for the game and y is the number of participants (the +1 exists because we start the count at 1 at the 0th spot. The player 1 spot to our left is eliminated by a starting count of 2, for example).

N mod 61 = 18 + 1 = 19
N mod 60 = 31 + 1 = 32
N mod 59 = 0 + 1 = 1

Note that as 59, 60, and 61 are coprime, our answer will be in the form $$ N = n mod(59*60*51) $$ or $$ n + k*(59*60*61)$$ where k is a whole number.

Also note that we have arrived at a system of three modular equations, a perfect time to apply the [Chinese Remainder Theorem] (https://en.wikipedia.org/wiki/Chinese_remainder_theorem), a fascinating result in number theory. The Chinese Remainder Theorem basically states that if you have a list of n integers ($$x_{1}, x_{2}, ..., x_{n}$$) with a GCD of 1, an and a second list of n integers ($$y_{1}, y_{2}, ..., y_{n}$$) such that every element of the second set is less than every element of the first set, there is one and only one integer x that is both less than the product of the n integers in the first list and equal to $$y_{i}(mod x{i})$$ for all 0<i<=n. This guarantees that there must exist one and only one $$ N < 59*60*61 = 212280 $$.

I couldn't figure out how to solve this quickly and analytically, so let's just brute force it in R:
```R
i <- 0
test <- FALSE

while (test == FALSE) {
  
  i = i + 1
  
  test <- (
    (i %% 61) -19 ==
    (i %% 60) -32
      &
    (i %% 61) -19 ==
    (i %% 59 -1) 
      &
    (i %% 60) -32 ==
    (i %% 59 -1)  
      &
    (i %% 61) -19 ==
    0
      &
    (i %% 60) -32 ==
    0
      &
    (i %% 59 -1)  ==
    0
    )

}
print(i)
```
This returns 136,232, which is both lower than our upper bound guarenteed by the CRT and can be verified by hand.

**Riddler Classic Extra Credit Solution:**
Again, let's just simulate this in R to determine a winner:
