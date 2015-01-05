---
layout: post
title:  "Typecasting"
date:   2014-09-04 03:24:54
categories: update
---


Typecasting
----------------------------------------------

One of the major pains about programming is that numbers and strings (and other things too, I suppose) are not the same. But, sometimes you will have something that is a string that you would prefer, really, to be a number. In order for this to happen you need to tell the computer to make that change. This process is called **typecasting**. Here are a few ways of going about it in typescript.


Number to string
------------------------------------------------

{% highlight javascript %}
var meaningOfLife:number = 42;
var stringOfLife = meaningOfLife.toString();
{% endhighlight %}


(Yes, put a .toString() at the end of a variable to turn it into a stringy version of itself)

String to Number
--------------------------------------------

{% highlight javascript %}
var pie:string = "3.14159";
var pi:number = parseFloat(pie);
var easyPi:number = parseInt(pie);
{% endhighlight %}



There are two methods to turn a string into a number:

	- parseInt will round to a *whole number*
	- parseFloat will turn it into a decimal number


Other objects
--------------------------------------------

There are other objects in typescript as well that are not the base type. To typecast them we put the name of the type in <> in front of the object, like so:


{% highlight javascript %}
    var xinput:HTMLInputElement = <HTMLInputElement>document.getElementById('x');
{% endhighlight %}

