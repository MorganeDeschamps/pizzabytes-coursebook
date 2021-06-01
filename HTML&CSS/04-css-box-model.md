<!-- ![](https://i.imgur.com/1QgrNNw.png)

# CSS | Box Model -->

## Learning Goals

After this unit you will be able to...

- Understand margin, padding and border properties, and the differences between them.
- Apply borders, paddings and margins to block elements.
- Use border radius property to set rounded corners to our elements or even turn them into circles.
- Eliminate the spacing behavior of the `border` and `padding` properties.
- Understand how these properties affect the element's properties.

## Introduction

In order to fully comprehend CSS-based web design you have to learn something really basic: every HTML element is a **rectangular box**.

The _CSS Box model_ is a series of concentric squares used to model the way elements take up space in a web page.

We will be discussing each aspect of the following image in detail throughout the lesson:

![](https://i.imgur.com/LF204FU.gif)

**Don't worry if it doesn't make sense yet!** Just remember to keep it around as reference as we go through each step.

## Setup

In this learning unit we will iterate on this [CodePen](http://codepen.io/ironhack/pen/ALAKNO). We will apply changes on a `<div>` to learn the new concepts.

At the end of the unit, you will have a clear example of borders, paddings and margins, and the effects they have on the `div`.

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/ALAKNO/?height=265&theme-id=0&default-tab=css,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/ALAKNO/'>CSS Box Model</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

:::warning
:zap: Remember to click **Edit on CodePen** so you can code along and play around
:::

In the code below, the `<div>` element has a `background-color` of green. This will allow us to see its default spacing.

We have also applied a fixed `width` to help us notice what happens when each property is applied to the `<div>`.

## Border Property

The `border` property allows you to set the border of an element.

You can specify three values for this property: `border-width`, `border-style` and `border-color`. The `border-width` and `border-color` properties have default values, so if you don't specify one of them, it will still have a value.

If borders are undeclared, they are either zero or the browser default value. All browsers have their own style, you have to use a [css reset file](http://cssreset.com/what-is-a-css-reset/) to neutralize them and avoid conflicts with your own styles.

Let's add a border to our `<div>`:

```css
border: 1px solid #17212e;
```

The result will be something like this:

![](https://i.imgur.com/BJJOTfO.png)

#### Border properties

In the previous example, the border is defined with 3 values:

- **`width`**(`1px`): we can specify any [size unit](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Values_and_units) to set the border width. We can also use the `border-width` property to do that.
- **`style`**(`solid`): we can specify any [border style](https://developer.mozilla.org/en-US/docs/Web/CSS/border-style) value, depending on the design you want to have. We can also use the `border-style` property to do that. **This property doesn't have a default value**. If you don't specify it, your border won't appear.
- **`color`**(`#17212e`): finally, we can specify a color, in any of the formats we have already seen. Again, we can also use the property `border-color` to do that.

The shorthand:

```css
border: 1px solid #17212e;
```

is equivalent to:

```css
border-color: #17212e;
border-style: solid;
border-width: 1px;
```

Generally, it's better (and faster) to use the shorthand.

### Spacing behavior

If we take a look at our CSS, the `<div>` element should have a width of `170px`. After applying the border, the width is not `170px` anymore. It's `172px`. Why?

When you apply a border to an element, it increases its effective width, even if you have specified a fixed width. Our element's border is `1px` width. The total width of the `<div>` will be `172px`:

- `170px` `<div>` width
- `+ 1px` `border-left`
- `+ 1px` `border-right`
- `= 172px`

When you apply a border to an element, it modifies the total width of that element.

### Single borders

What if you only want to have a border in one side of the element?

Let's suppose that you just want to have the bottom border in your `<div>`. There are two different ways to do it.

Number one:

```css
border-bottom: 1px solid #17212e;
```

The other way is a little bit longer. It involves setting the `border` value with the `style` and `color` property. Then, set the `border-width` as follows:

```css
border: solid #17212e;
border-width: 0 0 1px 0;
```

As you can see, the `border-width` receives _4 different values._ Those values correspond to:

```css
border-width: [border-top] [border-right] [border-bottom] [border-left];
```

The`border-bottom` has a value of `1px`, and is the only one displayed.

You can use this technique with all the `border` properties, but it's not common:

```css
border-color: red blue green yellow;
border-style: solid dashed dotted double;
```

We will cover this nomenclature in more detail in the next section.

At this point, your CSS in CodePen should be:

```css
div {
  background-color: #00d1ae;
  border: 1px solid #17212e;
  width: 170px;
}
```

### Border-radius Property

Related to the `border` property, we have the `border-radius`. The `border-radius` property allows you to define how rounded border corners are. **We can even create a circular `<div>`!!**

To set a rounded border in our element, we can do this:

```css
border-radius: 12px;
```

It will create a 12px border radius. As we did before with the border property, you can set the border radius values individually. The syntax is:

`border-<top|bottom>-<left|right>-radius`

If you want to have a 12px border radius just at the top left border, you have to set the property as follows:

```css
border-top-left-radius: 12px;
```

Finally, you can get a circular `<div>` with this property. To do that, you have to set the properties `width` and `height` with the same value, and the `border-radius` property to 50%:

```css
.circular-div {
  background-color: #ccc;
  border-radius: 50%;
  height: 100px;
  width: 100px;
}
```

In the Extra Resources section, there is a link to a video of [Lea Verou](http://lea.verou.me/) explaining how border-radius works in depth. Check it out if you want to understand it better :)

## Padding Property

### What is `padding`?

The `padding` property sets the space between the content and the border of an element. Add some padding to your code:

```css
padding: 10px 10px 10px 10px;
```

The image below, shows extra space between the content and the border of the `<div>`:

![](https://i.imgur.com/M2ZnyGd.png)

### Spacing behavior

Just like the `border` property, the `padding` property increases the `<div>`'s size. The total width won't be the specified in the CSS, it will be the sum of all the modifiers. In this case, it will be 192px:

- 170px `<div>` width
- `+ 10px` `padding-left`
- `+ 10px` `padding-right`
- `+ 1px` `border-left`
- `+ 1px` `border-right`
- `= 192px`

Don't forget about the `border` when you calculate the total `width` of the `<div>`.

### Padding values

As we have seen, we can specify different values to the padding. It's behavior is the same that we saw in the `border-width` property.

```css
padding: [padding-top] [padding-right] [padding-bottom] [padding-left];
```

We don't have to set the four values every time. Similarly to the border property, we can indicate one, two, or three values. If we do that, each value affects one side of the element:

```css
padding: 10px 20px 15px; /* padding-top 10px */
/* padding-right and padding-left 20px */
/* padding-bottom 15px */
```

```css
padding: 10px 20px; /* padding-top and padding-bottom 10px */
/* padding-right and padding-left 20px */
```

```css
padding: 10px; /* All the paddings are set to 10px */
```

Change your code and set the padding to `10px` on every side of the `<div>`:

```css
padding: 10px;
```

At this point, your CSS should look like this:

```css
div {
  background-color: #00d1ae;
  border: 1px solid #17212e;
  padding: 10px;
  width: 170px;
}
```

## Box-sizing Property

### Introduction

As we have seen, when we apply a border or padding to a block element, its width and height change. Sometimes, we have to fit the elements in a design, and there's no space to change width and heights. So, how can we avoid this extra space in our elements? How can we have a `<div>` with 170px of width, a 1px `border` and 10px of `padding`?

### What is `box-sizing`?

The `box-sizing` property is used to alter the default box model used to calculate width and height of the elements. This property _is not supported, by default, by all the browsers_, although it's possible to use it to emulate the behavior of browsers that don't support it correctly.

**Okay, what does it mean?**

Let's go back to our example in CodePen. We have calculated the total space used by our `<div>`. Setting the `box-sizing` with the correct value, we can reduce it to 170px of width:

```css
box-sizing: border-box;
```

Now, you can check out our `<div>` width size to see how it uses just 170px. The property can have two different values:

- content-box: it's the default value. The width and height properties are measured including only the content, but not the padding, border or margin.
- border-box: the width and height properties include the content, the padding and border, but not the margin.

### Spacing behavior

Setting the `box-sizing` property we reduce the current spacing of the element. Not, it's 170px:

- 170px `<div>` width
- `+ 10px` `padding-left`, that increases `0px` with `box-sizing`.
- `+ 10px` `padding-right`, that increases `0px` with `box-sizing`.
- `+ 1px` `border-left`, that increases `0px` with `box-sizing`.
- `+ 1px` `border-right`, that increases `0px` with `box-sizing`.
- `= 170px`

Don't forget about the `border` when you calculate the total `width` of the `<div>`.

## Margin Property

### What is `margin`?

The `margin` property sets the space between the border of an element and the _other elements around it_. If no elements are around, it will set the space between the element and the `<body>` tag.

Add some margin to your code and see what happens:

```css
margin: 10px 10px 10px 10px;
```

As you can see, the `<div>` now has space between each side and the `<body>`.

### Spacing behavior

When you apply margin, the `<div>` size remains the same: `170px`. But the space occupied in the HTML is bigger. It's is now `190px`:

- `170px` `<div>` width
- `+ 10px` `padding-left`, that increases `0px` with `box-sizing`.
- `+ 10px` `padding-right`, that increases `0px` with `box-sizing`.
- `+ 1px` `border-left`, that increases `0px` with `box-sizing`.
- `+ 1px` `border-right`, that increases `0px` with `box-sizing`.
- `+ 10px` `margin-right`
- `+ 10px` `margin-left`
- `= 190 pixels`

You should consider these sizes in the future when you're creating a layout with HTML, or you may be in for a surprise.

### Margin values

The `margin` property also works like `padding` property. You can specify the margin values by declaring them as follows:

```css
margin: [margin-top] [margin-right] [margin-bottom] [margin-left];
```

Again, we don't have to indicate every value.

```css
margin: 10px 20px 15px; /* margin-top 10px */
/* margin-right and margin-left 20px */
/* margin-bottom 15px */
```

```css
margin: 10px 20px; /* margin-top and margin-bottom 10px */
/* margin-right and margin-left 20px */
```

```css
margin: 10px; /* All the margins are set to 10px */
```

**Play with the example adding borders, paddings, margins and colors. You should be able to do whatever you want with all of them :)**

:memo: **Time to practice**

[Lorem Ipsum](http://www.lipsum.com/) is a website where you can generate random content to put to your designs. Let's create a card with the first paragraph that lipsum.com generates. You should get a result like this:

![](https://i.imgur.com/69OBWCJ.jpg)

Here we provide you some tips to do the exercise:

- You should work with three different divs: card (gray), title (green) and content (blue).
- The title is separated by 10px on the top and right sides, 20px from the left side and 40px from the content. It also has a 2px border.
- The content is separated by 10px on the left and right sides. On the top and the bottom, there is an space of 5px.
- You can use the colors that you want. If you want to use the colors you have in the image, those are:
  - Card background color: #E9E6E6
  - Title background color: #78F0B7
  - Title border color: #178C55
  - Content background color: #24CCDA

**Good luck, and may the force be with you :)**

## Summary

In this unit, you learned about box model and its properties

- The **Border property** adds a border to the element. The border width is added to the total width and height of the element. We can set the border width, style and color through its values.
- The **Padding property** references the space between the border of the element and its content. The padding is added to the total width and height of the element too.
- The **Box-Sizing property** helps you to avoid the spacing created by the `padding` and/or `border` properties.
- And the **Margin property** references the space between the border and the rest of elements in our website. It doesn't affect the element's width and height. It helps you to position elements in a particular place.

## Extra Resources

- [MDN Border](https://developer.mozilla.org/en-US/docs/Web/CSS/border) - Mozilla Developer Network summary of the border property.
- [MDN Padding](https://developer.mozilla.org/en-US/docs/Web/CSS/padding) - Mozilla Developer Network summary of the padding property.
- [MDN Box-Sizing](https://developer.mozilla.org/en/docs/Web/CSS/box-sizing) - Mozilla Developer Network summary of the box-sizing property.
- [MDN Margin](https://developer.mozilla.org/en/docs/Web/CSS/margin) - Mozilla Developer Network summary of the margin property.
- [The CSS Box Model](https://css-tricks.com/the-css-box-model/) - This article explains some of the consequences of applying these properties to the elements.
- [The border-radius](https://www.youtube.com/watch?v=b9HGzJIcfDE). Video of Lea Verou talk in the CSS Conf US in 2013 explaining the border-radius property.
