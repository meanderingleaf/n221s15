---
layout: post
title:  "Drag and Drop"
date:   2014-11-14 03:24:54
categories: update
---



Drag and drop
------------------------

Dragging and dropping in html comes in a combination of three events, and at least two objects. Here's a brief walkthrough of it.


The (base) markup
-----------------------

{% highlight html %}
	<div id="draggie" draggable="true">DRAG ME</div>
	<div></div>
{% endhighlight %}


The **draggable="true"** makes any dom element draggable.

The css
-----------------------

{% highlight css %}
	[draggable] {
	  user-select: none;
	}
	
	div { width: 100px; height: 100px; background-color: #ff0000; }

	#draggie {
		background-color: #00FF00; 
	}
{% endhighlight %}

Seting user-select:none; on any draggable element stops the browser from doing things like selecting text or images when they try to drag the element around. (It also disables selection of things within the element, so be careful of text users might want to copy, etc...)


Go ahead and try to drag that top one
-------------------------------

Whoooo!

The markup with the event listeners
-------------------------------

{% highlight html %}
	<div id="draggie" draggable="true" ondragstart="handleDragStart(event)">DRAG ME</div>
	<div ondrop="handleDrop(event)" ondragover="handleDragOver(event)"></div>
{% endhighlight %}

We're using three event listeners here (and yes, we could also do them in code by removing the 'on' for the string name of the evnt in an 'addEventListener' call)

1. dragstart: This event fires when the user starts to drag the element.
2. dragover: This event fires on an element when something is dragged **over it**.
3. drop: Fired when something is dragged over and **then dropped** on an element


handleDragOver
-------------------------------

{% highlight javascript %}
function handleDragOver(e) {

  if (e.preventDefault) {
    e.preventDefault(); // This has to be here. Without it we won't get a drop event to fire.
  }

  return false;
}
{% endhighlight %}

The *e* in the event argument, and function, is just a typical shortening of the word *event*.

**Prevent default** is another method of the event object. It simply stops the event from doing whatever it does normally. For instance, if one were to prevent the default of a click on a link, the page would not navigate to the next page.

dragStart
---------------------------------------

{% highlight javascript %}

var dragSrcEl = null; //to keep a reference to the thing being moved.

function handleDragStart(e) {
	dragSrcEl = e.target; //store a reference to the thing being moved
	e.dataTransfer.setData('text/html', e.target.innerHTML); //Used to tell the browser *what* is being dropped.
}
{% endhighlight %}


Outside of drag start (and any other function), we make a variable that will keep a reference to the thing being moved. We will get back to this in the drop functions.

The second part of this function, that begins with "e.dataTransfer" is a way to tell the browser, when you drop the object, what is being dropped. Modern browsers can accept lots of things to be dropped (such as dropping images onto a site to upload them), so you need to let the browser know precisely what you are dropping (that is what the "text/html" means).

drop
---------------------------------

{% highlight javascript %}
function handleDrop(e) {
  if (e.stopPropagation) {
    e.stopPropagation(); // Stops some browsers from redirecting.
  }

  //make sure the thing we're dopping onto isn't the thing we're dragging
  if (dragSrcEl != e.target) {
    // swap the html of the thing being dragged with the thing it was dropped onto
    dragSrcEl.innerHTML = e.target.innerHTML;
    e.target.innerHTML = e.dataTransfer.getData('text/html');
  }

  return false;
}
{% endhighlight %}

**e.stopPropagation** essntially makes sure the no other object also listens to and responds to this event.

We then swap the content inside of each div, by changing their innerHTML (e.target, in this case, is the thing being dropped on to).

Secondly, we set the drop target's HTML to the data being transferred (which, looking up to our start drag function, is the innerHTML of the thing being dragged)