---
layout: post
title: "Abstract Class VS Interface"
date: 2014-08-28 16:18
categories: programming object-oriented
---

The two seems really similar. Lots of website talks about it, and most fail to explain the underlying differences. Because, an abstract class with all class abstract, no fields, it is just like an interface.

The most important difference lies in the relationship between abstract class and the concrete classes that inherit from it, and between the interface and the classes that implements it.

Abstract class and concrete classes have a close relationship. For example, an abstract class is `Figure` and the concrete classes are `Square` and `Circle`. Square and Circle are closely related to a Figure. However, Square and Circle can `implement` PrintToScreen. `PrintToScreen` is an interface. It lists the required algorithm to print to screen. With PrintToScreen, Square and Circle can have its own way of printing to screen. But also, classes like `Windows`, `Browsers`, `CatPictures`, etc, they all can implement `PrintToScreen`.

Figure is very related to Square and Circle, so it works best with an Abstract Class relationship.
{% highlight java %}
public abstract class Figure {

	public abstract int getArea();
}

public class Square extends Figure {
	
	public int getArea() {
	// calculates area
	}
}
public class Circle extends Figure { 
	
	public int getArea() {
	// calculates area
	}
}
{% endhighlight %}

PrintToScreen and the other classes are not related, but the other classes would like to follow the same algorithm to print to screen. So an interface relationship works here.

{% highlight java %}
public interface PrintToScreen {


	public boolean screenEmpty();
	public void draw();
}

public class Square extends Figure implements PrintToScreen {
	
	public int getArea() {
	// calculates area
	}

	public boolean screenEmpty() {
	// implements screenEmpty()
	}

	public void draw() {
	// implements draw()
	}
}

public class Windows implements PrintToScreen {
	
	// do stuff

	public boolean screenEmpty() {
	// implements screenEmpty()
	}

	public void draw() {
	// implements draw()
	}
}

public class Browsers implements PrintToScreen {
	
	// do stuff

	public boolean screenEmpty() {
	// implements screenEmpty()
	}

	public void draw() {
	// implements draw()
	}
}

public class CatPictures implements PrintToScreen {
	
	// do stuff

	public boolean screenEmpty() {
	// implements screenEmpty()
	}

	public void draw() {
	// implements draw()
	}
}
{% endhighlight %}
###Other Differences and Similarities###
<table width="100%">
<tbody>
<tr>
<th width="50%"><strong>Abstract Class</strong></th>
<th width="50%"><strong>Interface</strong></th>
</tr>
<tr>
<td>inherited by subclasses</td>
<td>implemented by classes</td>
</tr>
<tr>
<td>contains abstract, public, private, protected, etc.</td>
<td>contains abstract and public only</td>
</tr>
<tr>
<td>can implement some methods</td>
<td>cannot implement any methods</td>
</tr>
<tr>
<td>can contain fields</td>
<td>cannot contain fields</td>
</tr>
<tr>
<td>cannot instantiate directly</td>
<td>cannot instantiate directly</td>
</tr>
<tr>
<td>class can only inherit one abstract class</td>
<td>class can implement multiple interfaces</td>
</tr>
</tbody>
</table>
  
<br />
So if an abstract class has only public/abstract methods and no fields, it would be the same as an interface, EXCEPT that classes can implement any interfaces, but only inherit one class (abstract or not), and the relationship between them I talked about earlier.