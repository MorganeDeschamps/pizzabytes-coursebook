<!-- ![](https://i.imgur.com/1QgrNNw.png)

# JS | Data Types in JavaScript - Arrays -->

## Learning Goals

After this lesson, you will be able to:

- Understand what arrays are and why they are useful
- Access an element using an array's index
- Add elements using **unshift** and **push** methods
- Remove elements using **splice**, **shift** and **pop** methods
- Iterate over an array with a for loop
- Iterate over an array with the **forEach** method
- Use `.split()` method to turn the string into the array of its elements

## Why Arrays?

:::info
[Arrays](https://en.wikipedia.org/wiki/Array_data_type) are data structures that allow us to group a collection of elements together in one variable.
:::
We can later **access each of the elements individually** using an **index**, which represents the position of each element in the structure of an array, or we can pass them around grouped as the array.

For example, if you have a class of several people and want to keep all their names saved in variables, instead of having one for each you can create one array. Let's take a look at how that works.

## Arrays operations

### Declaration

An array can be declared empty:

```javascript
const arrayNames = [];
```

Or you can declare it with some elements already in it:

```javascript
const arrayNames = ['Pedro', 'Jake', 'Joan', 'Mike'];
```

:::info
The elements of the array don't have to be all the same type; we can mix strings, numbers or any other type of data we want.
:::

```javascript
const arrayNames = ['Pedro', 2, true];
```

### Accessing Elements

:::success
We can access individual elements in the array by their position in the array. The position is named _index_.
:::

| **Index** | `0`       | `1`      | `2`      | `3`      |
| --------- | --------- | -------- | -------- | -------- |
| **Value** | `"Pedro"` | `"Jake"` | `"Joan"` | `"Mike"` |

:::warning
:warning: **Zero-Indexed:** Notice how the index of the first element is not `1` as we may think, but `0`!
:::

:::info
The **length of the array** is the number of elements the array is storing at a particular point in time. So if an array has `10` elements, the first index will be `0` and the last one `9` _(length - 1)_
:::
![](https://i.imgur.com/BG4RUNt.png)

Let's try to print _Pedro_ in the console:

```javascript
const arrayNames = ['Pedro', 'Jake', 'Joan', 'Mike'];
console.log(arrayNames[0]); // <== Pedro
```

Simple as that, you can access the elements inside an array by referencing their position in the array, but remember every array starts at _0_, not at _1_! This position is called **index** commonly, so the index 0 of _arrayNames_ returns/has "Pedro" as its value.

```javascript
console.log(arrayNames[1]); // <== Jake
console.log(arrayNames[2]); // <== Joan
console.log(arrayNames[3]); // <== Mike
console.log(arrayNames[99]); // <== undefined
```

:::warning
:warning: If we try to access an index that does not exist, it will return **undefined**.
::::

### Adding Elements

We already know how to create arrays with initial values inside them, but what if we don't know at the moment of creation which values will be stored there? Don't worry, we can easily add them later with [push](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/push) method.

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/qamOWa/?height=265&theme-id=0&default-tab=js%2Cresult&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/qamOWa/'>qamOWa</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

Now, arrayNames has a fourth element, and if we try again to get the fourth position (index 3), it gives us _Rachel_.

An important thing to keep in mind is that, **using `.push()` method, the new value is stored at the end of the array**, not at the beginning or in a random position.

If you wanted to **add an element at the beginning of the array**, use [unshift](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift) instead of _push_:

```javascript
const arrayNames = ['Pedro', 'Jake', 'Joan'];
arrayNames.unshift('Rachel');
console.log(arrayNames[0]); // <== Rachel
```

### Removing Elements

What if we want to delete an element from an array? The [splice](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) method allows us to do it!!

:::info

> **array.splice(start, deleteCount)**

**Start:** Index at which to start changing the array
**deleteCount:** number of old array elements to remove
:::

Let's see it in action!

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/rrmOLB/?height=265&theme-id=0&default-tab=js%2Cresult&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/rrmOLB/'>rrmOLB</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

So, in this example, we are starting at index `0` (first element of the array) and we want to delete 1 element. Finally, if we access the first element again, it gives us _Jake_, which was the second element originally.

Try it yourself:

```javascript
arrayNames.splice(0, 2);
arrayNames.splice(1, 1);
arrayNames.splice(2, 1);
```

But there are other ways to delete elements. For instance, the [pop](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/pop) method allows us to delete the last value, while [shift](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/shift) deletes the first one.

### Summary of Methods

| Method    | Action                                      |
| --------- | ------------------------------------------- |
| `push`    | Adds an element at the end                  |
| `unshift` | Adds an element at the beginning            |
| `shift`   | Removes the first element                   |
| `pop`     | Removes the last element                    |
| `splice`  | Removes elements from anywhere in the array |

### Iterating over each element in an array

Let's say we want to add up all the numbers in an array, or we want to say hello to each of the names in an array. For things like this, it is very useful to be able to iterate over several/all elements in the array with one piece of code. So how do we do that?

You already know what a loop is, for this example, we are going to use the `for` loop. For instance, imagine we want to print all the names inside `arrayNames`. Maybe the first thing you think is:

```javascript
console.log(arrayNames[0]);
console.log(arrayNames[1]);
console.log(arrayNames[2]);
```

But what if we have hundreds of names, or even thousands? This is how we can accomplish something like this with a `for` loop:

```javascript
const arrayNames = ['Pedro', 'Jake', 'Joan'];
for (let i = 0; i < arrayNames.length; i++) {
  console.log(arrayNames[i]);
}
```

Now it doesn't matter how many elements are in the array, this loop is going to print them all in just three lines of code.

### `forEach` method

Iterating over an array with `for` is cool, but since iterating over arrays is something we are going to be doing very often, JavaScript provides us with a much cleaner way of expressing the same idea. Welcome your new friend, the [forEach](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach) method!

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/YGVJAw/?height=265&theme-id=0&default-tab=js%2Cresult&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/YGVJAw/'>YGVJAw</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

:::success
[`forEach`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach) method iterates through all the elements of an array, and **FOR EACH** element in the array, it will call another function, passing in it each element, one by one.
:::

`forEach` receives only one parameter: a function. This function doesn't need a name (it's anonymous), but it can have zero, one, two or three parameters.
In case you are familiar with arrow functions syntax, you know we can shorten the previous syntax a bit:

```javascript
const arrayNames = ['Pedro', 'Jake', 'Joan'];
arrayNames.forEach(name => console.log(name));

// console:
// Pedro
// Jake
// Joan
```

If this syntax doesn't make sense at this moment, it is completely ok. Very soon you will know what arrow functions are and how to write them.

#### No parameters

Will just call the function as many times as elements are in the array:

```javascript
// ES5:
['a', 'b'].forEach(function () {
  console.log('hi!');
});

// ES6:
['a', 'b'].forEach(() => console.log('hi!'));

// => hi!
// => hi!
```

#### First parameter: Element

If we pass one parameter, it will be equal to each element on every iteration.

```javascript
// ES5:
//                        placeholder, can be anything (naming has to make sense though)
//                            |
[1, 2, 3, 4].forEach(function (element) {
  console.log(element * 2); // we can access each element inside!
});

// ES6:
[1, 2, 3, 4].forEach(element => console.log(element * 2));

// console:
// => 2
// => 4
// => 6
// => 8
```

#### Second parameter: Index

```javascript
const raceResults = ['Helen', 'John', 'Peter', 'Merry'];
raceResults.forEach(function (elem, index) {
  console.log(elem + ' finished the race in ' + (index + 1) + ' position!');
});

// => Helen finished the race in 1 position!
// => John finished the race in 2 position!
// => Peter finished the race in 3 position!
// => Merry finished the race in 4 position!
```

:pencil: **Practice time**

Write the function above using arrow function approach.

#### Your turn

Can you guess the output of this?

```javascript
function printStars(howMany) {
  console.log('*'.repeat(howMany));
}

[1, 2, 3, 4, 5].forEach(function (num) {
  printStars(num);
});
```

### String `.split()` method

It might sound like a mistake to introduce a string related method in the array lesson, but we have a good reasoning behind it.

:::info
The [split](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split) method allows us to separate a string into pieces and will **return** all the pieces as **elements of a new array**.
:::

So, imagine we have a loooong string and we want to count the number of words inside:

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/gwWQYX/?height=265&theme-id=0&default-tab=js%2Cresult&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/gwWQYX/'>gwWQYX</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

Step one would be to take the string and put each word separately into an array. How? Applying the _split_ method to a string, we will need to set the **separator**, in this case a space (" "), which is the character where the split is going to cut the string and add the rest of the characters before it, and then do it again every time it finds that character.

## Summary

Arrays are data structures that allow us to store a collection of elements, doesn't matter the type. We can manipulate arrays, getting, changing, adding or deleting their elements.

We also have several ways to go through all of their values, like loops such us _for_, or methods like _forEach_.

## Extra Resources

- [MDN Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [JavaScript Arrays - tips, tricks and examples](https://www.codingame.com/playgrounds/6181/javascript-arrays---tips-tricks-and-examples)
- [.split()](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/String/split)
- [Does it mutate](https://doesitmutate.xyz/)
