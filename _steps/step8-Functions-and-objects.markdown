---
layout: step
number: 8
title: Functions and Objects
permalink: step8/
---

We’ve been using `document.getElementById` a lot in our examples and not talking about it.

`getElementById` is a property of the `document` object, but it is also a function that returns a value.

How can a object property be a function?

## Functions are values

Function declarations *are* a type of value.  

The major difference between functions and the other value types is that functions can be invoked.  Other types, like strings and numbers can’t be invoked.

Consider this code:

```javascript
function foxSound(){
	return "yow-wow-wow-wow";
}
var foxSays = foxSound;
console.log( foxSays() );
```

`foxSound` is a function, and `foxSays` is a variable.  

When we assign the function `foxSound` to the variable `foxSays`, `foxSays` is still a variable, but it is a variable that contains a function declaration.  Therefore it is also a function and can be invoked.

Note that when we assign `foxSound` to `foxSay` we do not invoke `foxSound`.  If we did that then it would be the return value of `foxSound` that would be assigned to `foxSay` not the function itself.  Very different.

This is how "assigning functions to events" works.  `getElementById` returns an Element object. This object represents a single HTML element in the page.  The event handler functions like `onclick` and `onchange` are just properties of that object and you can assign anything you want to them.  By default they are null.  When the event "fires" the browser checks if the appropriate property is null, and if it isn’t, it tries to invoke it.  If you had assigned something which isn’t a function then you will see an error in the console.

## Function Expressions

We can also create a function as a **function expression**

```javascript
var foxSays = function(){
	return "yow-wow-wow-wow";
}
```

Any place where you could use a function declaration in an expression, you can just declare a new function there.  

(FYI compared to many other languages this is pretty wild!).

You *can* include the function name in the expression like a regular declaration but there isn’t much point, because you won’t be able to refer to the function by the name.  Functions created this way are often referred to as **anonymous functions** for this reason.

Function expressions mean you can do this:

```javascript
document.getElementById("buttonA").onclick = function(){
	document.getElementById("message").innerText = "You clicked the button!"!
};
```

This is very handy as a means of simplifying your code for those cases where you need a function, but it is only ever going to be used in that one place.

## Functions as object properties

And obviously since we can assign functions to variables, we can assign functions as properties of objects.

This is what `getElementById` is, a property of `document`.

Here’s a silly example showing an object with functions assigned to it’s properties three different ways: a function declaration, a function expression assigned to a variable, and a function expression assigned straight to the property.

```javascript
var animalSounds = {
	cat: meow,
	dog: woof,
	duck: function(){ console.log("quack!"); }
}

function meow() { console.log("meow!"); }
var woof = function(){ console.log("woof!"); }

animalSounds.cat();
animalSounds.dog();
animalSounds.duck();
```

## Chaining Functions & Properties

So let’s look at some code we’ve used frequently:

```javascript
document.getElementById(‘buttonA’).onclick = someFunction;
```
This single statement has a lot going on.  

Because `document.getElementById(‘buttonA’)` returns an `Element` object we can immediately use that expression as though it was the `Element` object.  Remember when an invoked function returns a value, you can treat it like it is that value.

Joining multiple function invocations and property accessors together like this is sometimes called property or function chaining.  Sometimes it can make your code concise and easy to read, but sometimes it can be confusing.  Apply your judgement as to when it makes sense to you:

It is worth pointing out that it is also perfectly valid to write the above code as:

```javascript
var button = document.getElementById(‘buttonA’);
button.onclick = someFunction;
```

At the end of the day they both do the same thing.
