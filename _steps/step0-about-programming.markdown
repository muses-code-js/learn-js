---
layout: step
number: 0
title: About Programming
permalink: step0/
---

So before we jump in lets have a quick chat about what programming actually is.

We expect you already know some HTML & CSS but we don't really consider those things to be programming in the same way that we are going to talk about here.  They are more about document design and content.  Not that those things are less valuable, but they are different.

So what *is* programming?

## Todo lists for computers

You can think of programming as writing a todo list for a computer.  

A computer by itself doesn't do anything, you need to give it instructions to follow.

The problem is that computers are actually pretty dumb, they can't think or apply judgment.  They can't "get" what you mean.  They just do exactly what you say, for better or worse.  When they do make decisions it is only the choices that you have already provided instructions for.

And also they can't actually do very much, so each item in your todo list has to be very simple.

So what are the things you can tell the computer to do?

1. Remember a piece of information.
2. Perform a calculation with one or more pieces of information.
3. Compare pieces of information to choose what actions to perform next.
4. Repeat a set of actions a number of times.
5. Group sets of instructions together so they can be use like a single instruction.

And we refer to these things as:

1. variables
2. operations
3. conditionals
4. loops
5. functions

That's actually kind of it.

But what about displaying stuff on the screen?  Or reading and writing to files?  Or getting input from the user?  Or making a network request?  How do we do those things?

You do those things using functions that are included with the language.  

Most languages include a lot of functions that perform all sorts of tasks.  Under the hood, these functions still just do the same kind of stuff but with more direct access to the internal details.  Javascript hides many of these kinds of details away for security reasons.  

## Programming in the Browser

Web browsers provide a "standard library" of functions that we use to do all sorts of interesting stuff in Javascript.  

There are a lot of these, but the ones we are going to be using today are referred to as the Document Object Model API or DOM API. API stands for Application Programming Interface, which is just a fancy way of saying "some functions that let you interact with a program".

The DOM is what we refer to the representation of the page (the document) that we can see from Javascript.

The DOM API has functions that we can use to read from and write to the page.  This is how we will display information to the user and get information from them.

You can read about all the other functionality the browser provides here: [Web API](https://developer.mozilla.org/en-US/docs/Web/Reference/API).

Anyway now we know a little background lets get on with writing code.
