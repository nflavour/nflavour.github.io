---
layout: post
title: "Learning Functional Programming"
date: 2014-11-16 23:20:00
categories: programming
---

*Note: I suspect I will be writing a lot more in the next week or two about Functional Programming and doing it in JavaScript*

In CS 135 the languate we learned was Scheme, a pure functional programming language (at least that was the restriction from our professor). I've learned imperative programming a long time ago, in Turing and Java. So when I first faced functional programming, I was confused and frustrated. But quickly after I realized the simplicity and elegance in functional programming. However, I never understood a good use for it, and why I would ever want to use functional programming. 

Until, I recently started learning Node.js. It seems that node.js `modules` uses a lot of "higher-order functions" at least according to some of the tutorials I've followed. After some research, I learned about the concept of Functional JavaScript. I first though Functional JavaScript was some new inventive way of writing JavaScript,but it is simply Functional Programming in JavaScript. I hope to learn underscore.js so I can practice with some data manipulation and practice functional programming in JavaScript.

----

I also learned a few pretty interesting concepts in Functional Programming. `Currying` is such a funny word, it's sounds like to make something a curry. It is really simply scaffolding a complex function into a simpler one (sort of).

{% highlight javascript %}
// a normal function
function add (x, y) {
  return x + y;
}

// currying the function
function add (x) {
  return function (y) {
    return x + y;
  }
}

// the add function returns an anomymous function (lambda) 
// to add two values, instead of add (5, 6)
add(5)(6); // returns 11
{% endhighlight %}

----

Recently, functional programming has become very popular because of concurrency in distributed systems and multicore processors. All those big data in multiple data centers requires lots of things to run well at the same time, so they can utilize the resources efficiently. Imperative programming has to run functions in sequential order because what if one function changes the value of a variable, the next function may depend on that variable. So side effect in imperative programming is actually a performance hinderance. In functional programming, side effect is not allowed. So you can run a function at the beginning of the program or at the end, it doesn't matter. So, this allows multiple function run together, and the result is still the same. I hope to learn more about concurrency as I study node.js.

----

Yes I really like JavaScript.