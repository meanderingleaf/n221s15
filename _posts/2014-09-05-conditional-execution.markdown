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

	    requestAnimationFrame(animate);
	}
{% endhighlight %}

Okay, this is sorta boring. But now that we can clear the stage and redraw it becomes easy to get some animation into our program by changing the value of a variable outside of the scope of funcion and using that value to control the position of the circle.

(this assumes we have our 'fillCircle' function in the script as well.)

{% highlight javascript %}

	var xPosition = 0;

	animate();
	function animate() {
		//get rid of our old drawing.
		ctx.clearRect(0, 0, canvas.width, canvas.height);

		//draw our new stuff
		ctx.fillStyle = "#FF0000";
		fillCircle(xPosition,0,100);

		xPosition = xPosition + 1;
		requestAnimationFrame(animate);
	}
{% endhighlight %}

Great, now we have a circle moving to the right. We'll come back to this a bit later to make it more.. fun. For now, let's use our if statements for a bit of easy drawing.


Using buttons to control an animated drawing
---------------------------------------------

First, the HTML

{% highlight html %}
<input type="button" id="btnLeft" value="left" /> <input type="button" id="btnRight" value="right" />
<canvas id="myCanvas" width="800" height="600"></canvas>
{% endhighlight %}


Then, the Javascript

{% highlight javascript %}
	var xPosition = 0;

	document.getElementById('btnLeft').onclick = function() {
		xPosition -= 10;
	}

	document.getElementById('btnRight').onclick = function() {
		xPosition += 10;
	}

	animate();
	function animate() {
		//get rid of our old drawing.
		ctx.clearRect(0, 0, canvas.width, canvas.height);

		//draw our new stuff
		ctx.fillStyle = "#FF0000";
		fillCircle(xPosition,0,100);

		xPosition = xPosition + 1;
		requestAnimationFrame(animate);
	}
{% endhighlight %}


Using if statments with the animation
---------------------------------

Let's change the drawing so its got different colors based on the side its on.
We're going to focus on only the drawing portion of the code, this time.

{% highlight javascript %}
function animate() {
	//get rid of our old drawing.
	ctx.clearRect(0, 0, canvas.width, canvas.height);

	//draw our new stuff
	if(xPosition < 400) {
		//red on left
		ctx.fillStyle = "#FF0000";
	} else {
		//blue on the right
		ctx.fillStyle = "#0000FF";
	}
	fillCircle(xPosition,0,100);

	xPosition = xPosition + 1;
	requestAnimationFrame(animate);
}
{% endhighlight %}


Some challenges
-------------------------------

How do you change the above code so:
	1. The circle is colored green on the middle on the screen (between 300 and 500)
	2. The circle can up and down
	3. Once the circle can go up and down, how does the code change so the circle is different colors in the four quadrants?