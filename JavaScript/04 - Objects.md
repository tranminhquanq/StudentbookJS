# Objects

An object is a built-in data type for storing key-value pairs. Data inside objects are unordered, and the values can be of any type.

```Javascript
    // Defining the Object:
    const myObjt = {
        key: value,
        key: value
    }

    // For example
    const person = {
        fullName: "Tran Minh Quang",
        age: 19,
        school: "FPT University HCM"
    }
```

# Properties and values of a JavaScript object

A JavaScript object literal is enclosed with curly braces `{}`. Values are mapped to keys in the object with a colon (`:`), and the key-value pairs are separated by commas. All the keys are unique, but values are not.

Key-value pairs of an object are also referred to as _properties_.

```Javascript
    // For example
    const classOf2020 = {
        students: 38,
        year: 2020
    }
```

# Dot Notation for Accessing Object Properties

Properties of a JavaScript object can be accessed using the dot notation in this manner: `object.propertyName`. Nested properties of an object can be accessed by chaining key names in the correct order.

```Javascript
    const apple = {
        color: 'Green',
        price: {
            bulk: '$3/kg',
            smallQty: '$4/kg'
        }
    };
    console.log(apple.color); // 'Green'
    console.log(apple.price.bulk); // '$3/kg'
```

# Restrictions in Naming Properties

JavaScript object key names must adhere to some restrictions to be valid. Key names must either be strings or valid identifier or variable names (i.e. special characters such as `-` are not allowed in key names that are not strings).

```Javascript

    // Example of invalid key names
    const trainSchedule = {
        platform num: 10, // Invalid because of the space between words.
        40 - 10 + 2: 30, // Expressions cannot be keys.
        +compartment: 'C' // The use of a + sign is invalid unless it is enclosed in quotations.
    }
```

# JavaScript Objects are Mutable

JavaScript objects are mutable, meaning their contents can be changed, even when they are declared as `const`. New properties can be added, and existing property values can be changed or deleted.

It is the _reference_ to the object, bound to the variable, that cannot be changed.

```Javascript
    const student = {
        name: 'Sheldon',
        score: 100,
        grade: 'A',
    }

    console.log(student)
    // { name: 'Sheldon', score: 100, grade: 'A' }

    delete student.score
    student.grade = 'F'
    console.log(student)
    // { name: 'Sheldon', grade: 'F' }

    student = {}
    // TypeError: Assignment to constant variable.
```

# JavaScript for...in loop

The JavaScript `for...in` loop can be used to iterate over the keys of an object. In each iteration, one of the properties from the object is assigned to the variable of that loop.

```Javascript
    let mobile = {
        brand: 'Samsung',
        model: 'Galaxy Note 9'
    };

    for (let key in mobile) {
        console.log(`${key}: ${mobile[key]}`);
    }
```

# Delete operator

Once an object is created in JavaScript, it is possible to remove properties from the object using the `delete` operator. The `delete` keyword deletes both the value of the property and the property itself from the object. The `delete` operator only works on properties, not on variables or functions.

```Javascript
    const person = {
        firstName: "Matilda",
        age: 27,
        hobby: "knitting",
        goal: "learning JavaScript"
    };

    delete person.hobby; // or delete person[hobby];

    console.log(person);
    /*
    {
        firstName: "Matilda"
        age: 27
        goal: "learning JavaScript"
    }
    */
```

# Javascript passing objects as arguments

When JavaScript objects are passed as arguments to functions or methods, they are passed by reference, not by value. This means that the object itself (not a copy) is accessible and mutable (can be changed) inside that function.

```Javascript
    const origNum = 8;
    const origObj = {color: 'blue'};

    const changeItUp = (num, obj) => {
        num = 7;
        obj.color = 'red';
    };

    changeItUp(origNum, origObj);

    // Will output 8 since integers are passed by value.
    console.log(origNum);

    // Will output 'red' since objects are passed
    // by reference and are therefore mutable.
    console.log(origObj.color);
```

# JavaScript Object Methods

JavaScript objects may have property values that are _functions_. These are referred to as object _methods_.

Methods may be defined using anonymous _arrow function expressions_, or with _shorthand method syntax_.

Object methods are invoked with the syntax: `objectName.methodName(arguments)`.

```Javascript
const engine = {
    // method shorthand, with one argument
    start(adverb) {
        console.log(`The engine starts up ${adverb}...`);
    },
    // anonymous arrow function expression with no arguments
    sputter: () => {
        console.log('The engine sputters...');
        },
    };

    engine.start('noisily');
    engine.sputter();

    /* Console output:
    The engine starts up noisily...
    The engine sputters...
    */
```

# JavaScript destructuring assignment shorthand syntax

The JavaScript _destructuring assignment_ is a shorthand syntax that allows object properties to be extracted into specific variable values.

It uses a pair of curly braces (`{}`) with property names on the left-hand side of an assignment to extract values from objects. The number of variables can be less than the total properties of an object.

```Javascript
    const rubiksCubeFacts = {
        possiblePermutations: '43,252,003,274,489,856,000',
        invented: '1974',
        largestCube: '17x17x17'
    };

    const { possiblePermutations, invented, largestCube } = rubiksCubeFacts;

    console.log(possiblePermutations); // '43,252,003,274,489,856,000'
    console.log(invented); // '1974'
    console.log(largestCube); // '17x17x17'
```

# shorthand property name syntax for object creation

The _shorthand_ property _name_ syntax in JavaScript allows creating objects without explicitly specifying the property names (ie. explicitly declaring the value after the key). In this process, an object is created where the property names of that object match variables which already exist in that context. Shorthand property names populate an object with a key matching the identifier and a value matching the identifier’s value.

```Javascript
    const activity = 'Surfing';
    const beach = { activity };
    console.log(beach); // { activity: 'Surfing' }
```

# Javascript factory functions

A JavaScript function that returns an object is known as a _factory function_. Factory functions often accept parameters in order to customize the returned object.

```Javascript
    // A factory function that accepts 'name',
    // 'age', and 'breed' parameters to return
    // a customized dog object.
    const dogFactory = (name, age, breed) => {
        return {
                name: name,
                age: age,
                breed: breed,
                bark() {
                console.log('Woof!');
            }
        };
    };
```

# this Keyword

The reserved keyword `this` refers to a method’s calling object, and it can be used to access properties belonging to that object.

Here, using the `this` keyword inside the object function to refer to the `cat` object and access its `name` property.

```Javascript
    const cat = {
        name: 'Pipey',
        age: 8,
        whatName() {
            return this.name
        }
    };

    console.log(cat.whatName());
    // Output: Pipey
```

# Javascript function this

Every JavaScript function or method has a `this` context. For a function defined inside of an object, `this` will refer to that object itself. For a function defined outside of an object, `this` will refer to the global object (`window` in a browser, `global` in Node.js).

```Javascript
    const restaurant = {
        numCustomers: 45,
        seatCapacity: 100,
        availableSeats() {
            // this refers to the restaurant object
            // and it's used to access its properties
            return this.seatCapacity - this.numCustomers;
        }
    }
```

# JavaScript Arrow Function this Scope

JavaScript arrow functions do not have their own `this` context, but use the this `of` the surrounding lexical context. Thus, they are generally a poor choice for writing object methods.

Consider the example code:

```Javascript
    const myObj = {
        data: 'abc',
        loggerA: () => { console.log(this.data); },
        loggerB() { console.log(this.data); },
    };

    myObj.loggerA();    // undefined
    myObj.loggerB();    // 'abc'
```

**_Note_**:

- `loggerA` is a property that uses arrow notation to define the function. Since `data` does not exist in the global context, accessing `this.data` returns `undefined`.

- `loggerB` uses method syntax. Since `this` refers to the enclosing object, the value of the `data` property is accessed as expected, returning `"abc"`.

# Getters and setters intercept property access

JavaScript getter and setter methods are helpful in part because they offer a way to intercept property access and assignment, and allow for additional actions to be performed before these changes go into effect.

```Javascript
    const myCat = {
        _name: 'Snickers',
        get name(){
            return this._name
        },
        set name(newName){
            //Verify that newName is a non-empty string before setting as name property
            if (typeof newName === 'string' && newName.length > 0){
                this._name = newName;
            } else {
                console.log("ERROR: name must be a non-empty string");
            }
        }
    }
```

# Javascript getters and setters restricted

JavaScript object properties are not private or protected. Since JavaScript objects are passed by reference, there is no way to fully prevent incorrect interactions with object properties.

One way to implement more restricted interactions with object properties is to use `getter` and `setter` methods.

Typically, the internal value is stored as a property with an identifier that matches the `getter` and `setter` method names, but begins with an underscore (`_`).

```Javascript
    const myCat = {
        _name: 'Dottie',
        get name() {
            return this._name;
        },
        set name(newName) {
            this._name = newName;
        }
    };

    // Reference invokes the getter
    console.log(myCat.name);

    // Assignment invokes the setter
    myCat.name = 'Yankee';
```
