# Hello World
Take a look at the following line of code:
``` js
    const h1 = <h1>Hello world</h1>;
```
It seems like it must be JavaScript, since it starts with `const` and ends with `;`. If you tried to run that in an HTML file, it wouldn’t work.
However, the code also contains `<h1>Hello world</h1>`, which looks exactly like HTML. That part wouldn’t work if you tried to run it in a JavaScript file.

# What is JSX?
*JSX* is a syntax extension for JavaScript. It was written to be used with React. JSX code looks a lot like HTML.

What does “syntax extension” mean?

In this case, it means that JSX is not valid JavaScript. Web browsers can’t read it!

If a JavaScript file contains JSX code, then that file will have to be *compiled*. That means that before the file reaches a web browser, a JSX compiler will translate any JSX into regular JavaScript.

Codecademy’s servers already have a JSX compiler installed, so you don’t have to worry about that for now. Eventually we’ll walk through how to set up a JSX compiler on your personal computer.

# Rendering JSX
You’ve learned how to write JSX elements! Now it’s time to learn how to *render* them.

To render a JSX expression means to make it appear onscreen.

``` js
    import React from 'react';
    import ReactDOM from 'react-dom';

    // Copy code here:
    ReactDOM.render(<h1>Hello World</h1>,
    document.getElementById('app'));
```

# Passing a Variable to ReactDOM.render()
`ReactDOM.render()`‘s first argument should *evaluate* to a JSX expression, it doesn’t have to literally be a JSX expression.

The first argument could also be a variable, so long as that variable evaluates to a JSX expression.

In this example, we save a JSX expression as a *variable* named `toDoList`. We then pass `toDoList` as the first argument to `ReactDOM.render()`:

```js
    import React from 'react';
    import ReactDOM from 'react-dom';

    // Write code here:
    const toDoList = (
    <ol>
        <li>Learn React</li>
        <li>Become a Developer</li>
    </ol>
    );

    ReactDOM.render(myList,
    document.getElementById('app'));
```

# class vs className
In HTML, it’s common to use `class` as an attribute name:
```js
    <h1 class="big">Hey</h1>
```
In JSX, you can’t use the word `class`! You have to use `className` instead:
```js
    <h1 className="big">Hey</h1>
```
This is because JSX gets translated into JavaScript, and `class` is a reserved word in JavaScript.

When JSX is *rendered*, JSX `className` attributes are automatically rendered as class attributes.

# Curly Braces in JSX
The code in the last exercise didn’t behave as one might expect. Instead of adding 2 and 3, it printed out “2 + 3” as a string of text. Why?

This happened because 2 + 3 is located in between `<h1>` and `</h1>` tags.

Any code in between the tags of a JSX element will be read as JSX, not as regular JavaScript! JSX doesn’t add numbers - it reads them as text, just like HTML.

You need a way to write code that says, “Even though I am located in between JSX tags, treat me like ordinary JavaScript and not like JSX.”
```js
    import React from 'react';
    import ReactDOM from 'react-dom';

    // Write code here:
    ReactDOM.render(
    <h1>{2 + 3}</h1>,
    document.getElementById('app');
);
```
# Variables in JSX
When you inject JavaScript into JSX, that JavaScript is part of the same environment as the rest of the JavaScript in your file.

That means that you can access variables while inside of a JSX expression, even if those variables were declared on the outside.
```js
// Declare a variable:
const name = 'Quang';

// Access your variable 
// from inside of a JSX expression:
const greeting = <p>Hello, {name}!</p>;
```

# Variable Attributes in JSX
When writing JSX, it’s common to use variables to set `attributes`.

Here’s an example of how that might work:
```js
// Use a variable to set the `height` and `width` attributes:

const sideLength = "200px";

const panda = (
  <img 
    src="images/panda.jpg" 
    alt="panda" 
    height={sideLength} 
    width={sideLength} />
);
```
Notice how in this example, the `<img />`‘s attributes each get their own line. This can make your code more readable if you have a lot of attributes on one element.

Object properties are also often used to set attributes:
```js
const pics = {
  panda: "http://bit.ly/1Tqltv5",
  owl: "http://bit.ly/1XGtkM3",
  owlCat: "http://bit.ly/1Upbczi"
}; 

const panda = (
  <img 
    src={pics.panda} 
    alt="Lazy Panda" />
);

const owl = (
  <img 
    src={pics.owl} 
    alt="Unimpressed Owl" />
);

const owlCat = (
  <img 
    src={pics.owlCat} 
    alt="Ghastly Abomination" />
); 
```

# Event Listeners in JSX

JSX elements can have `event listeners`, just like HTML elements can. Programming in React means constantly working with event listeners.

You create an event listener by giving a JSX element a special `attribute`. Here’s an example:
```js
<img onClick={myFunc} />
```
An event listener attribute’s name should be something like onClick or onMouseOver: the word on, plus the type of event that you’re listening for. You can see a list of valid event names [here](https://reactjs.org/docs/events.html#supported-events).

An event listener attribute’s value should be a function. The above example would only work if `myFunc` were a valid function that had been defined elsewhere:
```js
function myFunc() {
  alert('Make myFunc the pFunc... omg that was horrible i am so sorry');
}

<img onClick={myFunc} />
```
Note that in HTML, event listener names are written in all lowercase, such as `onclick` or `onmouseover`. In JSX, event listener names are written in `camelCase`, such as `onClick` or `onMouseOver`.

# JSX Conditionals: If Statements That Don't Work
Here’s a rule that you need to know: you can not inject an `if` statement into a JSX expression.

This code will break:
```js
(
  <h1>
    {
      if (purchase.complete) {
        'Thank you for placing an order!'
      }
    }
  </h1>
)
```
The reason why has to do with the way that JSX is compiled. You don’t need to understand the mechanics of it for now, but if you’re interested then you can learn more [here](https://reactjs.org/docs/jsx-in-depth.html).

What if you want a JSX expression to render, but only under certain circumstances? You can’t inject an `if` statement. What can you do?

You have lots of options. In the next few lessons, we’ll explore some simple ways to write conditionals (expressions that are only executed under certain *conditions*) in JSX.

# JSX Conditionals: If Statements That Do Work
How can you write a *conditional*, if you can’t inject an `if` statement into JSX?

Well, one option is to write an `if` statement, and not inject it into JSX.
Follow the if statement below: 
```js
import React from 'react';
import ReactDOM from 'react-dom';

let message;
let user = {
    name: "Quang",
    age: 19,
    role: "Teacher"
}
let drinkingAge = 18;

if (user.age >= drinkingAge) {
  message = (
    <h1>
      Hey, check out this alcoholic beverage!
    </h1>
  );
} else {
  message = (
    <h1>
      Hey, check out these earrings I got at Claire's!
    </h1>
  );
}

ReactDOM.render(
  message, 
  document.getElementById('app')
);
```

# .map in JSX

The array method `.map()` comes up often in React. It’s good to get in the habit of using it alongside JSX.

If you want to create a list of JSX elements, then `.map()` is often your best bet. It can look odd at first:
```js
const strings = ['Home', 'Shop', 'About Me'];

const listItems = strings.map(string => <li>{string}</li>);

<ul>{listItems}</ul>
```
In the above example, we start out with an array of strings. We call `.map()` on this array of strings, and the `.map()` call returns a new array of `<li>`s.

On the last line of the example, note that `{listItems}` will evaluate to an array, because it’s the returned value of `.map()`! JSX `<li>`s don’t have to be in an array like this, but they can be.
```js
// This is fine in JSX, not in an explicit array:

<ul>
  <li>item 1</li>
  <li>item 2</li>
  <li>item 3</li>
</ul>

// This is also fine!

const liArray = [
  <li>item 1</li>, 
  <li>item 2<li>, 
  <li>item 3</li>
];

<ul>{liArray}</ul>
```

# Keys

When you make a list in JSX, sometimes your list will need to include something called keys:
```js
<ul>
  <li key="li-01">Example1</li>
  <li key="li-02">Example2</li>
  <li key="li-03">Example3</li>
</ul>
```
A `key` is a JSX *attribute*. The attribute’s *name* is `key`. The attribute’s *value* should be something unique, similar to an `id` attribute.

`keys` don’t do anything that you can see! React uses them internally to keep track of lists. If you don’t use `keys` when you’re supposed to, React might accidentally scramble your list-items into the wrong order.

Not all lists need to have `keys`. A list needs keys if either of the following are true:

1. The list-items have `memory` from one render to the next. For instance, when a to-do list renders, each item must “remember” whether it was checked off. The items shouldn’t get amnesia when they render.

2. A list’s order might be shuffled. For instance, a list of search results might be shuffled from one render to the next.

If neither of these conditions are true, then you don’t have to worry about keys. If you aren’t sure then it never hurts to use them!

