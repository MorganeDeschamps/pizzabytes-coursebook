<!-- ![](https://i.imgur.com/1QgrNNw.png)

# HTML | Introduction -->

## Learning Goals

After this lesson, you will be able to:

- Understand the structure of an HTML document, apply basic HTML tags and tag attributes to create pages.
- Understand the difference between inline and block elements.
- Use inline and block elements to create a simple webpage.

## HTML Introduction

### What is HTML?

[HyperText Markup Language](https://developer.mozilla.org/en-US/docs/Web/HTML) (HTML) is a language for creating web pages and web applications. HTML special instructions are the building blocks of web pages.

A web page is a collection of many kinds of content. This might be text, graphics, forms, audio and video files, etc. These elements live inside HTML tags. The browser uses these tags to decide how to display, order and style the content on the page.

HTML files that produce web pages are simple text files. Text is a universal way of representing data for computers; any HTML you create on a Windows PC could work on a Mac, Linux/Unix, or any other operating system.

The best way to start working with HTML is to jump right in. So let's see a real example:

![](https://i.imgur.com/CjRpPff.png)

Let's take a look at the picture above. It shows a simple web page with a title, a menu, a picture and some written information.

:::info
:warning: **Cheating Warning:** Don't panic if you copy-paste the code and it doesn't look the same, we used some stylesheets to make the page look better :)
:::

Web browsers read and display HTML markup. This markup _-with a little help of CSS, which we'll learn in the future-_ tells the browser how to do it.

In the HTML file, you will find the content of the components shown below.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>The HTML5 Breakfast Site</title>
    <meta charset="UTF-8" />
  </head>
  <body>
    <div id="container">
      <nav id="topnav">
        <a href="index.html">HOME</a> | <a href="about.html">ABOUT US</a> | <a href="menu.html">MENU</a> |
        <a href="contact.html">CONTACT US</a>
      </nav>

      <section id="content">
        <h1>The IronHack Breakfast Place</h1>
        <p>Here you will find all sorts of delicious treats</p>
        <figure>
          <img src="Breakfast.jpg" width="400" alt="healthy breakfast" />
          <figcaption>powered by brekkie.</figcaption>
        </figure>
      </section>

      <footer>
        <p class="love">Made with love by Ironhack</p>
      </footer>
    </div>
  </body>
</html>
```

Try to locate these components in the HTML Code and in the picture:

- Title: The HTML5 Breakfast Site
- Navigation Bar: (HOME | ABOUT US | MENU | CONTACT US)
- The muffin image
- The signature of the webpage creators

Can you find them all?

### HTML DOM tree

Every HTML Document can be **represented** as a tree using the Document Object Model (DOM), which contains all the elements of the HTML document, their format and the browser state at a specific moment.

The DOM structure is usually represented as a tree of nodes, where we can see what nodes (such as `<html>`) have which other nodes inside, for example `<head>`.

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_4d9f2a2679822b4f694c06ae3ff3021a.png)

In the HTML DOM, everything is a node. The document is a document node. But the elements, attributes and the content inside de elements are nodes, too. We will learn about this in further lessons.

Now let's take a look at the code in the given example and let's explain some of the syntax:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My first document</title>
    <meta charset="UTF-8" />
  </head>
  <body>
    ...
  </body>
</html>
```

- `<!DOCTYPE html>`
  DOCTYPE Indicates that the markup language for your document content is HTML5.
- `<html>`
  html Represents the root of an HTML document. All other elements must be descendants of this element. It's the first node in our DOM. It is mandatory to close the tag at the very end of the document by typing `</html>`.
- `<head>`
  head Defines an element that provides general information (metadata) about the document, including its title and links to its scripts and style sheets. Usually it contains: - `<title>`
  Defines the title of the document, there's only one title element in the head element of an HTML. This title contains only text and it is shown in a browser's title bar or on the page's tab. - `<meta>`
  Used to define metadata. This includes information about styles, scripts and data to help browsers use and render the page. One of the most commons elements is the `<meta charset="UTF-8">` in our example. This specifies the character encoding for the HTML document as [UTF-8](https://en.wikipedia.org/wiki/UTF-8).
- `<body>`
  body is the element containing all the content of an HTML document. Every HTML component should be written between the opening and the closing body tag. As there can be only one entire body in a document, there can be only one `<body>` element.

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_1e69925bf7c951d9943654a612c1ee83.png)

## “Block” Vs “Inline”

:::warning
This is one of those concepts that we **really** encourage you to understand correctly. It can help you to take your HTML and CSS skills to the next level.
:::

Within the `<body>` element, we will write all the elements that we want to display in our website. These elements will be either `block-elements` or `inline-elements`.

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_9c6c4e882171fdb4c31b128e0861e64a.png)

We'll be discussing this in more detail, but check out this example on CodePen for clarification.

<iframe height='265' scrolling='no' src='//codepen.io/ironhack/embed/JRWGZq/?height=265&theme-id=0&default-tab=html,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/JRWGZq/'>JavaScript - Block vs Inline</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

## Block-level Elements

Block-level elements begin a new line on the webpage and, if no width is set, extend the full width of the available horizontal space of its parent element.

Examples of block-level elements are paragraphs or page divisions. Want to give it a try?

We will be working with this CodePen to learn our first block-level HTML tags!

<iframe height='292' scrolling='no' src='//codepen.io/ironhack/embed/PGokOb/?height=292&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/ironhack/pen/PGokOb/'>html-body-elements</a> by Ironhack (<a href='http://codepen.io/ironhack'>@ironhack</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

:::warning
:zap: Remember to click **Edit on CodePen** so you can code along and play around
:::

### The initial HTML on CodePen

In the HTML section of the CodePen you will find the code that is in the `body` section of an HTML file. CodePen allows you to simplify the code you insert here by adding in another layer some metadata, doctype information and stuff that is usually in the `head` section of an HTML file.

If you take a look at CodePen, you can find a tab for CSS code and another one for JavaScript code. We will not use them for now, but keep in mind the code in these tabs is already linked to the HTML.

In your HTML tab, let's add a new paragraph to explain a little bit about our Breakfast Place.

We will use the tag `p` for paragraph and we'll insert it in the CodePen replacing the comment

`<!-- Insert paragraph here -->`

You can copy and paste this text:

```html
<p>
  Our commitment is to use impeccable sourcing and quality ingredients to help you code. An ongoing collaboration between the classroom staff and the development team allow us to
  iterate our content and give our students the coding 'fruits and vegetables' -mainly made of JavaScript- that they need to grow as a healthy developer.
</p>
```

Easy, right?

### Paragraphs

The HTML `<p>` element represents a paragraph of text. Paragraphs are blocks of text separated from adjacent blocks by vertical blank space and/or first-line indentation.

### Preformatted text

The `<pre>` element represents preformatted text. Text within this element is typically displayed in a non-proportional ("monospace") font exactly as it is laid out in the file.

This is an example of a preformatted text. If you look closer, you will discover that the code in this platform is preformatted text :smiley:

<pre>This is a preformatted text</pre>

### Headings

Heading elements have six levels of document headings (titles): `<h1>` is the most important and `<h6>` is the least. A title briefly describes the topic of the section it introduces.

The following code shows all the heading levels, in use.

```html
<h1>Heading level 1</h1>
<h2>Heading level 2</h2>
<h3>Heading level 3</h3>
<h4>Heading level 4</h4>
<h5>Heading level 5</h5>
<h6>Heading level 6</h6>
```

Copy them in your CodePen to see its output!

### Lists

#### Ordered List

The HTML `<ol>` element represents an ordered list of items. Each list item is numbered.

#### Unordered List

The `<ul>` element represents a list of items too. However, the order of items is not relevant.

Here's a good trick to determine which one to use: try changing the order of the list items; if the meaning is changed, the `<ol>` element should be used, else the `<ul>` is adequate.

There is no limitation to the depth and overlap of lists defined with the `<ol>` and `<ul>` elements.

#### List Items

Ordered and unordered lists both have elements within them. These elements are declared as `li` elements.

This would be an example of code for an ordered list:

<!-- the formatting here is not correct -->

```html
<ol>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ol>
```

Let's create the same list in your CodePen to see the output.

### Tables

table, tr, td, tfoot, thead

#### The `<table>` tag

This element is used to express information in a two-dimensional data table. It requires several other elements inside to make sense.

The HTML element table row `<tr>` defines a row of cells in a table. If the element inside a row defines a header, we should use the `<th>` _(table header)_, otherwise we should use the `<td>` _(table data)_.

This would be a simple example of a table

```html
<table>
  <tr>
    <th>Name</th>
    <th>Bootcamp</th>
    <th>City</th>
  </tr>
  <tr>
    <td>Jose Perez</td>
    <td>FullStack WebDev</td>
    <td>Madrid</td>
  </tr>
  <tr>
    <td>Michael Smith</td>
    <td>FrontEnd WebDev</td>
    <td>Barcelona</td>
  </tr>
  <tr>
    <td>Ariel Quinones</td>
    <td>MasterChef WebDev</td>
    <td>Miami</td>
  </tr>
</table>
```

And this is its output:

<table>
  <tr>
    <th>Name</th>
    <th>Bootcamp</th>
    <th>City</th>
  </tr>
  <tr>
    <td>Jose Perez</td>
    <td>FullStack WebDev</td>
    <td>Madrid</td>
  </tr>
  <tr>
    <td>Michael Smith</td>
    <td>FrontEnd WebDev</td>
    <td>Barcelona</td>
  </tr>
  <tr>
    <td>Ariel Quinones</td>
    <td>MasterChef WebDev</td>
    <td>Miami</td>
  </tr>
</table>

### Forms

The `<form>` element is a section that allows the user to input information on the page. The `<form>` elements hold inputs, radio buttons, select boxes, etc. Usually, we will send this information to a web server, although we will learn how to access the user input from JavaScript as well.

The form element requires two very important attributes to work properly. Those are the `action` and `method` attributes.

Remember forms are elements created to allow users to send information to the website's server. When a user does this, it's known as a `post` (as in the user _posts_ information).

#### Action

This attribute sets the [URI](https://developer.mozilla.org/en-US/docs/Glossary/URI) to the program that processes the form's information. In other words, it tells the form where to send the information.

#### Method

This attribute sets the HTTP method that the browser uses to submit the form. We will learn just the `post` method for now.

The `post` method corresponds to the [HTTP POST method](<https://en.wikipedia.org/wiki/POST_(HTTP)>). This method sends the data inserted in the form to the server.

An example of a simple `form` with a post request would be:

```html
<form action="" method="post">
  <label for="name">Name:</label>
  <input id="name" type="text" />
  <button type="submit">Save</button>
</form>
```

#### Fieldset

The HTML `<fieldset>` element is used to group several controls as well as labels (`<label>`) within a web form.

We would need to group elements inside a form for different reasons: style purposes, organization and [web accessibility](https://en.wikipedia.org/wiki/Web_accessibility) features.

This is a form example with fieldset and label. It only includes one clickable element.

```html
<form action="/users" method="post">
  <fieldset><input type="radio" id="radio" /> <label for="radio">Click me</label></fieldset>
</form>
```

### HTML Block-level elements cheat sheet

Take a <em>good</em> look at this table with different tags for block-level elements. You will use all of them for the final exercise.

:::info
|Element | Description | Example of use / Output
|------------------|---------------------|-----------------------------------------------
|`<p></p>` | Paragraph | <p>Welcome to your website</p>
|`<pre></pre>` | Preformatted text | <pre>hello world!</pre>
|`<h1></h1>` | Heading (title) | <h1>Hello World!</h1>
|`<ol></ol>` | Ordered List | <ol><li>One</li><li>Two</li></ol>
|`<ul></ul>` | Unordered List | <ul><li>One</li><li>Two</li></ul>
|`<li></li>` | List Item | <li>One</li>
|`<table></table>` | 2-D Data | [Go to codepen](http://codepen.io/ironhack/pen/BLLWwY)
|`<form></form>` | Submit info | [Go to codepen](http://codepen.io/ironhack/pen/dppvqv)
|`<fieldset>` | Group form items | [Go to codepen](http://codepen.io/ironhack/pen/xEEAwz)
:::

### Let's practice!

We already used the `<p>` tag, but let's add more semantic content.

- Use `<pre>` tag to add a funny message asking our customers to code and enjoy

```html
<pre>
  Code everyday and enjoy your coffee every morning
</pre>
```

- Let's create a menu, using our fancy lists, to let them know what kinds of coffee we serve.

```html
<h3>Our food</h3>
<ul>
  <li>
    Our coffee
    <ol>
      <li>Cafe Latte</li>
      <li>Americano</li>
      <li>Capuccino</li>
    </ol>
  </li>

  <li>
    Our teas
    <ol>
      <li>Earl Grey</li>
      <li>English Breakfast</li>
      <li>Herb Tea</li>
    </ol>
  </li>
</ul>
```

Insert the code in your CodePen replacing this comment:

```html
<!-- Insert your menu here -->
```

- Let's create a form for reservations. But for now, we will leave it empty. We will fill it up with inline elements. We won't add the method nor action for now.

```html
<!-- Insert your reservations form here -->
```

Copy and paste this code

```html
<h3>Reservations here!</h3>
<form></form>
```

- We will let you work with tables on your own. Try to change the menu list and transform it into a table. :wink:

## Inline elements

`Inline elements` flow like text. They don't start a new line and they are shown right next to the previous element without clearing previous content.

Let's improve our HTML by using a couple of new tags. Let's take a look at them.

### Emphasizing the text

Let's try emphasizing text. We will use `em` tag to do it. We will emphasize the words "impeccable" and "quality" by wrapping them into `em` tags:

```html
... commitment is to use <em>impeccable</em> sourcing and <em>quality</em> ingredients...
```

Modify the code on CodePen to see the result.

#### When to use`<i>` and when to use `<em>`?

Although the visible result of the text style is that the word 'JavaScript' is in italic, there's a difference between the `em` tag, to emphasize stress. According to MDN:

It is often confusing to new developers why there are so many elements to express emphasis on text. `<i>` and `<em>` are perhaps one of the most common. Why use `<em></em>` vs `<i></i>`? They produce exactly the same result, right?

Not exactly. The visual result is, by default, the same - both tags render their content in italics. But the semantic meaning is different.

An example of `<em>` could be: "Just <em>do</em> it already!", or: "We <em>had</em> to do something about it". A person or software reading the text would pronounce the words in italics with an emphasis.

An example of `<i>` could be: "The <i>Queen Mary</i> sailed last night". Here, there is no added emphasis or importance on the word <i>"Queen Mary"</i>. It is merely indicated that the object in question is not a queen named Mary, but a ship named Queen Mary . Another example of `<i>` could be: "The word <i>the</i> is an article".

### Strong

It gives text strong importance, and is typically displayed in **bold**.

### Displaying Time/Dates

It is intended to be used presenting dates and times in a machine-readable format. A very common attribute is `datetime`, which indicates the time and date of the element and must be a valid date with an optional time string to be parsed.

### Links _(Anchors)_

`<a>` It defines a hyperlink to a location on the same page or any other page on the Web. Usually followed by ‘href’ attribute.`<a href = "http://www.example.com">`

### Break

`<br>` produces a line break in text (carriage-return) and it has no closure.

### Images

`<img>` defines an image. Is followed by the ‘src’ attribute and it is mandatory to add the image URL.
`<img src = "http://www.example.com">`

### Scripts

`<script>` is used to embed or reference an executable script within an HTML file.

### Spans

`<span>` is a generic inline container for phrasing content, which does not inherently represent anything. It can be used to group elements for styling purposes. It should be used only when no other semantic element is appropriate. Not recommended.

### Buttons

It represents a clickable button.

### Inputs

It is used to create interactive controls for web-based forms in order to accept data from the user. How it works varies considerably depending on the value of its type attribute.

### Labels

It represents a caption for an item in a user interface. It can be associated with a control either by placing the control element inside the `<label>` element, or by using the for attribute. One input can be associated with multiple labels.

### Selects

The HTML `<select>` element represents a control that presents a menu of options. The options within the menu are represented by `<option>` elements, which can be grouped by `<optgroup>` elements.

### Textarea

It represents a multi-line plain-text editing control. You can indicate the size by specifying number of column and rows.

### HTML Inline elements cheat sheet

Take a <em>good</em> look at this table with different tags for inline elements. Yes, we are emphasizing the word <i>good</i> because you will use all of them for the final exercise.

:::info
|Element | Description | Example of use / Output|
|-|-|-|
|`<em></em>` | Emphasizes text | We are the <em>best</em> in the city
|`<i></i>` | Italic text| <i>JavaScript</i> is a very powerful language
|`<strong></strong>` | Bold text | This is the <strong>last day</strong> to apply|
|`<time></time>`|Dates and times|The concert starts at 12:00
|`<a></a>`|Anchor|Go to <a href="www.google.com">Google</a>|
|`<br>`|Line break|To be <br> Or not to be|
|`<img>`|Image|[Go to codepen](http://codepen.io/ironhack/pen/VKjPPk)||
|`<script></script>`|Embedded code|[Go to codepen](http://codepen.io/ironhack/pen/JRKEWV)|
|`<span></span>`|Generic inline container|<p><span>Some text</span></p>|
|`<button></button>`|Clickable button|[Go to codepen](http://codepen.io/ironhack/pen/WGxRjE)|
|`<input></input>`|Data input field|[Go to codepen](http://codepen.io/ironhack/pen/VKjPWw)||
|`<label></label>`|Caption for item|[Go to codepen](http://codepen.io/ironhack/pen/bwZgRW)|
|`<select></select>`|Menu of options|[Go to codepen](http://codepen.io/ironhack/pen/pEbRAa)||
|`<textarea></textarea>`|Multi-line input|[Go to codepen](http://codepen.io/ironhack/pen/KgraXQ)|
:::

### Let's practice!

We already used the `<em>` tag, but let's add more semantic content.

- Use `<strong>` tag to highlight the words 'impeccable' and 'quality':

```html
...Our commitment is to use <strong>impeccable</strong> sourcing and <strong>quality</strong>...
```

- Let's add a 'Contact Us' link in the footer section. This will open our user's default email application and send an email to our staff:

```html
<!-- ... -->
    <a href="mailto:breakfast@ironhack.com">Contact Us</a>
  </footer>
<!-- ... -->
```

- Every restaurant has a schedule. Let's display our hours:

```html
<!-- ... -->
<p>We are open every day of the week from <time>8:00</time> to <time>22:00</time></p>
<footer>
  <!-- ... -->
</footer>
```

If you don't see any special change in your time, it's because what we are doing here is telling the computer this is a time element. Just that. We could later style every time element with CSS. For now it's a readable format for computers.

- Customers should be able to make reservations, let's create some fields. For now, we won't save their information, but let's create the space for them to input their reservation information. We will use the form element we created before

```html
<!-- ... -->
<label>
  Reservation for:
  <input type="text" name="name" value="Your name" />
</label>

<label>
  Meal:
  <select name="meal">
    <option value="breakfast">Breakfast</option>
    <option value="tea-time">Tea Time</option>
  </select>
</label>

<label>
  How many people?
  <select name="how-many">
    <option value="1">1</option>
    <option value="2">2</option>
    <option value="3">3</option>
    <option value="4">4</option>
  </select>
</label>

<button type="submit">Submit Reservation</button>
<!-- ... -->
```

Pretty cool, huh? Now is your time to play a little bit with the rest of the elements. Insert a `span` text, change and customize the text. Insert new images and a `textarea` for customers just in case they have allergies.

For now, keep the `script` tag out of your playground. We will learn about it later :smiley:

### Hidden elements

There is also a third type of element in HTML: those that aren't displayed at all. These elements provide information about the page but aren't displayed when rendered in a Web browser (as every element of our `<head>` section).

## Summary

In this unit, we learned that HTML is a language for creating web pages and applications. Its elements are the building blocks of web pages. Also, we learned that the DOM is a file that contains the elements of an HTML document, their format and the browser state at a specific moment.

Additionally, we learned to use block-level and inline elements. Block-elements begin a new line on the webpage and, if no width is set, they extend the full width of the available horizontal space.
On the contrary, inline elements' width only extends as far as its tag defines it.
Hidden elements are those that aren't displayed at all.

The following elements are "block-level":
_p, pre, small, h1 to h6, ol, ul, li, table, form, fieldset and many more!_

The following elements are "inline":
_em, i, small, strong, time, a, br, img, script, span, button, input, label, select, textarea..._

## Extra Resources

- [MDN HTML5 Documentation](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5) - This is your ideal documentation. Is pretty long, but is the first place to search when doubtful.
- [html5doctor](http://html5doctor.com/) - A good website to read how to implement HTML5
- [Inline elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements)
- [Block-level elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements)
- [HTML MDN Tutorial](https://developer.mozilla.org/en-US/docs/Learn/HTML)
