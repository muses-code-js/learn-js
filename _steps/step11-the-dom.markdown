---
layout: step
number: 11
title: The DOM
permalink: step11/
---

## What is the DOM

DOM stands for Document Object Model.

When your webpage loads, the browser doesn't actually show you the HTML.  What it does is read through the HTML (parse it) and create a collection of objects that represent all the things in the page.  This collection of objects is the DOM and it is this that the browser is using to display the page.  

When you use Javascript to change parts of the page, you aren't changing the HTML, you are changing the DOM.

Open up any of the previous exercises (I'll use the one from step 1) and open the dev tools and go to the Elements tab (or the Inspector tab in Firefox).

![Elements/Inspector in DevTools](../assets/step-11a.png){:title="Elements/Inspector in DevTools" class="img-responsive"}


This tab shows you a representation of the DOM of the current page.  It will look pretty similar to your HTML.

If you interact with the page (as per whatever behaviour that exercise implemented) you will see the DOM update in the dev tools.  

![Updated DOM in DevTools](../assets/step-11b.png){:title="Updated DOM in DevTools" class="img-responsive"}


However if you right click in your page you will see a `View Source` or `View Page Source` on the popup menu.  Select this and a new tab will open with the original HTML source of the page.  Note that it can be different from the current state of the DOM.  It is the original HTML that was loaded to create the DOM initially.  Manipulating the DOM doesn't change this.

![View Source](../assets/step-11b.png){:title="Updated DOM in DevTools" class="img-responsive"}


Making changes to a page means manipulating the DOM of the page.

Usually this means selecting elements and then either manipulating their properties or adding or deleting child elements from them.

Working with the DOM of a webpage in Javascript means you will probably spend a lot of time in the Dev Tools Elements/Inspector tab examining the exact state of the DOM.

## Selecting Nodes

### Selecting a single node

We've been doing this with `getElementById()` so far.  It lets you specify an element ID and it returns that element.

```javascript
var heading = document.getElementById('heading');
```

<https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById>

You can also use `document.querySelector()` as well. It's first parameter is a css selector.  It returns the first element matched.

```javascript
var heading = document.querySelector('h2.article-heading');
```

<https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector>


### Selecting Multiple Nodes

Selecting one element is useful, but what if you want to manipulate several?  There are a few functions for this:

`document.getElementsByClassName()` returns all the elements with the class that you pass as a parameter.

<https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName>

`document.getElementsByTagName()` returns all the elements of the tag name you pass as a parameter.

<https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByTagName>

`document.querySelectorAll()`  is like `querySelector()` but returns all the matched elements.

<https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll>

Each of those functions return an object called a NodeList.  A NodeList is a lot like an array, with each item in the array being an element.

## Manipulating Elements

Once you have a reference to an element via one of the above methods, changing them is as easy as assigning new values to their properties.

`innerText` is the property that contains the text content of an element.  We changed this frequently many times today.

You can change basically any property of an element.  A complete list can be found here:

<https://developer.mozilla.org/en-US/docs/Web/API/Element>

## Deleting Elements

To delete an element from the DOM you can use the `removeChild()` method of its parent.  This means you need to have a both a reference to the element you want to remove AND its parent element.  This is because the parent is responsible for removing it.

```javascript
var parent = document.getElementById("catlist");
var child = document.getElementById("cat_432");
parent.removeChild(child);
```

<https://developer.mozilla.org/en-US/docs/Web/API/Node/removeChild>

## Inserting Elements

Inserting new elements requires 3 steps:

1. Create the new element (and set it's properties)
2. Get the parent node
3. Add the new element to the parent

```javascript
var newLi = document.createElement('li');
newLi.innerText = cat.name + " ("+cat.age+"/"+cat.color+")";
var parent = document.getElementById('catlist');
parent.appendChild(newLi);
````

The example above uses `appendChild()` to add the new element to end of the list of its parent's child elements.

However there are several other functions for the actual adding of the child element, such as `replaceChild()`, `insertBefore()`, and `append()`

* <https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement>
* <https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild>
* <https://developer.mozilla.org/en-US/docs/Web/API/Node/replaceChild>
* <https://developer.mozilla.org/en-US/docs/Web/API/Node/insertBefore>
* <https://developer.mozilla.org/en-US/docs/Web/API/ParentNode/append>

## Learning more about the DOM

There is a huge number of functions available for interacting with an manipulating the DOM.  We've barely touched the surface here.

You can read more about it here: <https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction>
