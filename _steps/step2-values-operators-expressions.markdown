---
layout: step
number: 2
title: Values and operations
permalink: step2/

---


Most of the code you write will be manipulating or examining data of some sort. That data might come from a file, or from a 3rd party service, or from the user selecting something on a page or typing into a text box.  

That data is represented in our code as **values**.

**Values** are the literal data, the numbers, bits of text, etc. that our programs track. For example, `5` and `'Click the Button'` are two different values.

<!-- **Variables** are placeholders that represent a value.  You can think of a variable as being like a labeled box that you put a value into, and then you can use that value by referring to the box by its label. -->

**Operations** are how we combine values to do calculations, like add, subtract, divide, etc.

**Operators** are the symbols we use to perform operations, `+`, `-`, `=` etc.

An **Expression** is the combining of one or more values and operations to represent a new value.

This is all a bit abstract, so let's demonstrate them by using your browser's **developer tools**.

## Browser Dev Tools

Each of the major browsers includes an interface that you can use to inspect webpages.  This is usually referred to as the browser's Developer Tools or Dev Tools.

One of the tools is the Console.  The console serves two purposes.  Firstly, it displays any messages about errors and the like in the current page.  And secondly, you can run JavaScript in it.  It's really great to experiment with stuff straight in the browser.

To open your Browser's Developer Tools (Dev Tools):

* Chrome & Firefox
  * Windows/Linux: `Ctrl`+`Shift`+`i`
  * MacOS: `CMD`+`Option`+`i`
* Safari
  * MacOS: `CMD`+`option`+`i`
* Edge
  * Windows: `F12` or `Ctrl`+`Shift`+`i`

Safari doesn't have its Dev Tools enabled by default, you turn them on in Safari's Preferences under Advanced.

When you have your Dev Tools open, go to the Console tab.

![Chrome Developer Tools](../assets/step-2a.png){:title="Chrome Developer Tools" class="img-responsive"}


## Arithmetic Operations

In the Javascript console, type the number `205` and press enter.  

You will see it display the number `205` again.  The javascript Console **evaluates** the expression you type in and displays the result.  When you just type a single value like this, it evaluates to itself.

So lets try: `205 + 103`.

![Operations in the Console](../assets/step-2b.png){:title="Operations in the Console" class="img-responsive"}

You'll get `308` displayed.  This expression is an operation with the `+` operator AKA the addition operator.

The basic arithmetic operators are:

 * `+`: addition
 * `-`: subtraction
 * `*`: multiplication
 * `/`: division
 * `MOD`: remainder after division AKA modulus

Just like arithmetic, the good old **order of operations** applies, and you can use `(` & `)` too.

 * `100+50*2` evaluates to `200`
 * `(100+50)*2` is `300`

Experiment with different expressions in the console and see what you get.

### What's with `*` & `/`?
Why `*` & `/` instead of proper multiply & divide symbols?

The answer lies in the fact that the design of the earliest computer keyboards where derived from the design of mechanical typewriters.  

Writers using typewriters didn't need a multiplication symbol because they could just use a lowercase `x` if they needed one,  and you could make a division sign by typing a `-` and then backspacing and typing a `:` over the top.  (#lifehacks :wink:) People also got into the habit of typing fractions as `1/2` and `3/4`.

Fancier typewriters came along with special division and multiplication keys but never quite caught on.

So when we started using keyboards with computers we inherited that limitation and just worked around it by adopting the fractions convention for division and using the relatively unused `*` for multiplication.


### Values & Types

Ok so the values that we used above were all numbers.  What about other things like someone's name?  How do we represent that?

If we look at the code we have already, how do we represent the message that gets displayed?

```javascript
document.getElementById('displayBox').innerText = 'You clicked the button!';
```

When we surround characters with quotes characters like this, it makes a type of value that is called a **string**.  A string is just a sequence of letters, numbers and other characters which is a literal representation of them.  Imagine a string as bunting with letters, like a sign at a party.

[IMAGE PARTY SIGN BUNTING]

There are different kinds of values for different uses.  We refer to this as the **type** of the value.

The type of a value indicates some expectations about what it should contain and behave.

For instance, we know what to expect from `100+50`.  But what about `'100'+'50'`  Try it out.

JavaScript recognises that both values are strings, so it behaves differently when you try to add them together: it just sticks them together one after another.  

This is called **concatenating**.

Another example might be joining first and last names together to make a person's full name, like `'Jessica'+' '+'Anderson'`.  Notice how we actually used three strings there?  The second one is a string with just a single space.  A blank space is a character.  A string can be a single character, a word, a sentence, or a whole bunch of paragraphs.  It can be any set of characters you need to use.  A string can be empty too, `''`.

What about the other operators?  What happens if you multiple or subtract strings?

Give it a try.

Try `'Cat' / 'Dog'`.

The result is a special value `NaN`, which stands for **Not a Number**.  Not all operations make sense for all types & you can use values like `NaN` to check when errors might have happened.

Some of the other types include **arrays**, **booleans**, and **objects**.

We'll talk about each of these when we encounter them.

## Type Conversion

So far we've only talked about operations with values of the same type.  But what happens if you try to do operations with different types?

What happens if you try to multiple strings by numbers?
Or try to add strings and numbers?

There are two simple rules for this:

1. If the operation is `+`, then numbers get converted to strings and concatenation is done.
2. Otherwise, javascript tries to turn the string into a number and perform the operation.  If the string isn't a number, then you get `NaN` as the result

This is called **type conversion**.

Try it out in the console:

Eg.

 * `'50' + 5`
 * `'50' * 5`
 * `'Cat' + 102`
 * `'Dog' / 3`    

Ok so that's the basics of values, types, operators and expressions.  

Now let's move on to variables.
