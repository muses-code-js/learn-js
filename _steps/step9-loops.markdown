---
layout: step
number: 9
title: Loops
permalink: step9/
---


We often want to repeat specific steps in our programs at certain times.

And we don't always know exactly how many times.

We call this **looping** and there are many different ways to do it.

We are going to look at the `for` loop.

## The `for` loop

The `for` loop is used to repeat steps with a counter.  

Let's create a new page where you specify a message and a number and the message gets displayed that number of times.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Learning JS workshop</title>
  </head>
  <body>
    <input type="text" id="theMessage" placeholder="What message?"/>
    <input type="text" id="howMany" placeholder="Repeat how many times?"/>
    <button id="goButton">Go</button>
    <pre id="displayBox" />
  </body>

  <script>
  function showMessage(){
    var howManyTimes = document.getElementById('howMany').value;
    var message = document.getElementById('theMessage').value;

    var output = '';
    for(var i=1;i<=howManyTimes;i++){
      output = output + i + ' : '+message+'\n';
    }
    document.getElementById('displayBox').innerText = output;
  }
  document.getElementById('goButton').onclick = showMessage;
  </script>

</html>
```

Try it out.

Note that if you type in a number greater than about 10000 you will probably start to notice a slow down.  At about 30000 you should see a noticeable pause of about a second or two before the page updates.

Even though each time through the loop only takes a tiny fraction of a second, doing that 10s of 1000s of times quickly starts to add up.

Let's look at the loop in more detail:
```javascript
for(var i=1;i<=howManyTimes;i++){
  output = output + message+'\n';
}
```

There are two main parts:

1. The loop declaration, `for(var i=1;i<=howManyTimes;i++)`

  The loop declaration looks a bit like a function invocation,  but it isn't.  It defines how the loop will behave.

2. The loop statement block.

  The statement block is the steps to perform each time the loop repeats.

The declaration has the `for` keyword and three semicolon separated expressions inside the parentheses to define it.  

1. The first expression is the initialiser:`var i=0`

  This is run before the loop starts and is used to setup anything we need to track the loop.

  In this case, we create a counter to track how many times the loop as run.

2. The second expression is the condition: `i<=howManyTimes`

  This is evaluated at the beginning of each loop and the statement block only runs if it evaluates to `true`.  If it is `false` the block doesn't run and the loop ends.  

  So for our example it means that while the value of `i` is less than or equal to `howManyTimes` the loop continues.
3. The third expression is the final expression.  This is performed after each time the statement block runs.

In our loop block we are concatenating the message and the loop counter variable to the variable `output` each time.

Then after the loop we update the content of `'displayBox'` with the accumulated output.

Do you think you could change the for loop above so it counts down from `howManyTimes` to `1`?  Give it a try.

### Why so slow?

If you supply a large number like `32000` it takes several seconds to complete the loop and update the page.

But what if put the code to update the page *in* the loop?

What if we changed it like this?  Give it try.

```html
<script>
function showMessage(){
  var howManyTimes = document.getElementById('howMany').value;
  var message = document.getElementById('theMessage').value;

  var output = '';
  for(var i=1;i<=howManyTimes;i++){
    output = output + i + ' : '+message+'\n';
    document.getElementById('displayBox').innerText = output;
  }
}
document.getElementById('goButton').onclick = showMessage;
</script>
```

Unfortunately it doesn't work. Why?

The page can only be actually redrawn when Javascript isn't running.  It doesn't matter how many times you tell Javascript to do it, it just relays those instructions to the browser and the browser has to wait until Javascript has finished until it can actually redraw the page.  

It's a little more complicated than that, but the if you have code that takes a long time to run then the page cannot update, nor can anything else happen.  So try to avoid long loops. :wink:

### Other types of loops

There are a few different types of loops and most of them repeat actions either a number of times,  until a condition is met, or while a condition remains true.

However there are also loops which are related to performing actions for properties of variables.  We will see one of these when we talk about arrays.
