<!-- ![](https://i.imgur.com/1QgrNNw.png)

# JS | Numbers as Data Types - Advanced Topics -->

## Writing big numbers

Sometimes you have to work with extremely big numbers and writing those can be tricky. If you would need to have a number like this:

```javascript
const someVar = 100000000;
```
you could've easily mistyped it. One zero less and you go from 1 billion to 100 million.
In JavaScript, it is possible to avoid this kind of situations by adding the letter `e` to the number and specifying how many zeros are there in a number. Example:

```javascript
const someVar = 1e9;
```
This literally means: **1 and 9 zeros which is 1 billion**. Much better, ha? No need to count those zeros any more 😅

But don't get confused here - we are not simply adding zeros but instead we are multiplying the number with a zero representation of the big number. 

```jsx
1e9 = 1 * 1000000000
4.5e6 = 4.5 * 1000000
```
At the same time, this is not just applicable to the large numbers, but for the very small ones as well.

```jsx
const someSmallNumber = 0.001;
```
or even smaller one:
```jsx
const someOtherSmallNumber = 0.0000045;
```
Here, one more time, `e` will be helpful:
```javascript
const someSmallNumber = 1e-3;
const someOtherSmallNumber = 4.5e-6;
```
How this works:
```
1e-3 = 1/1000 ===> 0.001
4.5e-6 = 4.5/1000000 ===> 0.0000045
```

## Number Methods for Rounding

JavaScript has several built-in functions for rounding:

**`Math.floor()`** => **rounds ⬇️down**: 
- 3.1 becomes 3, and 
- -1.1 becomes -2.

**`Math.ceil()`** => **rounds ⬆️up**:
- 3.1 becomes 4, and 
- -1.1 becomes -1.

**`Math.round()`** => **rounds to the nearest integer**:
- 3.1 becomes 3, 
- 3.6 becomes 4 and 
- -1.1 becomes -1.

These methods round the decimal part of the number but if we would like to **round a number to one, two or three digits**, we would have to look for some alternatives:

1️⃣**Multiply-and-Divide** in combo with **Math.round()**:

```javascript
let anyNumber = 5.679345;
let roundedToOne = Math.round(anyNumber*10)/10;
let roundedToTwo = Math.round(anyNumber*100)/100;
let roundedToThree = Math.round(anyNumber*1000)/1000;

console.log(roundedToOne); // <== 5.7
console.log(roundedToTwo); // <== 5.68
console.log(roundedToThree); // <== 5.679
```
2️⃣ Use method [`.toFixed(n)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed) to round the number to **n** digits after the point.

:warning: Be careful though - this method doesn't return a number but its string representation, which means you should parse it back into the number.

```javascript
let anyNumber = 5.679345;
let roundedToOne = anyNumber.toFixed(1);
console.log(roundedToOne); // <== "5.7"
```
As you can see, we got the string back (notice the `""` around the number). To turn string representation of the number into the number itself, we can use:
- Number():
```javascript
let roundedToOne = Number(anyNumber.toFixed(1));
console.log(roundedToOne); // <== 5.7
```
🔖 Sidenote: Try adding `typeof` in the console.log() in the first and in the second case and see the difference!
- plus (`+`) sign:

```javascript
let roundedToTwo = +anyNumber.toFixed(2);
console.log(roundedToTwo); // <== 5.68
```
## Not accurate calculation ❌

- `Infinity`

Our computers use 64 bits to store a number. So is it possible to have a number so big, it doesn't fit 64 bits? Yes, it is possible and in that case we are dealing with `Infinity` issue.
If we try to save or manipulate extremely large number, here is what happens:
```javascript
console.log(1e400); // <== Infinity
```
If you would like to know more why and how this happens, you can check this article related to IEEE-754 (which is the standard for representing the numbers in computers): [IEEE 754-1985](https://en.wikipedia.org/wiki/IEEE_754-1985#Representation_of_non-numbers).

- Off calculations

```
0.1 + 0.2 = 0.3
```

If someone asks you to bet in the truthiness of this statement, what would you say?

We hope you were not ready to take a bet on this since this statement is `false` 🤯

Then how much is `0.1 + 0.2`?

```javascript
console.log(0.1 + 0.2); // 0.30000000000000004
```
Wow! This is a potentially huge problem! If you're helping to develop some measurement app and you don't take these things into account, you might spend a loooot time fixing your mistakes later. 
So why is this happening? 
We in everyday calculations use the decimal numeral system and computers, on the other hand, use binary numeral system.

Well, **in the binary numeral system, 1/10 is endless binary fraction**. 

To understand this, imagine dividing 1 by 3, in our everyday decimal numeral system : 
```
1/3 = 0.3333333333333333
```
To conclude:


In the decimal numeral system division by powers of 10 is guaranteed to work, but if we divide a number by 3, that doesn't work. At the same time, in the binary numeral system, the division by powers of 2 is guaranteed to work, but 1/10 is an endless fraction.

How to solve this problem? 

 
Use `.toFixed(n)` method (but keep in mind that it returns the string).

## Other math methods on numbers

**`Math.random()`** => returns a random number from 0 to 1 (including 0 but not including 1)

```javascript
console.log(Math.random()); // <== 0.010086087097095797
console.log(Math.random()); // <== 0.24143918045188073
console.log(Math.random()); // <== 0.23920890331219713
```
Every time will give you a different random number. You will be using this method quite often so keep it in mind.

**`Math.max(a, b, c...)` / `Math.min(a, b, c...)`** => returns the greatest/smallest from the arbitrary number of arguments.

```javascript
console.log(Math.max(2, 8, -10, 0, -4)); // <== 8
console.log(Math.min(1, 2, 0, -5)); // <== -5
```
**`Math.pow(n, power)`** => returns n raised the given power

```javascript
console.log(Math.pow(2, 3)) // <== 8
```
## Summary

## Extra resources
- [How to fix imprecise calculations in JavaScript](https://vyspiansky.github.io/2019/01/20/imprecise-calculations-in-javascript/)
- [Number.POSITIVE_INFINITY](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/POSITIVE_INFINITY)
- [Number.NEGATIVE_INFINITY
](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/NEGATIVE_INFINITY)