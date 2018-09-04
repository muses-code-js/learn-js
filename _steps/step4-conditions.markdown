---
layout: step
number: 4
title: Conditions
permalink: step4/

---


We don't always want our programs to perform the exact same series of steps every time.
Often we want different actions to occur based on user input or other information.

We refer to this as our code having **branches** or more than one **path**.

**Conditional statements** (or conditionals) are how we control which paths our programs will follow when they run.

The most common conditional is the `if` statement.

Here's an example that checks if the user had supplied a first name and sets an error message if they hadn't.

```Javascript
if(firstName == ''){
  errorMessage = 'You must enter your first name';
}
```

There are two basic parts to an `if`:

 * the condition in parentheses, which is the question being asked
 * the code block in braces, which is what to do if the answer to the question is yes.

Optionally you can add an `else` and another code block to be run if the condition is not met.

The condition is assumed to be what we call a **boolean expression**.
Boolean expressions are expressions that get evaluated to one of two special values: `true` or `false`.
This is done using special operators called **comparison operators**.

The boolean operator used above (`==`) is called the **equality operator** AKA the **is equal to** operator.
If the values on both sides of it are considered equal then the expression evaluates to `true`.
If they aren't equal then the expression is `false`.

## Using Conditionals

Let's continue the example from the previous step by updating it so we can tell the page our name, and it can use that name to address us.

First add a box that we can type our name into:

```html
<input type="text" id="nameInput" placeholder="Type your name here" />
```

Now lets's update our JavaScript so our `handleLeave` and `handleArrive` functions get what we have typed into the box and include it in the message.

```JavaScript
function handleArrive(){
  var name = document.getElementById('nameInput').value;
  message = 'Welcome '+name+'!';
}

function handleLeave(){
  var name = document.getElementById('nameInput').value;
  message = 'Farewell '+name+'!';
}
```

Ok, refresh the page, type a name into the box, click `arrive` or `leave`.

[SCREENSHOT]

But wait, we have a subtle problem.
What if you don't type in a name?
Your message will just have a blank name, which isn't great.

So let's fix that by using conditionals to tell our code what to do in that case.

```Javascript
function handleArrive(){
  var name = document.getElementById('nameInput').value;
  if(name == ''){
    message = "Welcome stranger!  What's your name?";
  }
  else {
    message = 'Welcome '+name+'!';
  }
}

function handleLeave(){
  var name = document.getElementById('nameInput').value;
  if(name == ''){
    message = 'Farewell mysterious stranger!';
  }
  else {
    message = 'Farewell '+name+'!';
  }
}
```

Here we are using an else block.

If `name` is an empty string we set `message` to a string that does not include `name`.

If `name` is not an empty string then the `else` block will run and it sets `message` to a string with `name` concatenated into it with `+`.

So now `handleArrive` and `handleLeave` both have two different **paths of execution**.  

<div class="aside">
`handleArrive` and `handleLeave` do almost exactly the same steps, with subtle differences.  
You might be wondering if there is a better way to handle this so you aren't writing almost the same code over and over.
Yes there is, we use functions for that which we will talk about about in the next step.
</div>

## Comparison Operators

So far we've seen the `==` comparison operator, the **is equal to** operator.

| Operator | Name/Description | Applies to |
|-|-|-|
| `==` | Equality.  Both sides must be equal.  | Numbers & Strings. |
| `===` | Strict equality. Value & type must both be the same.| Numbers & strings.|
| `!=` | Inequality.  Both sides must be different.  | Numbers & strings. |
| `!==` | Strict inequality. Different values OR different types. | Numbers & strings.|
| `<` | Less than.  | Numbers. |
| `>` | Greater than.  | Numbers. |
| `<=` | Less than or equal to.  | Numbers.  |
| `>=` | Greater than or equal to.  | Numbers. |

These are all pretty obvious with the exception of the strict equality & inequality.  

The non-strict versions (`==` & `!=`) will try to convert the types of the values if they are different before comparing them.  For example `12 == '12'` is treated as `'12' == '12'`.

The strict versions will not do the type conversion.

It is generally recommended to use the strict versions of these operators.

## Logical Operators

So that lets us compare two things.  But what if you have more complicated conditions you need to evaluate?
To do this we use **logical operators**.

There are three primary logical operators you will encounter: `&&`, `||` and `!`.

### The **AND** operator `&&`

`&&` is the **AND** operator and is used when you have multiple conditions that you need to be true.

```javascript
if (age >= 18 && agreedToTerms) {

}
```

You can chain together as many conditions as you need with `&&`.  It evaluates each from left to right and as soon as it encounters one that is `false` it considers the entire expression to be `false`.  Otherwise the expression is `true`.

### The **OR** operator `||`

`||` is the **OR** operator and is used when you have multiple conditions but only one of them needs to be true.

```javascript
if (age >= 18 || parentSignedForm) {

}
```

Like `&&` you can chain together as many conditions as you like with `||`. It also evaluates them left to right but as soon as it finds one that is `true` it considers the whole expression to be `true`.

### The **NOT** operator `!`

Unlike `&&` and `||` the **NOT** operator `!` is placed in front of an expression to reverse it.

```Javascript
if(!agreedToTerms){

}
```

This is useful for those situations where you want to respond to things not being done, or going wrong.

### Grouping conditions

You can also mix `&&` and `||` but it can get very confusing.  You can use parentheses to group conditions together to ensure they are evaluated how you expect.

Let's say we have a form where:

 * applicants have to specify their age (`age` number),
 * and agree to the terms and conditions (`agreedToTerms` boolean).
 * But if they aren't eighteen or over they have to get a parent to sign a form (`parentSignedForm` boolean).

The following `if` statement doesn't quite work as expected.

```Javascript
if (age >= 18 || parentSignedForm && agreedToTerms) {

}
```

If `age >= 18` is true, then when the `||` is encountered, Javascript thinks it doesn't have to evaluate any further.  Clearly not what we intended.

To clarify where we want the `&&` and `||` to apply we use parentheses:

```javascript
if ( (age >= 18 || parentSignedForm) && agreedToTerms) {

}
```

You can also put `!` before a group to reverse its outcome too.
