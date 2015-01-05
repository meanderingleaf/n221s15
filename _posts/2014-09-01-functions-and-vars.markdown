---
layout: post
title:  "Functions and Variables"
date:   2014-09-02 02:24:54
categories: update
---

***Functions and Variables***

Okay, let's talk about the building blocks of code: functions and variables.

**Variables**
-------------------------------

Variables store values. That is it. (Values, of course, can be a lot of things, from numbers to graphics).

*To make a variable*

Type the keyword `var`, the name of the var, a *colon*, and then a *variable type*.

{% highlight javascript %}
var myVar:any;
{% endhighlight %}

__Putting stuff into variables__

Use the **equals sign (=)**

{% highlight javascript %}
var something = 'Hello';
something = 'Goodbye';
{% endhighlight %}

(In thise case, the final value of the variable `something` will be 'Goodbye')

__Variable Types__

We're going to be working with three major variable types, to begin with, but you will quickly see that there is a plethora of variables out in the *Real World*.

All of your variables in this class *must have a type*. A type defines what the variable is. In order to specify a type, you write the name of the type after the colon. For instance, to make a variable a number type, we would write this:

{% highlight javascript %}
var showingTypes:number;
{% endhighlight %}

*Numbers*
----------------------------

These store.. numbers.

{% highlight javascript %}
var first:number = 10;
{% endhighlight %}

All sorts of numbers

{% highlight javascript %}
var another:number = 5.66;
var pewPew:number = 1000000000000000;
var yougetthepoint:number = 0.45;
{% endhighlight %}


*Strings*
-------------------------------------

{% highlight javascript %}
var another:string = 'Hello world!';
{% endhighlight %}

*A note on strings* in order to write strings in code you *must use* either the double quotes "  or single quote ', opening and closing the string with the same for the whole string.

Strings made in code like this are called **string literals**.

(The reason there are two types of quotes? So you can have quotes in quotes:'"Hello!" she said.'  is a valid string)

*Booleans*
----------------------------------

Store **true** or **false**.

{% highlight javascript %}
var isCold:Boolean = false;
var isWarm:Boolean = true;
{% endhighlight %}


Operands
------------------------------

You can do more with variables than just assign single values.

{% highlight javascript %}
var a:number = 4;
var b:number = 2;

//addition
var c:number = a + b; //6

//subtraction
var d:number = a - b; // 2

//multiplication
var e:number = a * b; //8

//division
var f:number = a / b; //2

//modulo
var g:number = a % b; // 0
{% endhighlight %}

Modulo
------------------------------

Also Known As "remainder"
The part left over after division

{% highlight javascript %}
7 % 3 //1
12 % 10 //2
{% endhighlight %}

Question
------------------------------

Let's say I have a variable `myVar` and I want to subtract 2 from it, and store that value back into the variable?

How do I do that?

Incrementing/Decrementing
------------------------------

{% highlight javascript %}
var a:number = 5;

//incrementing
a = a + 1; //a == 6

//decrementing
a = a - 3; //a == 3

//multiplenting? (this and the next are not real words I just thought they were funny)
a = a * 2; //6

//divisiplexing?
a = a / 3; //2
{% endhighlight %}

Incrementing/Decrementing/other shorthand
-----------------------------

{% highlight javascript %}
var a:number = 5;

//incrementing
a += 1; //a == 6

//decrementing
a -= 3; //a == 3

//Multiplication
a *= 2; //6

//Division
a /= 3; //2
{% endhighlight %}

String Concatenation
------------------------------

One can also use the plus sign to add strings together. This is called **String concatenation**.

{% highlight javascript %}
var first:string = "Hello";
var last:string = "World";
var else:string = first + last; //'HelloWorld';
{% endhighlight %}

Question - why no space between the hello and world in the result?

Logging
---------------------------

Logging lets you see the value of variables in the developer console. Here's an example:

{% highlight javascript %}
var someVar:string = "Hello";
console.log(someVar);
{% endhighlight %}

If we open up the chrome developer console (our developer console of choice), we will see the string "Hello" on one line of it.

Functions
------------------------------

Functions are a way to package up a block of code to run at a later time.
They code inside their curly brackets is not used until they are **called**, **invoked**, **run** (these are all terms I may or may not use in class)

**Here is a function**

{% highlight javascript %}
function sayHello() {
	console.log("Hello");
}
{% endhighlight %}

This function will, when used, output some text to our lovely developer console.

**Here's how to run that function**

{% highlight javascript %}
sayHello();
{% endhighlight %}

If you put it all together, it looks like this

{% highlight javascript %}

function sayHello() {
	console.log("Hello");
}

sayHello();

{% endhighlight %}

This is a good point to write your own, similar function, and call it
------------------------------------------------------------------------

Function arguments
--------------------------------------

- Functions are machines, and, like some machines, can take inputs (called **arguments**)
- Arguments become variables inside of the functions

**Argument Example**

{% highlight javascript %}
function sayHelloName(name:string) {
	//name is now a variable in this function
	//we can do anything we want with it

	//even something boring like say hello to the name
	console.log("Hello " + name + "!");
}
{% endhighlight %}

Calling a function with arguments
-----------------------------------------

- Provide the argument inside of the parenthesis

**Using our sayHelloName function**

{% highlight javascript %}
sayHelloName("Todd");
{% endhighlight %}

Multiple arguments
-------------------------------------------

- Functions can take multiple arguments
- Put a comma between each argument

{% highlight javascript %}

//the function
function sayHelloSalutation(salutation:string, name:string) {
	console.log(salutation + " " + name +"!")
}

//calling the function
sayHelloSalutation("What's up", "Dan");

{% endhighlight %}

Now is a good time to make a similar function to the one above and call it
--------------------------------------------

Don't you think?


Function returns
-------------------------------------------

Functions can also return values. Here's a simple example

{% highlight javascript %}
function makeHello() {
	var aString = "hello";
	return aString;
}


//use the function
var aHello = makeHello(); //a hello now contains 'hello'
//this would do the same thing as above
var aHello:string = "Hello";
{% endhighlight %}

Complex function usage
---------------------------------------------

{% highlight javascript %}
//our function
function generateHello(salutation, name) {
	var sal = salutation + " " + name +"!";
	return sal;
}

//use the function

var ourHello:string = generateHello("Hey there", "Dave");
console.log(ourHello);
{% endhighlight %}

Scope
----------------------------------------------

Now that we have functions, we need to start worrying about **variable scope**

**Variables created inside a function (with the var keyword) are not useable outside of that function**

**But** variables created outside of that function are.

{% highlight javascript %}
function myFunc() {
	var awesomeVariable:string = "Pretty cool";
}

function myOtherFunction() {
	console.log(awesomeVariable); //won't work
}


console.log(awesomeVariable); //won't work
{% endhighlight %}

{% highlight javascript %}
var awesomeVariable:string = "Pretty cool";

function myFunc() {
	console.log(awesomeVariable); //will work
}

function myOtherFunction() {
	console.log(awesomeVariable); //will work
}


console.log(awesomeVariable); //will work
{% endhighlight %}

Getting Input
--------------------------------------------------

Input is great! If only we all spent more time listening and less time talking (and here I am, talking away).

Here's the most basic way to get input from the user: an input (it actually becomes a **textfield** but close enough).

{% highlight html %}
<input id="userName" />
{% endhighlight %}

(Take note of that ID we'll be using it soon)

Now let's make another input tha's a bit more.. interactive. A **button**

{% highlight html %}
<input type='button' onclick='getUsername()' />
{% endhighlight %}

Okay, great. Let's finish this up. *Assuming we have both of these on the screen* we can add this to our javascript file:

{% highlight javascript %}
function getUsername() {
	var username = document.getElementById('userName').value;
	console.log(username);
}
{% endhighlight %}

Two things here:

*document.getElementById* will get any element on the screen with an ID that you pass in as an argument.
*.value* will get the value of any input element, if it has one.


Showing output
-------------------------------------------------------

Add a tag with an ID, like so

{% highlight html %}
<div id='output'></div>
{% endhighlight %}

Inside any function, change its *innerHTML*

{% highlight javascript %}
var output = document.getElementById('output');
output.innerHTML = "Hello!";
{% endhighlight %}