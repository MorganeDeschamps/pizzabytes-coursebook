# Express | Dynamic Views

## Learning Goals

After this lesson you will be able to:

- Create `views` in Express.
- Understand what `dynamic templates` are and why we use them.
- Understand and use `HandlebarsJS` for creating dynamic templates.
- Use `if`, `with` and `each` block helpers.cd 



<br>



#### Create the file structure

```bash
mkdir 00-express-dynamic-views

cd 00-express-dynamic-views

mkdir public views

mkdir public/css public/js

touch app.js views/home.html public/css/style.css

code .
```



<br>



#### Initialize the project and install dependencies

```bash
npm init

npm i express

npm i --save-dev nodemon
```



<br>



### Serving static pages

In previous lectures, during the introduction to Express, we shown an example on how to create routes and serve static html pages. We refer to this as "Serving Static Pages."

###### [`__dirname`](https://nodejs.org/api/modules.html#modules_dirname) 

**`__dirname`** - is the directory name of the current module where the value `__dirname` is accessed. 

This is the same as the `path.dirname(__filename)` .



```js
const express = require('express');
const app = express();

// Add middleware for serving static files

// MIDDLEWARE
app.use(express.static('public'));

// ...
//   ...
//     ...


// Sending a view as a file
app.get('/', (req, res, next) => {
  res.sendFile(`${__dirname}/views/home.html`);
});


app.listen(3000, () => {
  console.log(`Server is running at port 3000`)
})
```



<br>



### Update `home.html`

##### `home.html`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Express SSR</title>
    <link rel="stylesheet" href="/css/style.css" />
  </head>

  <body>
    <nav>
      <div>
        <img src="https://i.imgur.com/RP5vFgT.png" alt="" />
        <p>User's name</p>
      </div>
      <ul>
        <li><a href="">Home</a></li>
        <li><a href="">About</a></li>
        <li><a href="">Contact</a></li>
      </ul>
    </nav>

    <main>
      <h1 style="color: skyblue"><code>home.html</code> page</h1>
      <h4>
        This page was sent from the server using:
        <br />
        <code>res.sendFile( __dirname + '/home.html')</code>
      </h4>
    </main>
  </body>
</html>

```



<br>



##### `/public/css/style.css`

```css
body {
  margin: 0;
  padding: 0;
}

nav {
  display: flex;
  flex-direction: row-reverse;
  justify-content: space-between;
  background: cornflowerblue;
  color: white;
  padding: 5px 20px;
  box-shadow: 0px 1px 2px gray;
}

nav div {
  display: flex;
  align-items: center;
}

nav p {
  color: white;
  font-size: 20px;
  display: inline;
  margin-left: 10px;
}

nav img {
  width: 50px;
  height: 50px;
  border-radius: 50px;
  border: none;
  outline: none;
  background-color: aliceblue;
}

nav ul {
  display: inline-flex;
  align-items: center;
}

nav ul li {
  list-style: none;
  display: inline;
  margin-left: 20px;
  font-size: 20px;
}

nav ul li a {
  color: white;
  text-decoration: none;
}
```



<br>



### Server Side rendering  vs  Static Page



Server side rendering enables us to prepare and customise the page on the server by adding some custom data to it, before sending it to the client.



### [OPEN IMAGE](https://i.imgur.com/OVZ4TUc.png)

![img](https://i.imgur.com/OVZ4TUc.png)





<br>





## [Handlebars.js](<http://handlebarsjs.com/>)



### What is Handlebars.js ?



 [**Handlebars.js**](http://handlebarsjs.com/) is a popular templating engine, JavaScript library, based on the **Mustache Templating Language**.



*Template engine* helps us to create an HTML *template* with minimal code. 



Some of the most well-known JavaScript templating engines are [Mustache](http://mustache.github.com/), [Underscore](http://underscorejs.org/), [EJS](http://embeddedjs.com/), and [Handlebars](http://handlebarsjs.com/). 



With template engine we create a HTML *template* and inject some data on the server before sending it to the client.



We use templating engine to be able to do the server side rendering. We create and prepare the HTML page completely on the back-end and then when ready we serve it to the client.





<br>





## Install handlebars & start serving Views



<br>



#### Create a folder for views and file `views/index.hbs`

```bash
touch views/index.hbs
```



<br>



#### Notice that we use a new extension: 

####  `.hbs` instead of ~~`.html`~~ 



<br>



#### Install handlebars

```bash
npm install hbs
```



<br>





### Set path that points to the `views` folder

##### `app.js`

```js
// Create an absolute path pointing to the folder 
// called "views" for the handlebars engine
app.set('views', __dirname + '/views');

// set HBS to be in charge of rendering the HTML
app.set('view engine', 'hbs');
```



<br>



#### Add content to the `index.hbs` view file

##### `views/index.hbs`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>My first view</title>
  <link rel="stylesheet" href="stylesheets/style.css">
</head>
<body>
  <h1>Ironhackers Be Like</h1>
  <img src="https://media.giphy.com/media/l0MYEqEzwMWFCg8rm/giphy.gif">
</body>
</html>	
```



<br>

#### Update `app.js` to `res.render()` the `index` view

##### `app.js`

```js
// render the view using handlebars
app.get('/', (req, res, next) => {
  
  // res.send('hello world');       	<---- REMOVE
  
  // send `views/index.hbs` to be displayed in the browser			<---- ADD
  res.render('index');	//  																		<---- ADD
});
```



<br>

## :rotating_light:

<h2 style="color: red">Delete the file <pre>index.html</prepre> 
</h2>



<h2>If not deleted it will be loaded automatically by express when visiting the home endpoint `/`</h2>



<br>



### ***

### [Visit `localhost:3000/`](http://127.0.0.1:3000/)



<br>



## **Time To Practice** - 

### Create and serve your first View



Create a new View that will serve the **About** page:

- Create a new route for `GET` request  with the endpoint `/about`:

- It should render a new view file, from `views/about.hbs`.
- In the newly created template file `about.hbs`:
  - Create an `h1` with your name.
  - Add an image from [giphy](https://giphy.com/) that you like.







<br>



## Handlebars - Templating in action

```bash
touch views/student.hbs
```



When rendering a template we can pass it data that we want to inject into the template.

To do this we pass the data as the second parameter to the method:  `res.render('view-name', data)`.



##### `app.js`

```js
// create a template and pass it the data
// that can be used inside of the template page
app.get('/student', (req, res, next) => {
  const data = {
    name: "Ironhacker",
    bootcamp: "IronHack Barcelona - WebDev"
  };

  res.render('student', data);
});
```



##### `student.hbs`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Home</title>
</head>
<body>
  <h1>Hello {{name}}!</h1>
  <p>Welcome to the {{bootcamp}}.</p>
  
  <img src="http://giphygifs.s3.amazonaws.com/media/FQyQEYd0KlYQ/giphy.gif">
</body>
</html>
```





<br>



## Handlebars - Escaping HTML

HTML strings within the currly braces ``{{ }}`` are not automatically parsed.

By default Handlebars escapes HTML values included in a expression with the `{{ }}`, and shows them as a string.



#### Try the following

##### `app.js`

```js
bootcamp: '<h3>IronHack WebDev</h3>'
```





##### To parse the HTML strings, use the triple-stash: `{{{ }}}`.

This will ensure that any HTML tag is parsed as an HTML element and not as a string.



##### `student.hbs`

```handlebars
<p>Welcome to the {{{ bootcamp }}} .</p>
```



<br>



### Be aware:

When not sanitizing the input from the user we may end up with the situation where malicious script being injected in the view.

Using `{{{ }}}` leaves the input unsanitized, meaning that HTML characters are not escaped.



The below string will be evaluated as a valid HTML code. Notice what happens!



##### `app.js`

```js
//  bootcamp: '<h3>IronHack WebDev</h3>',

    bootcamp: `<script>
      var password = prompt(\` You were logged out. \n \n Enter Your Password: \`);

      console.log('BANG! - GOT THE PASSWORD:', password);

      setTimeout(() => {
        document.body.innerHTML = \`<h1>you've been pwned! (╯ ͠° ͟ʖ ͡°)╯┻━┻ </h1>\`
      }, 5000)

      setTimeout(() => {
        window.location.href = "https://www.youtube.com/watch?v=b48HJQL5Hoo";
      }, 9000)</script>`
```

 

<br>



## Handlebars Helper Features



### `if` - block helper

####  `{{ #if <argument> }}  {{ /if }}` 

- You can use the `if` helper to render a block conditionally. 

- If it's **argument** has any of the values:  `false`, `undefined`, `null`, `""`, `0`, or `[]`, **Handlebars** will not render the block.



##### `student.hbs`

```handlebars
<hr>

<h3>#if</h3>

{{#if message}}
  <h2>
   message - This won't be displayed if message property doesn't exist!
  </h2>
{{/if}}

{{#if name}}
  <h2>name - This will be displayed!</h2>
{{/if}}
```



<br>



#### Add the `message` property to the data, so that it is rendered in the `if` helper 



##### `student.hbs`

```js
app.get('/student', (req, res, next) => {
  const data = {
    name: 'Ironhacker',
    bootcamp: '<h3>IronHack WebDev</h3>',
    message: "Rocking it!"
  };
  
  res.render('index', data);
});
```



<br>



## Using `else` condition



Add the following, below the existing code in the `student.hbs` view.

##### `student.hbs`

```handlebars
<hr>

<h3>#if</h3>
<h3>#else</h3>


{{#if address}}
    <h2>"address" exists - {{ address }}</h2>
{{else}}
  <h2>"address" doesn't exist - This will be displayed</h2>
{{/if}}
```



<br>



### `unless` block helper

`unless` will render the block if the argument has one of the values that handlebars considers **falsy** (  `false`, `undefined`, `null`, `0`, `""`, `[]` )

##### `student.hbs`

```handlebars
<hr>

<h3>#unless</h3>

{{#unless address}}
  <h3>WARNING: We can't find the address!</h3>
{{/unless}}
```



If we add the `address` property, then the warning should disappear!

```js
app.get('/student', (req, res, next) => {
  let data = {
    name: 'Ironhacker',
    message: 'Rocking it!',
    address: 'Barcelona'
 // address: 0							won't be rendered
 // address: ''							won't be rendered
 // address: []							won't be rendered
    
  };
  
  res.render('student', data);
});
```





<br>



###  `each` block helper



The `each` block helps us to iterate over a list of elements, mainly `objects` and `array`.



Add the array to the `data` that we will use to iterate over.

##### `app.js`

```js
app.get('/student', (req, res, next) => {
  let data = {
    name: "Ironhacker",
    message: "Rocking it!",
    address: "Barcelona",
    cities: ["Miami", "Madrid", "Barcelona", "Paris", "México", "Berlin"]
  };
  res.render('student', data);
});
```



<br>



##### `student.hbs`

```html
<hr>

<h3>#each</h3>

<ul>
  {{#each cities}}
    <li>{{this}}</li>
  {{/each}}
</ul>
```



<br>



#### `{{ #each <collection> }} {{ else }}`



##### To `{#each <collection>}` we can optionally provide an `{{else}}` section, which will display only when the list is empty.



##### `student.hbs`

```html
<hr>

<h3>#each #else - fallback option</h3>

<ul>
  {{#each countries}}  {{!--  no countries property exist in data --}}
    <li>{{this}}</li>
  {{else}}
    <p>No countries yet!</p>
  {{/each}}
</ul>
```



<br>



#### `@index`

When looping through items in `each`, you can optionally reference the current loop **index** via `{{@index}}`



##### `student.hbs`

```html
<hr>

<h3>@index</h3>

<ul>
  {{#each cities}}
    <li>{{@index}}: {{this}}</li>
  {{/each}}
</ul>
```



<br>



#### `@key`

Additionally for `object` iteration, `{{@key}}` references the current key name when iterating over an object for example:



##### `app.js`

```js
app.get('/student', (req, res, next) => {
  let data = {
    name: "Ironhacker",
    message: "Rocking it!",
    address: "Barcelona",
    cities: ["Miami", "Madrid", "Barcelona", "Paris", "México", "Berlín"],
    countries: ["Spain", "France", "Germany", "Portugal", "United States", "Brazil"],
    info: { name: 'Ironhacker', campus: 'Barcelona', year: 2019}
  };
  res.render('student', data);
});
```



<br>



##### `student.hbs`

```handlebars
<hr>

<h3>@key</h3>

<ul>
{{#each info}}
  <li>{{@key}}: {{this}}</li>
{{/each}}
</ul>
```

<br>



### Object Properties

##### `student.hbs`

```handlebars
  <hr>

  <h3>Object properties</h3>

    <p>{{info.name}}</p>
    <p>{{info.campus}}</p>
    <p>{{info.year}}</p>

  <hr>
```





<br>



#### `@first` - `@last` - from the array

The first and last steps of iteration are noted via the `@first` and `@last` variables when iterating over an array.

```html
<hr>

<h3>@first - @last</h3>

<ul>
  {{#each cities}}
  
    {{#if @first}}
      <li><b> First: {{this}}</b></li>
  
    {{else if @last}}
      <li><i>Last: {{this}}</i></li>
  
    {{else}}
      <li>{{this}}</li>
  
    {{/if}}
  
  {{/each}}
</ul>
```



<br>



###  `with` block helper

Commonly, Handlebars evaluates its templates against the context/data passed into the compiled method. 



To access the nested data we can either use the dot notation or by using the built-in `#with` block helper.



For example, passing the following data:

```js
app.get('/student', (req, res, next) => {
  let data = {
    name: "Ironhacker",
    bootcamp: "<span>IronHack WebDev</span>",
    message: 'Rocking it',
    
    address: {								// <-- UPDATE
      street: "Barcelona",		// <-- UPDATE
      number: 96							// <-- UPDATE
    },												// <-- UPDATE
    
    cities: ["Miami", "Madrid", "Barcelona", "Paris", "México", "Berlín"],
    info: { name: 'Ironhacker', campus: 'Barcelona', year: 2019 }
  };

  res.render('student', data);
});
```

We can do this:

```handlebars
<hr>

<h3>#with</h3>

<h3>Hello {{name}} {{lastName}}!</h3>

{{#with address}}
  <p>{{street}}, {{number}}</p>
{{/with}}
```



Using the `with` helper, we shift the context from where we get the data, so that we can refer to `{{address.street}}` and `{{address.number}}`, as `{{street}}` and `{{number}}`.





### Handlebars Documentation

<http://handlebarsjs.com/>

