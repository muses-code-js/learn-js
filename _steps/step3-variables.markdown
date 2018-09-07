---
layout: step
number: 3
title: Variables
permalink: step3/

---

So now we know the basics about values, operations and expressions.

But so far we have only been able to write literal values.  We have needed to know what they will be ahead of time.  What if we don't know yet or if we expect them to change over time?  That's where variables come in.

**Variables** are named placeholders that represent a value.

To create a new variable you declare its name using the keyword `var`:

```javacript
var message;
```

This created a new variable with the name of `message`.

Variable names:

 * can contain letters, digits, underscores, and dollar signs.
 * must begin with a letter
 * are case sensitive (`message` and `Message` are different variables)
 * cannot be reserved words (eg. `var`)

Once you have created a variable, you **assign** a value to it using the **assignment operator** `=`.

```javascript
message = 'Hello There!';
```

You can also create and assign in a single statement:

```javascript
var message = 'Hello There!';
```

Assigning a value at the time of creation is sometimes called providing an **initial value** or **initialising** the variable.

 <!-- A variable with no value assigned contains the special value `undefined`.  `undefined` is not a string, it is a special type of it's own. -->

You can think of a variable as being like a labeled box that you put a value into, and then you can use that value by referring to the box by its label.

So for example you could change the `doStuff()` function like this:

```javascript
function doStuff(){
  var message = 'You clicked the button';
  document.getElementById('displayBox').innerText = message;
}
```

That's kind of an academic example though, it doesn't really demonstrate *why* you use variables.

Let's do a better one.

We're going to update the page so it has three buttons, labelled `Arrive`, `Leave`, and `Say`.
When you click on `Say` it will display a message that is saved in a variable.
Clicking on `Arrive` and `Leave` will change the message that is stored.

Let's create another page like this:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Learning JS workshop</title>
  </head>
  <body>
    <button id="arriveButton">Arrive</button>
    <button id="leaveButton">Leave</button>
    <button id="sayButton">Say</button>
    <pre id="displayBox"></pre>
  </body>
  <script>
    var message = "I don't know where you are!";

    function handleArrive(){
      message = 'Welcome!';
    }

    function handleLeave(){
      message = 'Farewell my friend!';
    }

    function sayStuff(){
      document.getElementById('displayBox').innerText = message;
    }

    document.getElementById('sayButton').onclick = sayStuff;
    document.getElementById('arriveButton').onclick = handleArrive;
    document.getElementById('leaveButton').onclick = handleLeave;

  </script>

</html>
```

In our JavaScript we have a variable called `message`.
`message` is what is displayed when we click on the `Say` button.
Clicking on either of the other buttons will assign a different value to `message`.

![Buttons](../assets/step-3a.png){:title="Buttons" class="img-responsive"}


Before going on to the next step, have a try at adding another button `Stay` which changes the message to `"Well, make yourself comfortable."`
