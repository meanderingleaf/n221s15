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
var resultOne:bool = 5 < 7; //true
var resultTwo:bool = 7 < 5; //false
{% endhighlight %}

Greater than
----------------------------------------------

{% highlight javascript %}
var resultOne:bool = 5 > 7; //false
var resultTwo:bool = 7 > 5; //true
{% endhighlight %}

Equal to
-----------------------------------------------

{% highlight javascript %}
var resultOne:bool = 5 == 5; //true
var resultTwo:bool = 7 == 5; //false
{% endhighlight %}

Not equal to
-----------------------------------------------

{% highlight javascript %}
var resultOne:bool = 5 != 5; //false
var resultTwo:bool = 7 != 5; //true
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

- With the code above, is there a chance the usere will _not_ see a final alert?

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
	console.log("Count have done better...")
}

{% endhighlight %}


A brief note about formatting
---------------------------------------------------------

- Note that every time a { appears, the next line is tabbed in
- And once that block exits with a }, the following lines are not longer tabbed in
- Get in the habit of doing this
	- Yes, it will be worth points


Animation
----------------------------------------------------------

Let's take a look at one of the functions in our code that we just.. glossed over before. The animate function. Technically it does a bit of voodoo behind the scenes so our eyes are going to remain semi-glossy as we continue working with it.

{% highlight javascript %}
	animate();
	function animate() {
	    renderer.render(stage);
	    requestAnimationFrame(animate);
	}
{% endhighlight %}

Actually let's stay far away from it. Edit it so it looks like this:

{% highlight javascript %}
	animate();
	function animate() {
		draw(); //new line
	    renderer.render(stage);
	    requestAnimationFrame(animate);
	}
{% endhighlight %}


Now we can make a draw function with the rest of our code and life will just be so much better. So. Let's animate.


{% highlight javascript %}
	function draw() {
		//get rid of our old drawing.
		drawing.clear();

		//draw our new stuff
		drawing.beginFill(0x000000);
		drawing.drawCircle(0,0,100);
	}
{% endhighlight %}

Okay, this is sorta boring. But now that we can clear the stage and redraw it becomes easy to get some animation into our program by changing the value of a variable outside of the scope of funcion and using that value to control the position of the circle.

{% highlight javascript %}

	var xPosition:number = 0;

	function draw() {
		//get rid of our old drawing.
		drawing.clear();

		//draw our new stuff
		drawing.beginFill(0x000000);
		drawing.drawCircle(xPosition,0,100);

		xPosition = xPosition + 1;
	}
{% endhighlight %}

Great, now we have a circle moving to the right. We'll come back to this a bit later to make it more.. fun. For now, let's use our if statements for a bit of easy drawing.


Getting mouse position
---------------------------------------------

Use stage.getMousePosition();

Store the result in a variable with type PIXI.Point.

{% highlight javascript %}

	var xPosition:number = 0;

	function draw() {
		//get rid of our old drawing.
		drawing.clear();

		//get the mouse position
		var mousePosition:PIXI.Point = stage.getMousePosition();

		//show mouse position on console
    	console.log(mousePosition.x, mousePosition.y);
	}

{% endhighlight %}



Using mouse position to control things on the screen
------------------------------------------------

CHanging color and position based on the x-position of the mouse.

{% highlight javascript %}

	var xPosition:number = 0;

	function draw() {
		//get rid of our old drawing.
		drawing.clear();

		//get the mouse position
		var mousePosition:PIXI.Point = stage.getMousePosition();

		if(mousePosition.x < 100 && mousePosition.y < 100) {
			drawing.beginFill(0xFF0000);
			drawing.drawRect(0,0,100,100);
		} else {
			drawing.beginFill(0x00FF00);
			drawing.drawRect(0,0,400,400);
		}
	}

{% endhighlight %}


Using complex conditionals to highlight corners
-----------------------------------------------

{% highlight javascript %}

	var xPosition:number = 0;

	function draw() {
		//get rid of our old drawing.
		drawing.clear();

		//get the mouse position
		var mousePosition:PIXI.Point = stage.getMousePosition();


		if(mousePosition.x < 100 && mousePosition.y < 100) { //upper left
			drawing.beginFill(0xFF0000);
			drawing.drawRect(0,0,100,100);
		} else if (mousePosition.x < 100 && mousePosition.y > 100 { //lower left
			drawing.beginFill(0x00FF00);
			drawing.drawRect(0,100,100,100);
		} else if(mousePosition.x > 100 && mousePosition.y < 100) { // upper right
			drawing.beginFill(0x00FF00);
			drawing.drawRect(100,0,100,100);
		} else if(mousePosition.x > 100 && mousePosition.y > 100) { // lower right
			drawing.beginFill(0x00FF00);
			drawing.drawRect(100,100,100,100);
		}
	}

{% endhighlight %}
