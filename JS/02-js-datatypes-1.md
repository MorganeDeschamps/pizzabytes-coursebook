<!-- ![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# JS | Data Types in JavaScript - number & string -->

## Learning goals

After this lesson you will:

- know what are the two main kinds of data types in JavaScript based on their values
- be able to use the number data type
- be able to use the string data type
- become more familiar with some string methods

## Two Main Kinds of Data Types

There are two kinds of data types in JavaScript:

1. **primitives** or **primitive values** and
2. **objects** or **non-primitive values**.


According to MDN, a primitive (a.k.a. primitive value or primitive data type) is **any data that is not an object and has no methods**.

This being said, in JavaScript, there are 6 primitive data types:

- number,
- string,
- boolean,
- null,
- undefined,
- symbol (latest added in ECMAScript2015)

We will come back to the concept of immutability but, for now, keep in mind that **all primitive data types are immutable**.

Let's talk a bit about numbers as data types 🔢

## A number as data type

Using numbers, we can represent **integers** and **floating-point numbers** in JavaScript.

```javascript
const age = 34;
const price = 12.99;
```

Number as a data type also supports **special numeric values**:
`NaN` and `Infinity`. We really don't have to go in details here but `NaN` is something that you'll see throughout this course so let's explain a bit.

`NaN` stands for **Not a Number** and it represents a **computational error**. It is a result of incorrect mathematical operation, such as:

```javascript
const name = 'Sandra'; // <== string data type
const whatIsThis = name / 2;

console.log(whatIsThis); // ==> NaN
```

_NaN_ is not a normal number, although it belongs to this data type. If you get _NaN_ and you expected to get a number after some mathematical operation, you are probably performing the operation on a string or some other data type that isn't a number.

### Number expressions

If you're familiar with math or other sciences, the term `operator` is well known to you. When we're doing basic addition, in the example `2 + 2`, `+` is the `operator`, and the operation executed here is `addition`.

Let's recap some basic math operations:

- `+` addition
- `-` subtraction
- `*` multiplication
- `/` division

Everyone is familiar with these operators, but in case you want to play a bit with them, here's a codepen:

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/WGRbGO/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/WGRbGO/'>JavaScript - Simple Math</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

### Advanced Operators

#### Exponentiation

In math, there is a very useful concept called [exponentiation](http://mathworld.wolfram.com/Exponentiation.html). Exponentiation is the process of taking a quantity `b` (the base) to the power of another quantity `e` (the exponent).

In JavaScript, we can easily use exponentiation by using the `**` (exponentiation) operator:

```javascript
console.log(2 ** 5);
// 2 * 2 * 2 * 2 * 2
// => 32
```

#### Modulo

Modulo (`%`) is the remainder operator. Think of this as saying _If I divide the first number by the second, what is the remainder?_

This is very handy for finding multiples of a particular number, and many other use cases:

<iframe height='385' scrolling='no' src='//codepen.io/ironhack/embed/ozBgrX/?height=385&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/ozBgrX/'>JavaScript - Modulo Operator</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### Assignment Operators

Previously we learned how to assign values to variables. We use **`=`** sign to do this. To make sure we are all on the same page:


The basic assignment operator is equal (=), which assigns the value of its right operand to its left operand. That is, x = y assigns the value of y to x. (source: [Assignment operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators))

Very commonly used assignment operator is `+=` and here is an example of how to use it:

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/jryEGk/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/jryEGk/'>JavaScript - +=</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>
<br />

`+=` is the equivalent of saying `myAge = myAge + 1`. Adding `myAge` and `1` on its own _does not_ change the value of myAge, it simply adds the two together and `returns` you the value computed. (**Remember this when we talk about immutability a bit later in the lesson.**)

##### Basic Assignment Operators Table

These are the most used assignment operators:

| Name                                 | Operator  | Equivalent   |
| ------------------------------------ | --------- | ------------ |
| **Assignment**: `=`                  | `x = y`   | N / A        |
| **Addition assignment**: `+=`        | `x += y`  | `x = x + y`  |
| **Subtraction assignment**: `-=`     | `x -= y`  | `x = x - y`  |
| **Multiplication assignment**: `*=`  | `x *= y`  | `x = x * y`  |
| **Division assignment**: `/=`        | `x /= y`  | `x = x / y`  |
| **Remainder assignment**: `%=`       | `x %= y`  | `x = x % y`  |
| **Exponentiation assignment**: `**=` | `x **= y` | `x = x ** y` |

To see the full list, visit [Assignment Operators - Overview](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Overview).

### Expressions

An expression is a combination of any `value` (number, string, array, object) and set of `operators` that result in another value.

So we can say that the following is an example of an _expression_:

```javascript
2 + 4;
```

And this is its correspondent [parse tree](https://en.wikipedia.org/wiki/Parse_tree):

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_d9aa3dbc661aaef507e7248739084b44.png)

_Take number two and add four to it._

Another example is this:

```javascript
const result = (7 + 5) / 3 - 8;
console.log(result);

// => -4
```

- Take the number 7, add it to 5
- Divide this new value by 3
- Take that value and then subtract 8
- Assign that value to `result`

_Parentheses_ are known as a [grouping operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Grouping).

It seems JavaScript knows in what order to put the numbers together. How does it do this?
Well it literally follows the basic mathematic rules - let's refresh our memory.

### Operator Precedence


In mathematics and computer programming, the order of operations (or operator precedence) is a collection of rules that define which procedures to perform first in order to evaluate a given mathematical expression.

Expressions in math have a particular order in which they get evaluated, based on the operators they use.

`2 + 2 = 4`
`2 + 2 * 2 = 6`
`(2 + 2) * 2 = 8`

As we said, in JavaScript, the same as in math, we have to follow **PEMDAS** rules.

| Precedence | Operator | Name               |
| :--------: | -------- | ------------------ |
|     1      | `()`     | **P**arantheses    |
|     2      | `**`     | **E**xponents      |
|     3      | `*`      | **M**ultiplication |
|     4      | `/`      | **D**ivision       |
|     5      | `+`      | **A**ddition       |
|     6      | `-`      | **S**ubtraction    |

In the numerical order, anything that comes first will be executed first (**1** for **Parentheses**, **2** for **Exponents**, etc.), meaning that anything in parentheses will be executed first, exponents second, multiplication third, etc.

```javascript
const i = 10 + (5 * 2 ** 3) / 4 - 6;
//  === 10 + 5 * 8 / 4 - 6 <== start with the exponents (2 ** 3)
//  === 10 + 40 / 4 - 6 <== then multiplication (5 * 8)
//  === 10 + 10 - 6 <== then division (40 / 4)
//  === 20 - 6 <== then addition (10 + 10 )
//  ==> 14 <== and finally finish with subtraction (20 - 6)
```

This Parse Tree diagram may help you understand it more visually :)

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_98330aa1e31c3739022d86bec0bcd822.png)

You can find a list of these operators and the order in which they are executed [here at MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence).

:memo: **Time to practice**

#### Guess the expression result!

Take a solid guess at what the result of the expression is going to be!


**Tip:** To see the actual result, uncomment the `console.log` by pressing `⌘` + `/`

<iframe height='475' scrolling='no' src='//codepen.io/ironhack/embed/qaRJab/?height=475&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/qaRJab/'>qaRJab</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

<br />

## A string as data type

### What is a string?

A `string` is simply **a sequence of characters**. A `character` can be a letter, number, punctuation, or even things such as new lines and tabs.

### Creating a String

To create a string in JavaScript you have to use one of these **quotes**:

- `""` double quotes,
- `''` single quotes or
- ` `` ` backticks (grave accents).

There's no real difference between double and single quotes, so it is a matter of preference.
**Backticks**, however, have **"extra" functionality**. Using backticks, we are actually creating **template literals**.


**Template literals** are string literals allowing embedded expressions.

Strings in JavaScript have been historically limited. [ES6 Template Strings](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) introduces an entirely different way of solving these problems.

```javascript
let greeting = `Yo, Ironhack!`;
```

One of their first real benefits is **string substitution**. Substitution **allows us to take any valid JavaScript expression and place it inside a template literal, and the result will be output as part of the same string**.

In simple English, using backticks we can **embed variables and expressions inside the strings**. Template strings can contain placeholders for string substitution using the **`${ }` syntax**, as demonstrated below:

```javascript
let name = 'Ana';
console.log(`Hello there, ${name}!`);
// ==> Hello there, Ana!

console.log(`${name} walks every day at least ${1 + 2} km.`);
// ==> Ana walks every day at least 3km.
```

**ES5 Old-school style!!**

```javascript
var customer = { firstName: 'Foo', lastName: 'Kim' };
var message = 'Hello ' + customer.firstName + ' ' + customer.lastName + '!!';
console.log(message);
```

**ES6 Interpolation style!!**

```javascript
let customer = { firstName: 'Foo', lastName: 'Kim' };
let message = `Hello ${customer.firstName} ${customer.lastName}!!`;
console.log(message);
```

As you can see, this kind of interpolation using template literals makes our code much more readable and cleaner!

### Multiline Interpolation

Another great functionality of backticks is being able to easily add **new lines** in the same string (meaning the string can span multiple lanes):

```javascript
const fruits = `
1. banana
2. apple
3. orange
4. cherry
`;

console.log(fruits);
// 1. banana,
// 2. apple,
// 3. orange,
// 4. cherry
```

As we can see, each fruit is on its own line. With other kinds of strings that would cause a syntax error.

<!-- **to take out:**
<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/ALjZxV/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/ALjZxV/'>JavaScript - Creating strings</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe> -->

#### Special characters

Some strings are special because they contain special characters. This means that we have to use **`escape sequences`** to make everything work.

For example, when you want to have double quotes in the middle of your string (sentence), you will have to use some "magic" 🎩.

```javascript
const favBook = "My favorite book is "Anna Karenina".";
console.log(favBook); // <== error: Unexpected token
```

If you can use single quotes, no problem:

```javascript
const favBook = "My favorite book is 'Anna Karenina'.";
console.log(favBook); // <== My favorite book is 'Anna Karenina'.
```

If you, however, for some reason have to use double quotes, your way around this would be using **backslash escape** character.

```javascript
const favBook = 'My favorite book is "Anna Karenina".';
console.log(favBook); // <== My favorite book is "Anna Karenina".
```

The same applies for apostrophes inside single quote strings:

```javascript
const mood = "I'm OK.";
console.log(mood); // <== I'm OK.
```


So, to conclude, you should use `\` (backslash) when there's a need to escape a special character in a string.

It's still possible to create **multilane strings** with double or single quotes but with the help of "new line character" `\n`.

```javascript
const fruits = ' 1. banana \n 2. apple \n 3. orange \n 4. cherry';

console.log(fruits);
// 1. banana,
// 2. apple,
// 3. orange,
// 4. cherry
```

To summarize - these are different ways of doing the same thing:


```javascript
console.log('Web Dev \nUX/UI');
console.log(`Web Dev
UX/UI`);

// both consoles are the same:
// Web Dev
// UX/UI
```


<!-- **to take out:**
<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/ozgKqV/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/ozgKqV/'>JavaScript - Escaped strings</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe> -->


:star: You can see a full list of these special characters at the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types#Using_special_characters_in_strings).

#### String length

`.length` is a numeric property of a string.

```javascript
const name = 'Ana';
console.log(name.length); // <== 3
```

`length` is not a method of a string so don't try to get it by putting parentheses after `name.length()`.

### Methods for string manipulation

Manipulating and modifying strings in code are common operations. Simple things such as capitalizing a name, or checking to see if a word starts with some letter are very common.

JavaScript includes a **String library of methods** to simplify some of the most common tasks on strings. Let's look at how to perform some of these operations.

#### Adding To Strings

We can easily `concatenate` or add characters to strings with the `+` or `+=` operator.

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/EgaqRZ/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/EgaqRZ/'>JavaScript - String Concatenation</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### Accessing characters

One of the ways to access the characters inside the string is using **`charAt(n)`** method.

**`charAt(n)`** shows the character on the `n`th position in the string but keep in mind, the first character is indexed with zero (0).

```javascript
const greeting = 'Hello there!';
console.log(`"${greeting}" is a string and it's length is ${greeting.length}.`);
// "Hello there!" is a string and it's length is 12.
console.log(greeting.charAt(0)); // <== H
console.log(greeting.charAt(1)); // <== e
console.log(greeting.charAt(5)); // <== " "
console.log(greeting.charAt(11)); // <== !
console.log(greeting.charAt(12)); // <== "" as an empty string
```

We can also access characters inside of strings with square brackets and their **`index`** number. As we said, the index **starts at 0**.

```javascript
const greeting = 'Hello there!';
console.log(greeting[0]); // <== H
console.log(greeting[3]); // <== l
console.log(greeting[9]); // <== r
console.log(greeting[-2]); // undefined
```

<!-- **to be taken out**
<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/XjJvxB/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/XjJvxB/'>JavaScript - Accessing characters</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe> -->

#### Finding a substring

JavaScript has a cool **`.indexOf(substr)`** method that returns the index where a particular character/substring occurs. If the substring was not found, it returns `-1`.

```javascript
const message = "Don't be sad, be happy!";
console.log(message.indexOf("Don't")); // <== 0
console.log(message.indexOf('t')); // <== 4
console.log(message.indexOf('Be')); // <== -1 (capitalized Be ≠ lowercased be)
console.log(message.indexOf('py')); // 20
```

The substring `be` appears more than once. To see the next occurrence, we need to tell somehow our .indexOf() method to skip the first one.

```javascript
const message = "Don't be sad, be happy!";
console.log(message.indexOf('be')); // <== 6
console.log(message.indexOf('be', 7)); // <== 14
```

What we did was passing a second parameter, which represents a value where the first occurrence appeared (it was 6) + 1. So we are telling the method to skip the positions from `0 to 7` and keep looking for the occurrence of the first parameter (in our case: _"be"_).

If we need to look for a substring but from the end to its beginning, you can use **`str.lastIndexOf(substr)`**. It shows occurrences in the reverse order.

```javascript
const message = "Don't be sad, be happy!";
console.log(message.lastIndexOf('be'));
// The index of the first "be" from the end is 14
```

<!-- **to be taken out**
<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/bwdbNR/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/bwdbNR/'>bwdbNR</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe> -->

#### 📝Practice

Write code that finds the index of the letter "j" in `My favorite dessert is jello`.

#### .repeat()

Repeat does exactly what it sounds like. Call repeat on a specific string, and pass it an argument of the times it is to be repeated.

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/WGvZwX/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/WGvZwX/'>JavaScript - Handy String Methods</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### Getting a substring

In JavaScript, we can use

- **.substring()**,
- **.substr()** and
- **.slice()**
  to get a substring from a string. Each of these methods is used for **getting the part of the string between start and end** but they have slight differences.

```javascript
const message = "Don't be sad, be happy!";
let withSubstring = message.substring(0, 3);
console.log(withSubstring); // <== Don

let withSubstr = message.substr(0, 3);
console.log(withSubstr); // <== Don

let withSlice = message.slice(0, 3);
console.log(withSlice); // <== Don
```

As we can see, they all give the same results. What if we pass a **negative** values?

```javascript
let withSubstring = message.substring(-3, -1);
console.log(withSubstring); // <== "" (empty string)

let withSubstr = message.substr(-3, -1);
console.log(withSubstr); // <== "" (empty string)

let withSlice = message.slice(-3, -1);
console.log(withSlice); // <== py
```

Only **.slice() supports negative values** and they mean the **position is counted from the string end**.
It is a matter of your personal preference which one to use.

#### Sorting the strings - .localeCompare()

According to [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare), the **`.localeCompare()`** method returns a number indicating whether a string comes before or after or is the same as some other string in sort order.
How does this method work?

```javascript
'str1'.localeCompare('str2');
```

:+1: Returns **1** if `str1` is greater than `str2` according to the language rules.
:+1: Returns **-1** if `str1` is less than `str2`.
:+1: Returns **0** if they are equal.

```javascript
console.log('barcelona'.localeCompare('miami')); // -1
console.log('miami'.localeCompare('barcelona')); // 1
console.log('Miami'.localeCompare('miami')); // 1
```

### ES6 new string methods

ES6 introduced a couple more methods.

#### `startsWith()` method

The `startsWith()` method determines whether a `string` begins with the characters of a specified string, returning `true` or `false` as appropriate.

It's important to remember that this method is case-sensitive.

**Syntax**



```javascript
str.startsWith(searchString[, position])
```

- **searchString** - the characters to search at the start of this string,
- **position** (optional) - the position in this string at which to begin searching for _searchString_ (the default is 0).
  
**Example**

```javascript
const str = 'To be, or not to be, that is the question.';

console.log(str.startsWith('To be')); // true
console.log(str.startsWith('not to be')); // false
console.log(str.startsWith('not to be', 10)); // true
```

#### `endsWith()` method

The `endsWith()` method determines whether a string ends with the characters of a specified string, returning `true` or `false` as appropriate. It's also case-sensitive.

**Syntax**



```javascript
str.endsWith(searchString[, length])
```

- **searchString** - the characters to search at the start of this string,
- **length** (optional) - if provided, overwrites the considered length of the string to search in. If omitted, the default value is the length of the string.
  
**Example**

```javascript
const str = 'To be, or not to be, that is the question.';

console.log(str.endsWith('question.')); // true
console.log(str.endsWith('to be')); // false
console.log(str.endsWith('to be', 19)); // true
```

#### `includes()` method

The `includes()` method determines whether one string may be found within another string, returning `true` or `false` as appropriate. The method is case sensitive.

**Syntax**



```javascript
str.includes(searchString[, position])
```

- **searchString** - the characters to search for at the start of this string,
- **length** (optional) - the position within the string at which to begin the search (defaults to 0).
  
**Example**

```javascript
const str = 'To be, or not to be, that is the question.';

console.log(str.includes('to be')); // true
console.log(str.includes('question')); // true
console.log(str.includes('nonexistent')); // false
console.log(str.includes('To be', 1)); // false
```

## Summary

In this lesson, we learned how to declare, use, and manipulate numbers and strings, two primitive data types. Also, we got familiar with some of the inherited number and string methods as well as with some of the new ones (introduced with ES6 updates).

## Extra Resources

- Most of the JavaScript String methods can be found at [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)
- [Using special characters in strings](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types#Using_special_characters_in_strings)
