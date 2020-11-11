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

The area of the "No Sign Zone" is then just the sum of these three areas:

$$\int_\Omega \nabla u \cdot \nabla v~dx = \int_\Omega fv~dx$$


## Here is a secondary hand eazeading

Here's a useless table:

| Number | Next number | Previous number |
| :------ |:--- | :--- |
| Five | Six | Four |
| Ten | Eleven | Nine |
| Seven | Eight | Six |
| Two | Three | One |


How about a yummy crepe?

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg)

It can also be centered!

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg){: .mx-auto.d-block :}

Here's a code chunk:

~~~
var foo = function(x) {
  return(x + 5);
}
foo(3)
~~~

And here is the same code with syntax highlighting:

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

## Boxes
You can add notification, warning and error boxes like this:

### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.
