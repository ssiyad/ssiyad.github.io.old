---
title: "Veronika Decides to Try JavaScript"
date: 2021-08-17T01:04:08+05:30
---
That’s a joke, she didn’t. Instead, she decides to die only to meet a new world of infinite possibilities that awaited her. She is a character from Paulo Coelho’s stellar novel titled ‘Veronika Decides to Die’. If you haven’t read it already, I suggest you do. It’s a good book with a very much relatable setting. Meanwhile, I thought it might make a good title so here we are.

You might be thinking, what is this about then, if not Veronika? yes! it’s JavaScript! Even tho I’m not a big fan of JavaScript, I find it quite tinker-able and useful. JavaScript makes its way into almost everything, from front-end web development to smartphone applications. If you’re one of those who use VSCode, your editor runs on JavaScript. If you happen to use any cross-platform desktop applications, it is probably an electron app that renders JavaScript in a polished window. That being said, if you’re a JavaScript guru, please ignore the rest of this post, and wave your hands as you close this window. If you’re going to continue reading, let me welcome you to the problem and the reasons for it.

### The Backstory

```
> a = 1
1
> b = 1
1
> a == b
true
```

This is good, both `a` and `b` have a value of `1` and when we check if `a` and `b` are equal (`==`), it returns `true` which means both `a` and `b` have equal values. Let's also note that,

```
> typeof a
'number'
> typeof b
'number'
```

And let's try,

```
> a = {}
{}
> b = {}
{}
> a == b
false
```

Why wouldn't `a` and `b` not equal? They are both empty right? Well, as developer docs says,

> If the operands are both objects, return true only if both operands reference the same object.

That means a and b have different memory addresses unlike,
```
> a = b = {}
{}
> a == b
true
```

where a point to b and equality is satisfied. In the case of primitive values like in the first case, we have a different condition that says,
> If the operands have the same type, they are compared as follows:
- `String`: return `true` only if both operands have the same characters in the same order.
- `Number`: return `true` only if both operands have the same value. `+0` and `0` are treated as the same value. If either operand is `NaN`, return `false`.
- `Boolean`: return `true` only if operands are both `true` or both `false`.

### The Problem

We know that,

```
> typeof new Date()
'object'
```

and let's try,

```
> new Date() == new Date()
false
```

This is known since both have different memory addresses and variables referencing different objects do not satisfy equality. But then we can,
```
> new Date() <= new Date() && new Date() >= new Date()
true
```

which to be frank, looks like an abomination but helps me spit this point. This essentially means we have equality satisfied but at a very high cost. But why would this work when == doesn’t? Because we have a different algorithm for < and >. From developer docs,
> First, objects are converted to primitives using Symbol.ToPrimitive with the hint parameter be 'number'.
If both values are strings, they are compared as strings, based on the values of the Unicode code points they contain.
Otherwise JavaScript attempts to convert non-numeric types to numeric values:
Boolean values true and false are converted to 1 and 0 respectively.
null is converted to 0.
undefined is converted to NaN.
Strings are converted based on the values they contain, and are converted as NaN if they do not contain numeric values.
If either value is NaN, the operator returns false.
Otherwise the values are compared as numeric values.

So what `<` and `>` does is converting the date object to its numerical value, which is t*he number of milliseconds between 1 January 1970 00:00:00 UTC and the given date aka the epoch.* JavaScript use `Date.prototype.valueOf()`behind the scenes to convert a date object to a primitive value. But we can use `Date.prototype.getTime()` since `Date.prototype.valueOf()` is usually called internally by JavaScript and not explicitly in code. 

### The Solution

Now we know what was wrong, and how we should actually equality check date objects

```
> new Date().getTime() == new Date().getTime()
true
```

### That's it!

JavaScript is a weird programming language to learn, but it's also a fun experience. So if you decide to try it, like Veronika, I'd recommend you to play with its core, there is a lot to explore. Thanks for reading!

