# Functions Assigned to Variables

In JavaScript, functions are a data type just as strings, numbers, and arrays are data types. Therefore, functions can be assigned as values to variables, but are different from all other data types because they can be invoked.

``` Javascript
    let plusFive = (number) => {
        return number + 5;  
    };
    // f is assigned the value of plusFive
    let f = plusFive;

    plusFive(3); // 8
    // Since f has a function value, it can be invoked. 
    f(9); // 14
```

# Callback Functions

In JavaScript, a callback function is a function that is passed into another function as an argument. This function can then be invoked during the execution of that higher order function (that it is an argument of).

Since, in JavaScript, functions are objects, functions can be passed as arguments.

``` Javascript
    const isEven = (n) => {
        return n % 2 == 0;
    }

    let printMsg = (evenFunc, num) => {
        const isNumEven = evenFunc(num);
        console.log(`The number ${num} is an even number: ${isNumEven}.`)
    }

    // Pass in isEven as the callback function
    printMsg(isEven, 4); 
    // Prints: The number 4 is an even number: True.
```

# Higher-Order Functions

In Javascript, functions can be assigned to variables in the same way that strings or arrays can. They can be passed into other functions as parameters or returned from them as well.

A “higher-order function” is a function that accepts functions as parameters and/or returns a function.

### Read more: [Higher-Order Functions](https://viblo.asia/p/tim-hieu-ve-higher-order-functions-trong-javascript-yMnKMY2mK7P)

