---
layout: post
title:  "THE STRUGGLE WITH DECIMALS"
date:   2017-03-24 13:53:46 +0000
---


A couple of months ago, while trying to build a basic javascript calculator I came across the issue involving calculations with decimal numbers. At first I thought it was a javascript thing, but I eventually came to find out and realized that, this is the case of all languages that use IEEE 754 standard for floating point computation. In general, decimal numbers are not interpreted by a computer with precision.

For example, 3.06+3.08= 6.14, right?...well according to irb:


```
2.3.0 :003 > 3.06+3.08
 => 6.140000000000001 
2.3.0 :004 > 2.05+5.07
 =>7.12 
2.3.0 :005 > 7.09+3.04
 => 10.129999999999999
```

Here is another example involving equality from the Javascript console:

```
0.1+0.2 === 0.3
false
```


The problem comes along when the computer tries to convert or interpret the decimal part to a binary number (base 2). There is a lot that goes into how floating points are stored in memory, but a good and easy example is a simple fraction like 1/3; 1/3 cannot be represented with a decimal number and a finite number of digits (0.3333...).
The inconsistency between languages in the output of floating point math is the result of how each language 'abreviates' or rounds the output.
Floating point numbers are most commonly used to represent decimal data and while some of these imprecisions are fairly minimal, there are cases when even the slightest decimal can becomes a problem, especially when it comes to dealing with money. A strategy that is often used by developers when dealing with money in apps is to store any currency amount as whole numbers in terms of cents. Ruby has a BigDecimal class that you can 'require' and use to improve the accuracy on floating point numbers. There is also a 'money' gem which is pretty popular and widely used. 
Javascript, is not popular at all when it comes to anything related to mathematics; fastest and easiest approach is to used the toFixed() built-in method where you specify the number of decimal places you want, however, this won't necessariyl fix the rounding errors issue, and it returns a string which is not very practical when it comes to doing multiple calculations. There are also some Javascript libraries such as mathjs and sinfuljs. Number.EPSILON is a property of the Number object in Javascript which is commonly used to compare two decimal numbers for equality considering a small rounding error tolerance, so this tackles the earlier equality issue:

```
function epsEqu(x, y) {
    return Math.abs(x - y) < Number.EPSILON;
}
console.log(epsEqu(0.1+0.2, 0.3))
 true
```

Ultimately it is a matter of choosing the right tools; there are definitely ways to get around some of these issues. As far as my small calculator, I will stick with limiting the number of decimal places to what the screen can fit. It was definitely a great learning experience that got me into a few rabbit holes where I came accross words like mantissas, epsilon, and read about double precision format, all of which I still need to process and review. Good luck if you are dealing with decimals! 


