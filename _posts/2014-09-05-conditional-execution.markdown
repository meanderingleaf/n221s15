---
layout: post
title:  "Conditional Execution"
date:   2014-09-05 03:24:54
categories: update
---


Logic
---------------------------------------------

- The building blocks of interactivity
- Computers can do basic logical checks
	- Greater than / greater than or equal to
	- Less than / less than or equal to
	- Equal to
	- Not equal to

- These checks all turn out to be **true** or **false**

Less than
---------------------------------------------

{% highlight javascript %}
var resultOne = 5 < 7; //true
var resultTwo = 7 < 5; //false
{% endhighlight %}

Greater than
----------------------------------------------

{% highlight javascript %}
var resultOne = 5 > 7; //false
var resultTwo = 7 > 5; //true
{% endhighlight %}

Equal to
-----------------------------------------------

{% highlight javascript %}
var resultOne = 5 == 5; //true
var resultTwo = 7 == 5; //false
{% endhighlight %}

Not equal to
-----------------------------------------------

{% highlight javascript %}
var resultOne = 5 != 5; //false
var resultTwo = 7 != 5; //true
{% endhighlight %}

The if statement
-----------------------------------------------

- Only runs a **block of code** if something is true

- A block of code is anything inside of *curly brackets* { }

- An example:

{% highlight javascript %}
if(true)
{
	//this code runs
}
{% endhighlight %}

Else
-----------------------------------------------

- The else statement only runs if the thing within the if statement is **false**

{% highlight javascript %}
if(4<5) {
	alert("All is right with the world.");
}
else
{
	alert("Something has gone terribly wrong");
}
{% endhighlight %}


Confirms
---------------------------------------------------

These are awful. Never use them in real development. And yet, for our purposes here, they can be useful.

In short, using the confirm method in JavaScript pops up a window that displays some text and lets the user respond with a *yes* or a *no*.

This response turns into a boolean **true** or **false**.

{% highlight javascript %}
var yesOrNoHmmm = confirm("Yes or no?");

console.log(yesOrNoHmmm); //will be either true or false
{% endhighlight %}


Nesting conditionals
----------------------------------------------------

- It is entirely possible to have if statements within if statements

{% highlight javascript %}
//get user's input if they want to read a book
var readAbook = confirm("Do you want to read a book?");
var doHomework = confirm("Do you also want to do you homework?")

if(readABook == true)
{
	//if the user wants to read a book
	if(doHomework==true)
	{
		//if the user wants to do their homework
		alert("Excellent!");
	}
}
else
{
	//if the user does not want to read a book
	alert("Your mind will rot!")
}
{% endhighlight %}


Quick question
--------------------------------------------------------

- With the code above, is there a chance the user will _not_ see a final alert?

Logical operators
--------------------------------------------------------

- The previous example can be simplified down a bit using **logical operators**

{% highlight javascript %}
&& //('AND')
|| //('OR')
{% endhighlight %}

How the logical operators work
--------------------------------------------------------

- looks for a true/false one either side
- Turns into a single true/false

{% highlight javascript %}
true 	|| false 	// true
true 	|| true 	// true
false	|| false 	// false

true 	&& true		// true
true 	&& false	// false
false	&& false	// false
{% endhighlight %}

Simplifying our previous if/else statement
--------------------------------------------------------

{% highlight javascript %}
//get user's input if they want to read a book
var readAbook = confirm("Do you want to read a book?");
var doHomework = confirm("Do you also want to do you homework?")

if(readABook == true && doHomework == true)
{
	//if the user wants to read a book AND do their homework
	alert("Excellent!");
}
else
{
	//if the user does not want to read a book
	alert("Your mind will rot!")
}
{% endhighlight %}

Else if
--------------------------------------------------------

Else ifs will only run if the previous if does not evaluate to true.
They come after a closing curly bracket, and you can have also many as you want.


{% highlight javascript %}

var grade:number = 85;

if(grade >= 90) {
	console.log("Hooray.");
} else if (grade >= 80) {
	console.log("good enough.");
} else if (grade >=70) {
	console.log("I am avergae.");
} else {
	console.log("Count have done better...");
}

{% endhighlight %}


A brief note about formatting
---------------------------------------------------------

- Note that every time a { appears, the next line is tabbed in
- And once that block exits with a }, the following lines are not longer tabbed in
- Get in the habit of doing this
	- Yes, it will be worth points
