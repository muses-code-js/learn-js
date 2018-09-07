---
layout: step
number: 6
title: Objects
permalink: step6/

---

Now we can make lists of values.

But those values are still very simple, just strings and numbers etc.  
What about more complex things that cannot be adequately described in a single value?  
What if our app had to managed information about customers?  Or cats?

This is where **objects** come in.

Objects are variables that contain multiple variables.  Their purpose is to collect together multiple different values that each describe different aspects of the same thing.  These values are called the object’s properties.

Let’s create another page like the previous one, but instead of just keeping a list of names we will have a list of objects and display them in different ways.

For example a customer object might have a name, an address, a customer ID.

Objects can be created a few different ways but the easiest is to use **object literal syntax** to declare the object.

Here is a cat object:

```javascript
var cat = {
  name: 'Garfield',
  weight: 8.2,
  colour: 'orange',
  likes: 'lasagna',
  hates: 'Mondays'
};
```

This object, assigned to the variable cat, has five properties: 4 strings and one number.
To use the properties of an object you use **dot syntax**: object name DOT property name, eg. `cat.name`

You can use the properties of an object just like any other variable:

```javascript
cat.weight = cat.weight - 0.2;

console.log(cat.name + " really hates " + cat.hates);
```

If you try to read a property that doesn’t it’s value is `undefined`.

If you try to assign a value to a property that doesn’t exist it will create that property.

Javascript and the browser uses objects extensively.  Every element on the page and every event is represented by an object.  We will learn more about those next.
