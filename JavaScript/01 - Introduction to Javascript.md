# What is JavaScript?

JavaScript is a programming language that powers the dynamic behavior on most websites. Alongside HTML and CSS, it is a core technology that makes the web run.

# console.log()

The ***console.log()*** method is used to log or print messages to the console. It can also be used to print objects and other info.

``` Javascript
    console.log('Hello C4E!');
// Prints: Hello C4E!!
```

You’ll see later on that we can use ***console.log()*** to print different kinds of data.

### Exercises

Use the ***console.log()*** code in the editor to log your age to the console.

Run your code when you are ready to see the result.

# Methods

Methods return information about an object, and are called by appending an instance with a period `.`, the method name, and parentheses.

``` Javascript
    // Returns a number between 0 and 1
    Math.random();
```

# Libraries

Libraries contain methods that can be called by appending the library name with a period `.`, the method name, and a set of parentheses.

``` Javascript
    Math.random();
// ☝️ Math is the library
```

# Data Types

***Data types*** are the classifications we give to the different kinds of data that we use in programming. In JavaScript, there are seven fundamental data types.

* ***Number***: Any number, including numbers with decimals: `4, 8, 1516, 23.42.`
``` Javascript 
    let amount = 6;
    let price = 4.99;
```
* ***String***: Any grouping of characters on your keyboard (letters, numbers, spaces, symbols, etc.) surrounded by single quotes: `' ... '` or double quotes `" ... "`. Though we prefer single quotes. Some people like to think of string as a fancy word for text.
``` Javascript 
    let single = 'Wheres my bandit hat?';
    let double = "Wheres my bandit hat?";
```
* ***Boolean***: This data type only has two possible values— either `true` or `false` (without quotes). It’s helpful to think of booleans as on and off switches or as the answers to a “yes” or “no” question.
``` Javascript 
    let lateToWork = true; // or false
```
* ***Null***: This data type represents the intentional absence of a value, and is represented by the keyword `null` (without quotes).
``` Javascript 
    let x = null;
```
* ***Symbol***: A newer feature to the language, symbols are unique identifiers, useful in more complex coding. No need to worry about these for now.

* ***Object***: Collections of related data.
``` Javascript 
    let persons = {
        firstName: "Tran",
        lastName: "Quang",
        age: 19,
        school: "FPT University HCM"
    };
```
The first 6 of those types are considered ***primitive data types***. They are the most basic data types in the language. 

### Exercises

1.  In the editor, ***console.log*** all of the following: `'JavaScript', 2020, "Woowhoo! I love to code.", 4.4` to the console.
2. 

# Arithmetic Operators

JavaScript supports arithmetic operators for:

* `+` : Addition
* `-` : Subtraction
* `*` : Multiplication
* `/` : Division
* `%` : Modulus (Division Remainder)

``` Javascript
    // Addition
    5 + 5
    // Subtraction
    10 - 5
    // Multiplication
    5 * 10
    // Division
    10 / 5
    // Modulo
    10 % 5
```

# String Interpolation

String interpolation is the process of evaluating string literals containing one or more placeholders (expressions, variables, etc).

It can be performed using template literals: `text ${expression} text`.
``` Javascript
    let age = 7;

    // String concatenation
    'Tommy is ' + age + ' years old.';

    // String interpolation
    `Tommy is ${age} years old.`;
```

# Variables

Variables are used whenever there’s a need to store a piece of data. A variable contains data that can be used in the program elsewhere. Using variables also ensures code re-usability since it can be used to replace the same value in multiple places.
``` Javascript
    const currency = '$';
    let userIncome = 85000; 

    console.log(currency + userIncome + ' is more than the average income.');
    // Prints: $85000 is more than the average income.
```

# Learn Javascript: Variables

A variable is a container for data that is stored in computer memory. It is referenced by a descriptive name that a programmer can call to assign a specific value and retrieve it.
``` Javascript
    // examples of variables
    let name = "Tammy";
    const found = false;
    var age = 3;
    console.log(name, found, age);
    // Tammy, false, 3
```

# Declaring Variables

To declare a variable in JavaScript, any of these three keywords can be used along with a variable name:

* ***var*** is used in pre-ES6 versions of JavaScript.
* ***let*** is the preferred way to declare a variable when it can be reassigned. `let` creates a local variable in JavaScript & can be re-assigned. Initialization during the declaration of a `let` variable is optional. A `let` variable will contain `undefined` if nothing is assigned to it.
* ***const*** is the preferred way to declare a variable with a constant value. A constant variable can be declared using the keyword `const`. It must have an assignment. Any attempt of re-assigning a `const` variable will result in JavaScript runtime error.

``` Javascript
    var age = 19;
    let weight = 50;
    const numberOfFingers = 20;
```

# String Concatenation

In JavaScript, multiple strings can be concatenated together using the `+` operator. In the example, multiple strings and variables containing string values have been concatenated. After execution of the code block, the `displayText` variable will contain the concatenated string.

``` Javascript
    let service = 'credit card';
    let month = 'May 30th'; 
    let displayText = 'Your ' + service  + ' bill is due on ' +  month + '.';
    console.log(displayText);
    // Prints: Your credit card bill is due on May 30th.
```

# Template Literals

Template literals are strings that allow embedded expressions, `${expression}`. While regular strings use single `'` or double `"` quotes, template literals use backticks instead.

``` Javascript
    let fullName = "Tran Minh Quang";
    console.log(`Hello, ${fullName}`); 
    // Prints: Hello, Tran Minh Quang

    console.log(`Quang is ${10+9} years old.`) 
    // Prints: Quang  is 19 years old.
```