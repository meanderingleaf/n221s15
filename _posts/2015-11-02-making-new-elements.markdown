---
layout: post
title:  "Making New Elements"
date:   2015-11-03 03:24:54
categories: update
---


Adding new elements
------------------------------------

Sometimes when creating webpages, one may desire to put new content onto the page. One way to accomplish this is via updating innerHTML with the tags you want to add.


{% highlight javascript %}
dvOutput.innerHTML = “<h1>You won!</h1><button>Play again</button>”;
{% endhighlight %}


This is an entirely acceptable approach. The major issue is that, with the above code, how would you add an event listener to the button to actually play again? You would need to 1) put an id on the button 2) select that button via document.querySelector 3) attach the event handler.

Honestly, it would be better if you could just attach the event handler ahead of time, and customize the element before it appeared on the screen


Creating elements
----------------------------

It is also possible to create new DOM elements inside of javascript, before ever having them be visible to the user. This lets you do things like customize their classes and styles, and add event handlers to them, before the user can interact with them.

It also is the first step towards making your applications more dynamic, because many applications do not come with all their elements already created on the page before it runs.

In order to create new elements inside of your scripts, use document.create element(). This is a method that takes one argument, a string name of a valid HTML tag.

{% highlight javascript %}
var myNewDiv = document.createElement(‘div’); //makes a new div element
var myButtonSpot = document.createElement(‘button’); //makes a new button
var someNewPost= document.createElement(‘p’); //makes a new paragraph
{% endhighlight %}

Now, once you make an element, it is not yet visible on the screen.



Adding new elements to the DOM
-------------------------------------

With an element created, the next step is to add that element to the page. This is a two step process.

Get a reference to a DOM element that is already visible to the user
Use appendChild to take your not-currently-showing element, and add it as a child to your referenced element

Assuming some markup on your page like this:

{% highlight html %}
<div id=”buttonBox”></div>
{% endhighlight %}

You could then get a reference to the button box, and add a brand new button to it, by following these steps

{% highlight html %}
//get rerfence
var dvButtonBox = document.querySelector(“#buttonBox”);

//create element, add to the button box div
var newButton = document.createElement(“button”);
dvButtonBox.appendChild(newButton); //now you can see the button!
{% endhighlight %}


Styling newly created elements
------------------------------------

Anything you create with document.createElement is the same thing as a the dom references that are found via document.querySelector. This means you can style them via the “style” property.

{% highlight javascript %}
var newDiv = document.createElement(“div”);
newDiv.style.height = “100px”;
newDiv.style.width = “100px”;
newDiv.style.backgroundColor = “#FF0000”;
{% endhighlight %}


Adding events to newly created elements
-----------------------------------------

Just like with styles, it is possible to add listeners to newly created elements, before they are added to the DOM.

{% highlight html %}
var newDiv = document.createElement(“div”);
newDiv.style.height = “100px”;
newDiv.style.width = “100px”;
newDiv.style.backgroundColor = “#FF0000”;
newDiv.addEventListener(“click”, clickReponse);

function clickResponse(event) {
    console.log(“How could you.”);
}
{% endhighlight %}


Putting it all together
----------------------------------------

Of course, the final question to this all is “why”. Perhaps my favorite example of this is is when you need to create a lot of elements that all work about the same. Here is an example that puts a bunch of elements on the screen that you can click to destroy.

{% highlight html %}
<div id=”itemBox”></div>
{% endhighlight %}


{% highlight javascript %}
var dvItemBox = document.querySelector(“#itemBox”);

for(var i = 0; i < 20; i++) {
    var newDiv = document.createElement(“div”);
newDiv.style.height = “100px”;
newDiv.style.width = “100px”;
newDiv.style.backgroundColor = “#FF0000”;
newDiv.addEventListener(“click”, clickReponse);
}

function clickResponse(event) {
    event.target.remove();
}
{% endhighlight %}
