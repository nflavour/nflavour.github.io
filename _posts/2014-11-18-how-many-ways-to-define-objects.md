---
layout: post
title: "Objects in JavaScript"
date: 2014-11-18 23:55:00
categories: programming
---

## Functions ##
Let's first talk about functions. There are so many ways are there to define a function (which actually "inherits" an object) in JavaScript.

JavaScript treats functions and objects as first-class citizens, which means they can be defined, called, passed, returned, or do anything else much like you can do to a variable. Here are examples of how to declare a function (that I know).

{% highlight javascript %}
// the traditional way
function add(x, y) {
  return x + y;
}
add(4, 5); // returns 9
{% endhighlight %}

{% highlight javascript %}
// function literal
var add = function (x, y) {
  return x + y;
}
add(4, 5); // returns 9
{% endhighlight %}

{% highlight javascript %}
// function literal with function name
// the function name is useful for recursion
var add = function foo (x, y) {
  return x + y;
}
add(4, 5); // returns 9
{% endhighlight %}

{% highlight javascript %}
// anonymous function
function (x, y) {
  return x + y;
}(4, 5) // returns 9

// An anonymous function must be invoked at the moment of declaration, 
// otherwise there would be no way of calling it.
// Or it can be simply used as a parameter to another function
// this is often the case in jQuery functions
{% endhighlight %}

One great thing about function as first class citizens is that they can be passed in to other functions as parameters.

{% highlight javascript %}
// this works with either way of declaring a function
var add = function (x, y) {
  return x + y;
}

var foo = function (func, a, b) {
  return func(a, b);
}

foo(add, 4, 5); // returns 9
{% endhighlight %}

This is a really contrived example. But, it does show how the `add` function can be passed into `foo` and called. A good example is the `map` function in some functional program languages, like in `Scheme`. `map` takes two parameters, first one a function, and second one a list, and it applies the function to every element of the list and spit out a new list

{% highlight scheme %}
;; create a list of numbers
(define myList (list 1 2 3 4))

;; define a function that does something magical to the parameter
(define (magic x)
 (+ (* x x) x))

;; apply map using the magic function to myList
(map magic myList) ;; returns '(2, 6, 12, 20)
{% endhighlight %}

## Objects ##
Objects are even more interesting. They can be pretty much declared in the same way as functions, but there's a bit more to them.

{% highlight javascript %}
// most simple object
var student = {
  first_name: "Tony",
  last_name: "Tang",
  age: 15,
  english: 95,
  math: 97,
  geography: 85,
  history: 78,
  gym: 85,
  get_average: function() {
    return (this.english + this.math + this.geography + this.history + this.gym) / 5;
  }
};
// an object named student is instantiated with the fields
// the form is identical to the JSON format
student.first_name; // returns "Tony"
student.first_name = "Bob";
student.firsT_name; // returns "Bob"
student.get_average(); // calculates average of the 5 courses. 88
{% endhighlight %}

The same can be done with a form similar to an anonymous function

{% highlight javascript %}
// object in form of an anonymous function
var Student = function() {
  var first_name, last_name, english, math, geography, history, gym;
  var get_average = function() {
    return (this.english + this.math + this.geography + this.history + this.gym) / 5;
  }
};
// with this, it becomes a constructor
// we can create a new Student class with the new keyword
// note 'Student' is capitalized because of constructor
//  convention that first letter be capitalized

student_1 = new Student;
student_2 = new Student;
// I just created two new instances of the Student object
// each object is unique on its on
student_1.first_name = "Tony";
student_2.first_name = "Bob";

student_1.first_name; // returns "Tony"
student_2.first_name; // returns "Bob"
{% endhighlight %}

Actually a function is an object

{% highlight javascript %}
// object in form of a function
function Student() {
  // fields and methods go here
}
// Same as previous example
{% endhighlight %}

Adding function directly into the constructor looks like classes in other Object-Oriented Language, like Java or C++. However, it is not the optimal way of add functions in JavaScript Objects.

JavaScript is a prototypal language. So everything "inherits" an object. Student is a prototype created from Object. To add functions to an object efficiently is through using the `.prototype.function` property

{% highlight javascript %}
// object in form of a function
function Student() {
  // fields and methods go here
}

// to add a function called full_name
Student.prototype.full_name = function() {
  return this.first_name + " " + this.last_name;
}

var student_1 = new Student();
student_1.first_name = "Tony";
student_1.last_name = "Tang";
student_1.full_name(); // returns "Tony Tang"
{% endhighlight %}

By creating Object's method through prototype is much faster because it is how JavaScript intended to process objects. Inheritance is simple, invoke this before adding any methods `Student.prototype = Object.create(ParentObject.prototype);`. Student prototype will be a copy of the prototype of another Object, so it "inherits" all the functionality of the other Object.