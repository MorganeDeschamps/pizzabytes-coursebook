<!-- ![](https://i.imgur.com/1QgrNNw.png)

# CSS | Responsive Web Design -->

## Learning goals

After this lesson, you will be able to:

- Understand what is Responsive Web Design
- Create a good Responsive Design on your website
- Understand and apply the Mobile-First principle
- Create different media queries depending on the viewport size
- Set responsive styles on the `font-size` and `line-height` properties
- Use different tools to work with your responsive designs

## Introduction to Responsive Web Design

We all have a computer. We all have a cell phone. Some of us also have a tablet. Maybe someone has a smart TV. What does this mean for us? Does it mean that when a user visits our website, we won't know which device will she be using? How will it adapt the appearance to show nicely on different devices? **Responsive Web Design to the rescue!**

Nowadays, the number of users that will visit our website from a mobile device is greater than the number of visitors from other devices. Since there are many types of device resolutions, we will have to adapt our design depending on which device visits our site. This is the goal of Responsive Web Design (RWD).

RWD is the practice of building a website that is suitable to work on every device and every screen size, no matter how large or small, mobile or desktop. It's focused around providing an intuitive and gratifying User Experience for everyone.

## How to do a good Responsive Design?

We know the design should change depending on the device, but we **don't have to be focused on the device. Instead, we have to think in the viewport size**.

We don't have to create a specific design for the last iPhone or Samsung device. You have to create a design for a viewport with a width of 680px. Why?

The goal we want to achieve is not to have a perfect website in every possible single device _(that would take super long and would make development so complex!)_. Instead, we will group all the devices with a similar screen size into one viewport.

We will see this deeply in the **Media Queries** section.

## Mobile First

We could think that the normal workflow when creating a website is:

- I create the website on my computer, so the site appears perfect on my monitor.
- I visit then the website with my cell phone. All the content is probably too small, and I can't see it correctly.
- I then create a new design for the cell phone so that it will appear well on the cell phone.
- Then I visit the website with my tablet... I realize the design could be better.
- I add a new design with another viewport size. In this case, for the tablet.
- etc.

We avoid this concern with the **Mobile-First** approach.

We will not create websites from large screens (computers) and then translate them into smaller screens (mobile). We will do the opposite: **we will design the mobile view first and then add more elements incrementally for larger resolutions**.

This will help us keep just the necessary elements for our mobile version. Mobile visitors don't have to see anything but the necessary information. This technique is very useful to ensure a good UI/UX experience. It's the best way to keep the user focused on what is really important.

Another reason to do Mobile First is to avoid loading unnecessary resources and assets. We add an image to the mobile version just if it's necessary, and it adds some value to the design. We also have to add just the necessary scripts to work on mobile.

:::warning
:zap: Remember that mobile phones can commonly use 3G connectivity, which is very slow. Avoid unnecessary assets in your mobile version to increase loading speed and reduce data usage, which will translate into a better user experience.
:::

## Media queries

A media query is an optional media type with zero or more expressions that limit the style sheets' scope by using media features: width, height, etc.

In other words: we use a media query to set the viewport sizes where different styles will be applied. We can consider each one like a step in the design. While we resize the browser, we see the different styles depending on the current resolution.

### Create a media query

The syntax to create a media query is the following:

:::info
CSS media query within a stylesheet:

```css
@media [(media-features) ] {
  // Styles
}
```

CSS media query within a stylesheet:

```html
<link rel="stylesheet" media="(media-features)" href="styles.css" />
```

:::

The `[media-features]` are optional, and they will specify where to apply the styles indicated in the CSS or the specified file.

When a media query is true, the corresponding style sheet or style rules are applied, following the normal cascading rules. Style sheets with media queries attached to their `<link>` tags will still download even if the media queries would return false.

We will work over this CodePen to learn how to apply media queries to our design:

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/ozZbmP/?height=265&theme-id=0&default-tab=css,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'></iframe>

:::warning
:zap: Remember to click **Edit on CodePen** so you can code along and play around
:::

As you can see, we just have a `div` with a class. In the CSS, we set the width and height with a fixed value and a background color. We will add different media queries and see how they change the styles by resizing the browser window.

First of all we will add a media query to change the background color when the resolution is bigger than 1000px:

```css
@media (min-width: 1000px) {
  .responsive-div {
    background-color: blue;
  }
}
```

:::warning
:point_up: Due to media-queries themselves have no [CSS specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity), the above code MUST be written AFTER the previous CSS rule for `.responsive-div`.
:::

Our `<div>` will change the background color. This is because the browser (that, in this case, is our viewport) size is bigger than 1000px. If we resize the window, we will see how it changes its color when the resolution becomes smaller than 1000px.

We can compose complex media queries using logical operators, including `not`, `and` and `only`. The `and` operator is used for combining multiple media features into a single media query.

Let's create a media query to change the background color when the resolutions is smaller than 1000px and bigger than 650px:

```css
@media (min-width: 650px) and (max-width: 999px) {
  .responsive-div {
    background-color: green;
  }
}
```

Now, the `<div>` color will be:

- Blue: resolution bigger than 1000px.
- Green: resolution between 650px and 999px.
- Red: resolution smaller than 650px.

We can set up a lot of different options. Check out the [MDN article "Using media queries"](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) to see them all.

### Viewport meta tag

Viewport meta tag allows us to control the viewport's size and scale. We must add this tag if we want to load the styles correctly in different devices. Just add it in the `<head>` section, at the top of the page:

```html
<meta name="viewport" content="width=device-width, initial-scale=1" />
```

## Responsive Font Size with CSS

Having fixed font-size across devices is not always a good idea. You should make your font-size respond to viewport or container to complete your responsive designs. CSS viewport units and media queries provide the means to implement a responsive font size.

### Font-Size

Most websites today use font sizes ranging between 14 and 18 pixels for body text. [Usability experts](https://www.smashingmagazine.com/2011/10/16-pixels-body-copy-anything-less-costly-mistake/) recommend a font-size of at least 16px.

We should also consider how many words per line appear. The recommendation is to have about 18 words. As a general rule, use the largest font-size that doesn't look disproportionate and results in lines with 20 words or less.

### Line-Height

Another measurement to take into account is [line height](https://developer.mozilla.org/en/docs/Web/CSS/line-height) or line spacing. Line height doesn't involve a compromise because it only affects the page height. Most sources recommend a line-height of 1.2 to 1.45em for good readability and aesthetics.

### Implement Responsive Font Size

There are two main ways to implement a responsive font-size: viewport units and media queries, along with good old pixels and ems.

#### CSS Viewport Units

CSS viewport units were specially created to allow measurements in CSS (including `font-size`) to be relative to the viewport size. They allow a truly responsive `font-size`, by defining the size as a percentage of the viewport width or height. We have four possible values:

- **vw**. Viewport width. 1vw equals 1% of the viewport width.
- **vh**. Viewport height. 1vh equals 1% of the viewport height.
- **vmin**. Viewport minimum. It's relative to the shortest dimension (width or height).
- **vmax**. Viewport maximum. It's relative to the longest dimension.

**The problem with viewport units**

When we try to set the responsive font size in viewport units, we can find two different problems:

- **Text gets too large or too small**. Setting `font-size: 1vw` will produce 19px letters in 1920px wide displays, but 6px letters in 640px wide viewports.
- **Viewport units don't account for max-width**. The viewport size might be larger than the site's `max-width` and `vw` doesn't care. The text will get larger while the rest of the layout stays the same. The same occurs for `min-width`.

### Pixels, ems, rems and Media Queries

The other way to implement a responsive font size is to use media queries along with the fixed-size text. For fixed-size text, we can use:

- **px**. It specifies the height of the letters in CSS pixels
- **em**. It's relative to parent's font size. i.e. 2em = 20px if parent element's `font-size` is 10px.
- **rem**. It's relative to the `html` font size. i.e. 1rem = 10px if html element's `font-size` is 10px.

The best way to use ems and pixels is to specify a pixel `font-size` for the HTML element and use ems and rems for the rest. The reasons to do that are:

- **The CSS is easier to maintain**. Change the HTML `font-size` will change all the fonts of the website.
- **Using media queries gets easier for the same reason**. You just have to change the rule on the HTML element, and all the media queries will be updated.
- **Browser compatibility**. Some browsers don't allow resizing fonts set in pixels. Users won't be able to increase the font size in those browsers.

#### Examples

#### `em` values

```html
<html>
  <head>
    .....
  </head>
  <body>
    <h1>Champions League Champions</h1>
    <ul>
      <li>Real Madrid</li>
      <li>FC Barcelona</li>
      <li>Juventus</li>
      <li>Manchester United</li>
    </ul>
  </body>
</html>
```

```css
/*
Your .css file
*/

html {
  font-size: 10px;
}

h1 {
  font-size: 1.5rem;
}

ul {
  font-size: 8px;
}

li {
  font-size: 1.5em;
}

@media (max-width: 600px) {
  html {
    font-size: 8px;
  }
}
```

##### `rem` values

```css
/*
Your .css file
*/
html {
  font-size: 10px;
}

h1 {
  font-size: 1.5rem;
}

li {
  font-size: 1rem;
}

@media (max-width: 600px) {
  html {
    font-size: 8px;
  }
}
```

:::info
:bulb: If we want to use ems and pixels, it's recommended to set the HTML element `font-size` to 10px. It will be much easier to calculate the size of the elements multiplying them by 10.

i.e. if we want to have a 15px font-size, we will set the element's font-size to 1.5rem
:::

**CSS Units/ Box Dimensions** (Video):
{%youtube 2B_uJhpSIC4 %}

## Developer Tools

### Chrome Dev Tools

We have seen that resizing our browser, we can check out if the responsive design is working or not. We can do the same with Google Chrome Developer Tools:

- Open the Chrome Developer Tools (Cmd+Alt+J in Mac)
- Select the "Toggle device toolbar"

![](https://i.imgur.com/njHhsta.png)

- The browser will display the mobile version of our website. We will be able to check out if all the styles are applied correctly.

### Google Chrome Extension - Responsive Inspector

With the [Responsive Inspector](https://chrome.google.com/webstore/detail/responsive-inspector/memcdolmmnmnleeiodllgpibdjlkbpim) extension allows us to:

- See all the media queries that are defined in a site.
- Inspect a particular media and see the result on the site.
- Test a CSS for a specific viewport size.
- Save an image of your website for a specific viewport size.

In the following [video](https://www.youtube.com/watch?v=ylMHAj0OU10) you can see how it works.

## Summary

Responsive Web Design is the practice of building a website suitable to work on every device and every screen size. Mobile-first helps you to design the design from bottom to top, avoiding the use of useless information on the mobile versions.

With media queries, you can change the design of the website depending on the viewport size, and you can check out the different viewport versions with the Chrome Dev Tools. Finally, you will be able to control the font size and the line height in a Responsive website.

## Extra Resources

- [Mobile First](http://zurb.com/word/mobile-first)
- [Responsive Font Size](http://codeitdown.com/responsive-font-size-css/)
- [MDN - Using media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)
- [CSS Downloads by Media Query](http://scottjehl.github.io/CSS-Download-Tests/). This page is to test whether today's browser will download stylesheets that are referenced with media queries that would not apply to that browser or device.
- [Font-Size recommendation](https://www.smashingmagazine.com/2011/10/16-pixels-body-copy-anything-less-costly-mistake/). Smashing Magazine article about the font-size recommendation for body copies.
- [Chrome DevTools Network Performance](https://developers.google.com/web/tools/chrome-devtools/network-performance/network-conditions) - This will allow us to simulate different network speeds (2g/3g/etc.) so we can see how our website performs with slow bandwidth connections

### Google I/O 2014 - Design principles for a better mobile web

[![](http://img.youtube.com/vi/xqviGwyy7y0/0.jpg)](http://www.youtube.com/watch?v=xqviGwyy7y0)
