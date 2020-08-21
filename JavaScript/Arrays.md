# Arrays

*Arrays* are lists of ordered, stored data. They can hold items that are of any data type. Arrays are created by using square brackets, with individual elements separated by commas.

``` Javascript
    // An array containing numbers
    const numberArray = [0, 1, 2, 3];

    // An array containing different data types
    const mixedArray = [1, 'chicken', false];
```

# Index

Array elements are arranged by *index* values, starting at `0` as the first element index. Elements can be accessed by their index using the array name, and the index surrounded by square brackets.

``` Javascript
    // Accessing an array element
    const myArray = [100, 200, 300];

    console.log(myArray[0]); // 100
    console.log(myArray[1]); // 200
    console.log(myArray[2]); // 300
```

# Property .length

The `.length` property of a JavaScript array indicates the number of elements the array contains.

``` Javascript
    const numbers = [1, 2, 3, 4];

    numbers.length // 4
```

# Mutable

Javascript arrays are *mutable*, meaning that the values they contain can be changed.

Even if they are declared using `const`, the contents can be manipulated by reassiging internal values or using methods like `.push` and `.pop`.

``` Javascript  
    const names = ['Alice', 'Bob'];

    names.push('Carl');
    // ['Alice', 'Bob', 'Carl']
```

# Method .push()

The `.push()` method of JavaScript arrays can be used to add one or more elements to the end of an array. `.push()` mutates the original array returns the new length of the array.

``` Javascript  
    // Adding a single element:
    const cart = ['apple', 'orange'];
    cart.push('pear'); 

    // Adding multiple elements:
    const numbers = [1, 2];
    numbers.push(3, 4, 5);
```

# Method .pop()

The `.pop()` method removes the last element from an array and returns that element.

``` Javascript  
    const ingredients = ['eggs', 'flour', 'chocolate'];

    const poppedIngredient = ingredients.pop(); // 'chocolate'
    console.log(ingredients); // ['eggs', 'flour']
```

# Other methods

1. **concat()** : The `concat()` method is used to join two or more arrays. This method does not change the existing arrays, but returns a new array, containing the values of the joined arrays.

``` Javascript  
    let array1 = ['a', 'b', 'c'];
    let array2 = ['d', 'e', 'f'];
    let array3 = array1.concat(array2);

    console.log(array3); // ["a", "b", "c", "d", "e", "f"]
    console.log(array1); // ["a", "b", "c"]
    console.log(array2); // ["d", "e", "f"]
```

2. **filter()** : The `filter()` method creates an array filled with all array elements that pass a test (provided as a function).

``` Javascript  
    let words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
    let result = words.filter(function(word) {
    return word.length > 6;
    });

    console.log(result); // ["exuberant", "destruction", "present"]
    console.log(words); // ["spray", "limit", "elite", "exuberant", "destruction", "present"]
```
> ***Note***: `filter()` does not execute the function for array elements without values and `filter()` does not change the original array.

3. **find()** : The `find()` method returns the value of the first element in an array that pass a test ( provided as a function ). The `find()` method executes the function once for each element present in the array:
    * If it finds an array element where the function returns a `true` value, `find()` returns the value of that array element (and does not check the remaining values).
    * Otherwise it returns undefined.

 > ***Note***: `find()` does not execute the function for empty arrays and `find()` does not change the original array.

``` Javascript  
    let array = [5, 12, 8, 130, 44];
    let found = array.find(function(element) {
    return element > 10;
    });

    console.log(found); // 12
    console.log(array); // [5, 12, 8, 130, 44]
```

4. **forEach()** : The `forEach()` method calls a function once for each element in an array, in order.
``` Javascript  
    var array = ['a', 'b', 'c'];

    array.forEach(function(element) {
    console.log(element);
    });

    // "a"
    // "b"
    // "c"

    console.log(array); // ["a", "b", "c"]
```

> ***Note***: The function is not executed for array elements without values.

5. **includes()** : The `includes()` method determines whether a string contains the characters of a specified string. This method returns `true` if the string contains the characters, and `false` if not.
``` Javascript  
    var array = [1, 2, 3];

    console.log(array.includes(2)); // true
    console.log(array); // [1, 2, 3]
```

> ***Note***: The `includes()` method is case sensitive.

6. **indexOf()** : The `indexOf()` method returns the position of the first occurrence of a specified value in a string. This method returns `-1` if the value to search for never occurs.

``` Javascript
    var beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];

    console.log(beasts.indexOf('bison'));
    console.log(beasts.indexOf('bison', 2));
    console.log(beasts.indexOf('giraffe'));
    console.log(beasts);
```

> ***Note***: The `indexOf()` method is case sensitive.

> ***Tip***: Also look at the `lastIndexOf()` method.

7. **join()** : The `join()` method returns the array as a string. The elements will be separated by a specified separator. The default separator is comma `(,)`.

``` Javascript
    var elements = ['Fire', 'Air', 'Water'];

    console.log(elements.join()); // "Fire,Air,Water"
    console.log(elements.join('')); // "FireAirWater"
    console.log(elements.join('-')); // "Fire-Air-Water"
    console.log(elements); // ["Fire", "Air", "Water"]
```

> ***Note***: This method will not change the original array.

8. **map()** : The `map()` method creates a new array with the results of calling a function for every array element. `map()` method calls the provided function once for each element in an array, in order.
``` Javascript
    var array = [1, 4, 9, 16];

    var map = array.map(function(item) {
    return item * item;
    });

    console.log(map); // [1, 16, 81, 256]
    console.log(array); // [1, 4, 9, 16]
```
> ***Note***: `map()` does not execute the function for array elements without values, this method does not change the original array.

9. ***shift()*** : The `shift()` method removes the first item of an array.
``` Javascript
    const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato'];

    console.log(plants.shift()); // "broccoli"
    console.log(plants); // ["cauliflower", "cabbage", "kale", "tomato"]
```

> ***Note***: This method changes the length of the array. The return value of the shift method is the removed item, this method will change the original array.

> ***Tip***: To remove the last item of an array, use the `pop()` method.