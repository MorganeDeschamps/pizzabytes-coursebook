<!-- ![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# CSS | Transitions & Animations -->

## Learning Goals

After this unit, you'll be able to:

- Create transitions using CSS3 Transitions module
- Explain the differences between transitions and animations
- Understand how to create animations using animation blocks
- Create keyframes
- Apply animation properties

## Introduction

Adding animation to your website is a powerful way to drive users' attention to certain areas of your product and add interest to your interface. After all, our brains are naturally built to track moving objects.

When done well, animations can add valuable interaction and feedback, as well as enhance the emotional experience, bring delight, and add personality to your interface. In fact, to animate means to bring to life.

## CSS3 Transitions

CSS transitions are nothing other than mutations of DOM elements by the use of CSS. Usually, property changes take effect immediately. Take a look at the example in this CodePen:

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/GjEEGd/?height=265&theme-id=0&default-tab=html,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/GjEEGd/'>CSS-transitions-1</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

:::warning
:warning: Click on Edit on CodePen if you want to code along.
:::

In the code above, you'll find two sets of rules for the same element.

- The first one is for the class `.box` and it describes the regular box style.
- The second one is `.box:hover` and it describes the box style when the mouse hovers on the element.

When the user's mouse hovers over the element, the change is instantaneous. **CSS transitions** let us adjust this response's speed to happen over a period of time.

Add this code to the `.box:hover` class and try again:

```css
transition-property: width;
transition-duration: 2s;
transition-timing-function: linear;
transition-delay: 1s;
```

:::success
:ballot_box_with_check: It is possible to alter the appearance and behavior of an element whenever a state change takes place: hovered over, focused on, active, or targeted.
:::

Let's explain the code above.

### Syntax

The CSS3 Transitions module introduces a number of properties, which together can be used to specify:

- `transition-property`: Specifies the CSS property (or properties) to be transitioned.
- `transition-duration`: Specifies the duration of the transition.
- `transition-timing-function`: Specifies the timing function of the transition.
- `transition-delay`: Specifies an optional delay.

#### `transition-property`

CSS transitions let you decide which properties to animate (by listing them explicitly). The first step to create a transition effect is to specify which CSS property (or properties) will be affected:

```
transition-property: none | all | [ <IDENT> ] [, <IDENT> ]*
```

The `transition-property` can be configured in two different ways:

- we could set the specific list of properties that will be affected:
  ```css
  transition-property: width, height, border;
  ```
- but it also accepts one of two keywords: `all` (the default value) or `none`:
  ```css
  transition-property: all;
  ```
  ```css
  transition-property: none;
  ```

Add this line to your CodePen exercise to transform the element's width:

```css
transition-property: width;
```

:::warning
:exclamation: Note: When the property is set to `none`, it will not create any kind of animation. This is used to avoid inheritance of transition in nested elements.
:::

#### `transition-duration`

The `transition-duration` property accepts a comma-separated list of times, specified in seconds or milliseconds, which determine how long the corresponding properties (specified using transition-property) take to complete their transition.

```
transition-duration: <time> [, <time>]*
```

The code in our transition rule will be **triggered by the mouse hovering over the element**. When this happens, it will transform the element (making it bigger) until it reaches the `200px` established in the hover state.

Steps between initial state and final state of a transition are often called _implicit transitions_. These are implicitly defined and automatically calculated by the browser.

Add this line to your CodePen exercise:

```css
transition-duration: 2s;
```

:::warning
:exclamation: Note: The `transition-duration` property’s default value is 0, meaning that the transition is instantaneous. The only value required to create a transition is that of **transition-duration.**
:::

What happens if the `transition-duration` property is not specified in the transition effect?

#### `transition-timing-function`

The `transition-timing-function` property is used to specify how the pace of the transition changes over its duration.

The easy way to implement it is by specifying a number of pre-defined keywords: **ease, linear, ease-in, ease-out or ease-in-out**

```
transition-timing-function: <timing-function> [, <timing-function>]*
```

with

```
<timing-function> = ease | linear | ease-in | ease-out | ease-in-out
or
<timing-function> = cubic-bezier(<number>, <number>, <number>, <number>)
```

If no timing function is specified, the default value is ease. Let's make our transition linear by adding:

Add this line to your CodePen exercise to transform the element's width:

```css
transition-timing-function: linear;
```

#### `transition-delay`

The final step when creating a transition effect is to specify an optional delay using the `transition-delay` property. It accepts a comma-separated list of times, specified in seconds or milliseconds, which in this case determines the length of time between the transition being triggered and the transition starting. The default value is 0.

`transition-delay: <time> [, <time>]*`

Add this line to your code, change the number of seconds to see the differences. What happens if you set a negative value?

```css
transition-delay: 1s;
```

:::warning
:exclamation: Negative values are accepted for transition-delay. When supplied, the transition will commence as soon as triggered. However it will appear to have begun execution at the specified offset.

ie, the transition effect will begin part-way through its cycle (see the examples section below for an example).
:::

### The transition shorthand property

Instead of writing four lines of code to create a transition, we can simplify our code by use the transition shorthand property. The syntax is:

```css
transition: <transition-property> <transition-duration> <transition-timing-function> <transition-delay>;
```

Change the code above to match this syntax:

```css
transition: width 2s linear 1s;
```

### Multiple transitions

It is possible to transform multiple properties at the same time. The transition shorthand property can be used to define multiple transitions, using a comma-separated list. Take a look a this code:

```css
transition: width 2s ease-in 1s, height 4s, background-color 6s;
```

Copy the code above to the previous example to watch the changes.

:::info
:moneybag: Bonus: The **CSS transform property** lets you modify the coordinate space of the CSS visual formatting model. Using it, elements can be translated, rotated, scaled, and skewed. Use the transform property to rotate the element 180 degrees and create a translation to make your box fly!
:::

Our code in the `box:hover` class will be something like this:

```css
transform: rotate(180deg);
```

Meanwhile, our transition ends up like this:

```css
transition: width 2s ease-in 1s, height 4s, background-color 6s, transform 2s;
```

### Animations

#### The Building Blocks of Animations

CSS animations are a combination of two basic components: a style, describing the CSS animation, and a set of `@keyframes` indicating the states of the animation and possible intermediate steps.

Let's animate this Ironhack hexagon in CodePen :smile:

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/vXWYjK/?height=265&theme-id=0&default-tab=css,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/vXWYjK/'>css-animations-1</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

:::warning
:warning: Click on Edit on CodePen if you want to code along.
:::

#### Keyframes

As they define what the animation looks like at each stage of the animation timeline, they constitute the essential foundation of the animations.

To make our hexagon slide in, we are going to change its position using keyframes:

```css
@keyframes myslidein {
  0% {
    margin-left: 100%;
    width: 300%;
  }

  100% {
    margin-left: 0%;
    width: 100%;
  }
}
```

Each @keyframes is composed of:

- **Name of the animation**: A name that describes the animation, for example, bounceIn. You can make up the name, it could be anything, but we recommend using some descriptive one so anyone can understand what's the animation about. :wink:
- **Stages of the animation**: Each stage of the animation is represented as a percentage. `0%` represents the beginning state of the animation. `100%` represents the ending state of the animation. Multiple intermediate states can be added in between. Use percentages to define the different stages of the animation.
- **CSS Properties**: The CSS properties defined for each stage of the animation timeline.

The `@keyframes` are added to your main CSS file.

#### Animation properties

Animation properties do two things: assign the @keyframes to the element that you want to animate and define how it is animated. To create an animation you must add two properties:

###### `animation-name`

It is the name of the animation defined in the @keyframes.

###### `animation-duration`

The duration of the animation in seconds or milliseconds.

Continuing with the above CodePen, add animation-name and animation-duration to the container class.

:::warning
:bulb: If we use our container class, we can modify the position of the hexagon from without.
:::

```css
animation-name: myslidein;
animation-duration: 3s;
```

#### More animation properties

Although the name and duration are enough properties to define an animation, there are other sub properties we can define:

- `animation-delay`: Allows you to specify in seconds or milliseconds when the animation will start. A positive value will start the animation after it is triggered. A negative value will start the animation at once, but starts as many seconds as specified into the animation.

- `animation-direction`: Configures whether or not the animation should alternate direction on each run through the sequence or reset to the start point and repeat itself. Values are: `normal` (default), `reverse`, `alternate` or `alternate-reverse`.

- `animation-iteration-count`: Defines the number of times the animation should repeat. Its value could be: - A specific number of iterations (default is 1). - `infinite` to repeat it forever. - `initial` to set the iteration count to the default value. - `inherit` to inherit the value from the parent.

- `animation-play-state`: Lets you pause and resume the animation sequence.

- `animation-timing-function`: Defines the speed curve or pace of the animation, Predefined timing options are: `ease`, `linear`, `ease-in`, `ease-out`, `ease-in-out`, `initial`, `inherit`. You could even create your custom timing functions using [`cubic-bezier` class](https://developer.mozilla.org/en-US/docs/Web/CSS/timing-function). The default value is ease, which starts out slow, speeds up, then slows down. [play around](http://cubic-bezier.com/#.17,.67,.83,.67)

- `animation-fill-mode`: This property is a little confusing, but once understood it is very useful. It specifies if the animation styles stay visible before or after the animation plays. Its values could be: - `backwards`: before the animation (during the animation delay), the styles of the initial keyframe (0%) are applied to the element. - `forwards`: After the animation is finished, the styles defined in the final keyframe (100%) are retained by the element. - `both`: The animation will follow the rules for both forwards and backwards, extending the animation properties before and after the animation. - `normal` (default): The animation does not apply any styles to the element, before or after the animation.

#### Animation Property Shorthand

Each animation property can be defined individually, but for cleaner and faster code, it’s recommended that you use the animation shorthand. All the animation properties can be added to an animation in one step by defining properties in the following order:

```css
animation: [animation-name] [animation-duration] [animation-timing-function] [animation-delay] [animation-iteration-count] [animation-direction] [animation-fill-mode]
  [animation-play-state];
```

:::info
:warning: For the animation to function correctly, we need to follow the proper shorthand order AND specify at least the first **two values.**
:::

The next step is to define the `slidein` animation using keyframes.

#### Multiple Animations

To add multiple animations to a selector, you simply separate the values with a comma. Here’s an example:

```css
.div {
  animation: myslidein 2s, myrotate 1.75s;
}
```

## Transitions vs. Animations

<img src="https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_de9072d0847fc84e38ab1fbc6ee8a5f0.png" style="width:48%; margin:0 2% 20px 0;">
<img src="https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_124b8aca585c9626cb20541ec655726c.png" style="width:48%;margin:0 0 20px 2%;">

|                                  | Transitions                                                                                                                                                                      | Animations                                                                                                                                                     |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Starting Them**                | Require a trigger to run. The trigger may be one of the events listed in the last section or it might be JavaScript, but the transition needs something outside itself to start. | Do not need a trigger. They can respond to a trigger, but one isn’t needed to start the animation. Animations can run automatically when the page first loads. |
| **Defining Intermediate Points** | Limited to an initial and final state                                                                                                                                            | Animations can include as many intermediate states (keyframes) as desired in between the initial and final state.                                              |
| **CSS Iteration**                | Can’t change CSS properties.                                                                                                                                                     | Can change property values inside their keyframes.                                                                                                             |
| **Looping**                      | They are not designed for looping                                                                                                                                                | Have no problem for looping.                                                                                                                                   |

### Exercise

In the next CodePen, you will find three geometric figures (all of them created using only CSS). Your mission is to create a different animation for each one of them:

- The Circle: You should make the circle bounce forever.
- The square: With a 5s delay, make it fly to the right.
- The triangle: Make it move in zigzags to the bottom of the page and then come back to its actual position.

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/yaPvjg/?height=265&theme-id=0&default-tab=css,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/yaPvjg/'>css-animations-exercise</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

### CSS animation vs. Script-driven animation

There are three key advantages to CSS animations over traditional script-driven animation techniques:

- They're easy to use for simple animations; you can create them without even having to know JavaScript.
- The animations run well, even under moderate system load. Simple animations can often perform poorly in JavaScript (unless they're well made). The rendering engine can use frame-skipping and other techniques to keep the performance as smooth as possible.
- Letting the browser control the animation sequence lets the browser optimize performance and efficiency by, for example, reducing the update frequency of animations running in tabs that aren't currently visible.

## Summary

Now, you are able to create amazing transitions and animations. Your websites will be more **interactive** and appealing to users by letting them interact and trigger transitions with your site. Also, your websites will have automatic motion by using complex animations properties and keyframes. With those basic properties, the **possible animations** you can create are endless!

## Extra Resources

- [CSS animated properties](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties) - Not all CSS properties can be animated, this is the list of CSS properties that accept CSS Animations or CSS Transitions.
- [David Khourshid:](https://www.youtube.com/watch?v=lTCukb6Zn3g) - Reactive Animations with CSS
- [CSS Levels Up](https://www.youtube.com/watch?v=UpVj5azI-iI) - A very cool video explaining next CSS features.
- [Animate.css](https://daneden.github.io/animate.css/) - A library with dozens of fun animations to get you started and use on your projects.
