---
layout: step
number: 5
title: Array
permalink: step5/
---

Having variables to hold your strings and integers is cool and all but what if we don’t know how many we will need?  
What if that number is going to change as the program is used?

Having to keep track of lists of information of varying and changing length is pretty common in software, and Javascript provides a special value type for just this purpose: arrays.

Arrays are a special type of object (see later for more about objects) which contain an **ordered list** of values.
Instead of just one value, an array can contain many.

Arrays are one of several types which are sometimes referred to as **collections**.

Lets create a simple page that lets us display a list of names that we can add to.

First lets create a page with our HTML elements:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Learning JS workshop</title>
  </head>
  <body>
    <input type="text" id="newName" placeholder="Type name to add here" />
    <button id="buttonA">Add</button>
    <div id="nameCount"></div>
    <div id="nameList"></div>
  </body>
  <script>

  </script>
</html>
```

This gives us a box to type a new name into, a button to click to add the name, and two divs: one to display the list of names and the other to show us the number of names.

[INSERT SCREENSHOT]

So now within our `<script>` tag we do the following ...

## Creating an array

An empty array can be created with just two square brackets.

Add this line to the start of our script to create our empty array and assign it to the variable `names`:

```Javascript
var names = [] ;
```

You can create an array with elements already in it by include a comma separated list of them inside of the brackets.

```Javascript
var names=[“Jessica”, “Helen”];
```

For our example just leave the starting array empty to start with.

## Adding to our Array

When our `Add` button is clicked we want to add the name in the box to the end of our array.

First lets create our function that will be responding to the `click` and assign it to the event.

```javascript
function handleAddName(){

}

document.getElementById("buttonA").onclick = handleAddName;
```

Now within `handleAddName` we want to get whatever is in the text input and add it to the end of our `names` array.

```javascript
var name = document.getElementById('newName').value;
names.push(name);
```

`push()` is a function which is attached to all arrays.
It's called a property.  Arrays have a whole bunch of useful properties that we can use.  We will learn more about objects in the next few steps after this one.

Now we have our updated array we want to display a list of them and the count of how many there are.  

To get our single string list, we will use the `join()` property.  `join()` takes all the elements of the array and concatenates all the elements together as one string.

To get the number of elements we will use the `length` property.  This property isn't a function like the previous two, it's a number value.

Add the following code to `handleAddName`:

```javascript
document.getElementById('nameList').innerText = "The names are: " + names.join(', ') + ".";
document.getElementById('nameCount').innerText = "There are " + names.length + " names.";
```

Now open the page up and try adding some names:

[INSERT SCREENSHOT]

Cool.

You might notice however that we have a few minor issues with our page though.

1. You can add an empty name, and that looks weird.
2. If you only have a single name it says “There are 1 names.”  We probably want it to say “There is 1 name.”

We could use conditions to fix these up.  Give it a try before going onto the next step.

Hints:

1. `if (name === ‘’)`
2. `if (names.length === 0)`

One possible solution:

```javascript
  <script>
    var names=[];

    function handleAddName(){
      var name = document.getElementById('newName').value;
      if(name !== ''){
        names.push(name);
      }

      var countMessage = '';
      var namesListMessage = '';

      if (names.length === 0){
        countMessage = "There are no names.";
      }
      if (names.length === 1){
        countMessage = "There is 1 name.";
        namesListMessage = "The name is: " + names[0] + ".";
      }
      if (names.length > 1){
        countMessage = "There are " + names.length + " names.";
        namesListMessage = "The names are: " + names.join(', ') + ".";
      }
      document.getElementById('nameCount').innerText = countMessage;
      document.getElementById('nameList').innerText = namesListMessage;
    }

    document.getElementById("buttonA").onclick = handleAddName;

  </script>
```
