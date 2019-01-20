---
title: How to fix imprecise calculations in JavaScript
categories: [JavaScript]
tags: [calculation, parseFloat, toFixed]
---

What is it about? Try to execute some of the following examples in the browser console (or somehow using JavaScript) and you will see that sometimes there are small computational errors.

Browser console output:

```
> 0.1 + 0.2
0.30000000000000004
```

```
> 0.1 * 0.2
0.020000000000000004
```

```
> 16.08 * 100
1607.9999999999998
```

```
> 0.1.toFixed(20)
"0.10000000000000000555"
```

```
> 9999999999999999
10000000000000000
```

Don't get me wrong, this is certainly not a problem of the language itself. The same thing happens in Java, C, PHP, Ruby, etc. If you are interested in the details, please read more in [this article](https://javascript.info/number#imprecise-calculations).

Below you will find the simplest solutions that allow to "fix" this inaccuracy.

## Solution #1

Let’s use the [toPrecision](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toPrecision) method to format a number to a specified precision.

```javascript
// Pedro Ladaria's solution
function strip(number) {
    return (parseFloat(number.toPrecision(12)));
}
```

Browser console:

```
> strip(0.1 + 0.2);
0.3
```

```
> strip(0.1 * 0.2);
0.02
```

```
> strip(16.08 * 100);
1608
```

## Solution #2

Let’s format a number using fixed-point notation into a string with 2 (up to 20) digits after the decimal point using the [toFixed](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed) method.

Browser console:

```
> (0.1 + 0.2).toFixed(2)
"0.30"
```

```
> (0.1 * 0.2).toFixed(2)
"0.02"
```

```
> (16.08 * 100).toFixed(2)
"1608.00"
```

It's not hard to get a number as a return value. For instance,

```
> parseFloat((0.1 + 0.2).toFixed(2))
0.3
```