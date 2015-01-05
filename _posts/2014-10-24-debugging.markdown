---
layout: post
title:  "Debgugging"
date:   2014-10-24 03:24:54
categories: update
---


Debugging
======================================

By now you have probably encountered some bugs in your application. Here's a few tips and pointers on how to get your programing back to 'working'.


Types of bugs
-----------------------------

1. Syntactical
	
	You typed something wrong. 

2. Logical
	
	You think the application should be doing one thing, when, actually, its doing something else entirely.

The developer console
----------------------------

In this class you should *always* have the developer console open. In chrome its under tools->javascript console.

Fixing syntatical bugs
-----------------------------

Firstly, you need to memorize syntax or have a reference if you're not confident you have it memorized.

1. Check the developer console for the error. It will be in red. The error report will give you the exact line to look at. (You can also click on the line number on the far right to be taken (usually) to the line of code)
3. Attention to detail (this comes with time)
4. Make sure to look through *all your code*. Oftentimes your error will come from lines before where the exact error is reported.
5. **Indent your code correctly** 

Common syntactical errors:

1. Opened a curly brace and did not close it in the right location. Look through your code and count opening and closings.
2. Opened a string and did not close it. This is highly apparent in an editor because all your subsequent code will be highlighted like a string.
3. Missing a closing or opening parenthesis around a loop or logical statment
4. Forgetting an equals sign in variable assignment.
5. Using a comma instead of a semi-colon inside of a for loop

Fixing logical bugs
---------------------------

**Mitigation**

Pseudocode

Using comments, write out **in eglish** the steps your application needs to go through. Here is an example.

{% highlight javascript %}
	//get a reference to the input on the stage

	//get the value typed into that input

	//convert that value to a number

	//get 10% of that number, store in a vriable
{% endhighlight %}


**Fixing**

1. Think like the computer
	Take each action *one step at a time*
	Ask yourself, "What happens here.. where does this lead?"
	If need be, comment out subsequent lines of code so it only goes as far as you are thinking
2. Console.log
	Use console.log to check the value of variable throughout your code.
	This can also be used to **check if a certain bit of code is reached/running**
3. Comment out as much as possible
	Go line by line if need be
	Make sure **each step is working**


Remember
--------------------------

Debugging is an iterative process. You will often fix errors just to encounter new ones. Don't get frustrated - every error fixed gets you closer to working.