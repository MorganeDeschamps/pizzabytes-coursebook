<!-- ![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_d5c5793015fec3be28a63c4fa3dd4d55.png)

# JS | Data Types in JavaScript-boolean, undefined & null and Immutability -->

## Learning Goals

After this lesson, you will be able to:

- use boolean, undefined and null as data types,
- understand primitives and immutability and
- explain the difference between `value` and `reference` in JavaScript.

## A boolean as data type

Some questions can only be answered with two possibilities: `yes` or `no`. For example:

- Are you going out tonight? `No`
- Will you learn a lot of new stuff at Ironhack? `Yes`
- Do you like your TAs? Hell, `yes`!

These answers are the equivalent of the boolean values in programming.
:::info
A **boolean** or **bool** expression can result in the value of either **TRUE** or **FALSE**.
:::

Booleans are often used in conditional statements, but we will come to that in a bit. Let's first get familiar with **logical operators**.

### Boolean logic operators

We use logical operators to combine two (or more) conditions and depending on the conditions and the logical operator(s), we will get as a result a **true** or a **false**.

We have three different logical operators:

- **or**,
- **and** and
- **not**.

#### OR Operator (`||`)

The _or_ operator, represented by `||`, returns `true` if **one of the evaluated expressions is `true`**.

:::info

```javascript
expr1 || expr2;
```

:::

If `expr1` or `expr2` is `true`, the result will be `true`. If they both are `false`, the result of the expression will be `false`.

```javascript
true || true; // => true
true || false; // => true
false || true; // => true
false || false; // => false
false || 4 > 2; // true
```

#### AND Operator (`&&`)

The **and** operator, represented by `&&`, returns true just if **all the evaluated expressions are true**.

:::info

```javascript
expr1 && expr2;
```

:::

If `expr1` and `expr2` are `true`, the result will be `true`. If one of the expressions is `false`, the result will be `false`. If both expressions are `false`, of course, the result will be `false`.

```javascript
true && true; // => true
true && false; // => false
false && true; // => false
false && false; // => false
true && 4 > 2; // => true
```

:::info

#### A short-circuit evaluation

As logical expressions in JavaScript are evaluated left to right, they are tested for possible "short-circuit" evaluation using the following rules:

```
false && (anything) is a short-circuit evaluated to false.
true || (anything) is a short-circuit evaluated to true.
```

The rules of logic guarantee that these evaluations are **always correct**.
:::

#### NOT Operator (`!`)

Here we have to mention nothing less important - the **not** operator. It is used to negate the value of an expression.

:::info

```javascript
!expr1;
```

:::

If the expression is **true**, the result will be **false**, and vice versa.

```javascript
!true; // => false
!false; // => true
!(4 > 2); // => false
```

Keep these rules in mind, you will be using them quite a lot.

## An `undefined` as data type

:::info
The **`undefined`** is primitive value automatically assigned to variables when they are declared.
:::

```javascript
let name;
console.log(name); // <== undefined
```

## A `null` as data type

In computer science, a **null** value represents a reference that points, generally intentionally, to a nonexistent address, meaning the variable that hasn't been even declared yet.
However, in JavaScript, `null` is often used to represent `value unknown` variables:

```javascript
let name = null;
console.log(name); // <== null
```

You will often use this value when checking if a variable has even been declared or when you intentionally want to reassign the value of some variable to _null_ because of some changes in its status in your application. (this is just hypothetically speaking, it will be more clear later through the course)

:::warning
We also mentioned `symbol` as a primitive value. However, we will not dig into symbols since we won't use it during this course. If you would like to know more about it here is [MDN - Symbol](https://developer.mozilla.org/en-US/docs/Glossary/Symbol) page and there are many other online resources.
:::

### Truthy and falsy values

:::info
Falsy values will evaluate as FALSE, and truthy values will evaluate as TRUE.
:::

Here are values considered to be truthy and falsy:

| Truthy                | Falsy                 |
| --------------------- | --------------------- |
| `true` (the keyword)  | `false` (the keyword) |
| `'0'` (as string)     | `0` (as number)       |
| `'false'` (as string) | `''` (empty string)   |
| `{}`                  | `null`                |
| `[ ]`                 | `undefined`           |
| `35` (as number)      | `NaN`                 |
| `new Date()`          |

Try putting any of these into the `if` statement and check the result.

```javascript
if ('false') {
  console.log('Passed thingy is truthy');
} else {
  console.log('Passed thingy is falsy');
}

// => 'Passed thingy is truthy'
```

## Immutability

As we said at the very beginning, all primitive data types are **immutable**.
:::info
Immutability means that once one of the primitive values is created, it can't be modified.
:::

Let's explain this:

```javascript
let city = 'miami';
console.log(city[0]); // <== m
city[0] = 'M';
console.log(city); // <== miami
```

Don't get confused here because **values are immutable** but variables are mutable which means you can reassign them:

```javascript
let city = 'miami';
console.log(city); // <== miami

// we CAN re-assign our variable to another value
city = 'berlin';
console.log(city); // <== berlin

// but still CAN NOT change the value "berlin"
city[0] = 'B';
console.log(city); // <== berlin
```

:heavy_check_mark: You can see from the previous example that you can reassign the variable with a new value but you can't alter the existing value.
As you can see, when we practiced the string methods, each of them returned a new string and the original string stayed untouched.

```javascript
const message = "Don't be sad, be happy!";
console.log(message.slice(0, 3)); // <== Don
console.log(message); // <== Don't be sad, be happy!
```

Numbers are immutable as well - but that is more a common sense, right? If number "5" is of value "5", it will stay forever the same value - you can't change it.

Immutability is a very important topic in JavaScript and we will come back to it a bit later in this module when we talk about Objects. Objects (and arrays) are mutable data types by default and we will see what that means in a couple of learning units.

## Summary

In this lesson, you have learned that besides `string` and `number`, there are other primitive data types which you will be using heavily: `boolean`, `null` and `undefined`. Variables that have boolean values can only have the value of `true` or `false`. Booleans are very often used with _logical operators_: _and_ (`&&`), _or_ (`||`), _not_ (`!`).
Besides being `true` or `false`, variables also can have `truthy` and `falsy` values.

All primitive data types are immutable - meaning, once primitives are created, they can't be modified. Values are immutable but variables are mutable which means you can reassign them:

## Extra Resources

- [MDN - Logical Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators)
- [MDN - undefined as data type](https://developer.mozilla.org/en-US/docs/Glossary/Undefined)
- [MDN - null as data type](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/null)
- [MDN - Difference between null and undefined](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/null#Difference_between_null_and_undefined)
- [MDN - Mutable](https://developer.mozilla.org/en-US/docs/Glossary/Mutable)
