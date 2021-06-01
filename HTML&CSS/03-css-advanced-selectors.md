<!-- ![](https://i.imgur.com/1QgrNNw.png)

# CSS | Advanced Selectors -->

## Learning Goals

After this lesson, you will be able to:

- Select elements using basic selectors
- Select elements combining different selectors
- Select elements based on their relationship to other elements
- Select elements based on their attributes

## Combining CSS Selectors

Before learning about combined CSS selectors, it's a good idea to understand the document tree in the [Document Object Model](https://en.wikipedia.org/wiki/Document_Object_Model). If you understand the document tree concept, then CSS selectors will be much easier to understand and therefore apply.

All HTML documents can be represented as trees. Each level of the tree is described in the same manner as a human family tree, with ancestors, descendants, parents, children and siblings. CSS selectors can describe elements in the document tree.

For example, in any HTML document, the `<body>` element is the ==ancestor== of all other elements shown on the page. On the contrary, a ==descendant==refers to any element that is connected but lower down the document tree - no matter how many levels lower.

Parents and children work the same. A ==parent== is an element that is directly above and connected to an element in the document tree; a ==child== is directly below and connected to an element in the document tree.

```html
<ul>
  <li class="menu-item"></li>
  <li class="menu-item"></li>
</ul>
```

In this example, the `<ul>` is a parent to every `<li>` . Those `<li>` elements are its children.

## Selecting Descendants

### Direct Descendants (Children)

:::info

```css
parent > child {
  property: value;
}
```

:::

The [> selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Child_selectors) separates two selectors and matches only those elements matched by the second selector that are direct children of elements matched by the first.

Imagine you have several lists and you want to style them all. All _li_ tags inside the menu _ul_ tag will have 50px height and 100px width.

One option would be to assign a class to every `li` tag in the menu list, then write the properties for them.

```html
<ul>
  <li class="menu-item"></li>
  <li class="menu-item"></li>
  <li class="menu-item"></li>
  <li class="menu-item"></li>
  <li class="menu-item"></li>
</ul>
```

```css
.menu-item {
  width: 100px;
  height: 50px;
}
```

But.. we have an easier way: [The child selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Child_selectors)!

The `> combinator` will select those elements matched by the second selector that are direct children of elements matched by the first.

If we add a `menu` id to the `ul`, we can simply select all of its `li` children by using the `#menu > li` selector:

```html
<ul id="menu">
  <li>1</li>
  <li>2</li>
  <li>3</li>
  <li>4</li>
  <li>5</li>
</ul>
```

```css
#menu > li {
  width: 100px;
  height: 50px;
}
```

Now we have a rule saying that every `li` child of the element with `menu` id will have that width and height.

### Descendant Selector

:::info

```css
selector1 selector2 {
  property: value;
}
```

:::

The [Descendant Selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Descendant_selectors) matches those elements **matched by the second selector**, but only those, which **have an ancestor element, matched by the first selector**.

Let's take this HTML fragment for a second and think about how we would target the `em` inside the `li`, without targeting the `em` inside the `p`:

```html
<p>Ironhack <em>Descendant</em> Selectors</p>
<ul>
  <li>item 1</li>
  <li>item 2</li>
  <li><em>item 3</em></li>
</ul>
```

Well, we could of course add a class to the second `em`, or we could add an ID as well. However, using this combination of selectors helps us match elements without having to mess around with the HTML too much.

![](https://i.imgur.com/YdqDUNh.png)

One of the goals of this course is to teach you to keep the HTML as tidy, clean, and compact as possible. These selectors will help you target elements without having to add classes everywhere:

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/amBQkV/?height=265&theme-id=light&default-tab=html,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/amBQkV/'>amBQkV</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

:::warning
:zap: Remember to click **Edit on CodePen** so you can code along and play around
:::

Here, the rule that we wrote `ul em` will apply to all `em` elements that are descendants of an `ul`. Therefore, the first `em` inside the `p` will not be affected.

Useful right?

## Selecting Siblings

### Adjacent Sibling

:::info

```css
formerElement + targetElement {
  property: value;
}
```

:::

This is referred to as an [adjacent selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Adjacent_sibling_selectors) or next-sibling selector. It will select only the specified element that immediately follows the former specified element

This selector allows you to get the elements that are next to each other:

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/amBQEG/?height=265&theme-id=light&default-tab=html,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='https://codepen.io/ironhack/pen/amBQEG/'>Example</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

If we look carefully at the CSS code:

```css
/* All DIVs Green by default */
div {
  background-color: green;
}

/* ID=former... make it red*/
#former {
  background-color: red;
}

/* First adjacent sibling of #former is YELLOW */
#former + div {
  background-color: yellow;
}
```

## Multiple selection

:::info

```css
selector1,
selector2 {
  property: value;
}
```

:::

Imagine we want all our titles `h1`-`h6` to be colored blue. We can add a separate rule for `h1`, another rule for `h2`, another for `h3`... but there is a better way. The multiple selections allow us to apply the same list of rules to different elements:

```css
h1,
h2 {
  color: blue;
}
```

And this method can work with more complicated selectors as well, although you should probably put each selector in a different line for ease of reading. For example, we may want different elements to have background-color yellow:

```css
.todo-list > li,
h2 + .red-box,
h2 {
  background-color: yellow;
}
```

You can mix selectors as much as you need to create awesome and beautiful web pages!

## Attribute Selector

:::info

```css
element[attr-name='value'] {
  property: value;
}
```

:::

We can select elements by tag name, why not select an element by it's attributes? Let's see how this works:

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/GjAWAo/?height=265&theme-id=light&default-tab=html,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/GjAWAo/'>GjAWAo</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

Only the links with the word `hack` in their `src` attribute are affected by the rule, and therefore are show in green.

Another examples of this same selector:

| Selector             | What does it select?                                                                                                     |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| `[attribute]`        | All elements with the specified attribute                                                                                |
| `[attribute=value]`  | All elements where the specified attribute is equal to ‘value’                                                           |
| `[attribute~=value]` | All elements with an attribute which has a list of whitespace-separated values, one of which is exactly equal to ‘value’ |
| `[attribute|=value]` | All elements with an attribute which has a hyphen-separated list of values beginning (from the left) with ‘value’        |
| `[attribute^=value]` | All elements with an attribute beginning with ‘value’                                                                    |
| `[attribute$=value]` | All elements with an attribute ending with ‘value’                                                                       |
| `[attribute*=value]` | All elements with an attribute containing the substring ‘value’                                                          |

Here you have one more example to play around:

<iframe height="485" style="width: 100%;" scrolling="no" title="attr-selectors-css" src="https://codepen.io/abernier/embed/NWKmera?height=485&theme-id=0&default-tab=html,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/abernier/pen/NWKmera'>attr-selectors-css</a> by Antoine BERNIER
  (<a href='https://codepen.io/abernier'>@abernier</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

## Summary

In this Unit, we have learnt:

- How to select descendants `selector1 selector2` and children `selector1 > select2` of a node
- How to select siblings `selector1 + selector2` of a node
- How to combine selector rules `selector1, selector2`
- How to select elements based on their attribute values `element[attr="value"]`

## Extra Resources

- [Css-tricks](https://css-tricks.com/attribute-selectors/) | Interesting article explaining further uses of attribute selectors in the real world.
- [CSS Selectors](http://www.w3schools.com/cssref/css_selectors.asp) | All selectors available
