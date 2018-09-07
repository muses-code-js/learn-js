---
layout: step
number: 1
title: Setting Up
permalink: step1/
---


At lot of beginning workshops for Javascript start you with the very basics and only start doing the fun stuff (like messing around with page) at the end.

That's kind of boring, so we want to jump right in with the fun stuff.

So lets get started with a simple page that has a button and a box.

Then we are going to write some code that will make changes to the box when you click the button.

I'll describe what all of this does, and then in the following steps we will expand on those explanations and make it do more stuff.

Ready?  Lets go!

Create a new HTML file, call it whatever you want just so long as it has `.html` at the end, then add the following to it:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Learning JS workshop</title>
  </head>
  <body>
    <button id="actionButton">Click me</button>
    <pre id="displayBox"></pre>
  </body>
  <script>
    function doStuff(){
      document.getElementById('displayBox').innerText = 'You clicked the button!';
    }
    document.getElementById('actionButton').onclick = doStuff;
  </script>

</html>
```

Save it and open that file in your browser.

You should see your button.

Now click on the button and you will see the text 'You clicked the button!' added to the page.

![Your very first Javascript](../assets/step-1a.png){:title="Your very first Javascript" class="img-responsive"}

[INSERT BRAIN EXPLODING GIF]

So what just happened here?

The file is mostly straight forward HTML.

When the page loads in the browser, the browser reads the HTML file, and draws the HTML elements as it finds them in the file.  

Until it hits the `<script>` tag.
When that happens it pauses drawing the page and runs the instructions in the `<script>` tag.
Once it finishes that it continues drawing whatever page elements it finds after `<script>`.
That's the first way a browser runs Javascript code, when it finds a `<script>` tag when loading the page.

What happens in our `<script>` tag?

We did two things.  

First, it created a function which we named `doStuff`.  That function gets the element on the page with the ID of `displayBox` and set the text in that element to be `You clicked the button!`.  `document` and `getElementById` are parts of the DOM API.  A function is a way of creating some code to run later.

Then, it found the element with the element with the ID of `actionButton` and told the browser that when that element gets clicked on it should run the function `doStuff`.

So then when you click on the button, the text changes on the page.  

That is the second time that Javascript code runs: when something happens, called an `event`, that has a Javascript function attached to it.

This is called event-driven programming, and it is how programs in Javascript are structured.

Almost everything that happens in the browser triggers an event. Think of an event as an announcement from Javascript that a specific thing happened. When the page loads, when you scroll, when you click on something, all these things and many more cause the browser to create events.

When we write Javascript, we tell the browser what instructions (functions) to run when different events happen.

So now we have something to work with lets dig into the basics of Javascript.
