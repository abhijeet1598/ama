# Techincal Paper on AMA held on July 06

### 1. What is the difference between (==) and (===) operator ?

**Ans:** (==) is comparison operator which only compares the values whereas (===) operator compares both values and data types.
For example: "2" == 2 evaluates to true because the values are equal whereas "2" === 2 evaluates to false because the data type of the operands are different.

### 2. Console.log(typeof []) is equals to 'object' why?

**Ans:** In Javascript, arrays are type of object. Arrays are used to store multiple values of different data types in a single variable. They behave like object because arrays also have some built-in properties like push, pop, length, isArray, etc.

### 3. Whats are the disadvantages of using closure?

**Ans:** Following coule the disadvantages of using closure:

- Closures can cause increased memory usage because they retain references to their lexical scope. This can lead to memory leaks if the retained variables consume a lot of memory.

### 4. Why using global variables are bad in js?

**Ans:** Global variable are bad beacuse:

- Global variables are accessible through the entire program. Hence, there could be risk of naming collisions which can lead unexpected behaviour and it will be harder to catch bugs.

- Global variables can be accidentally overwritten which can again lead to bugs and unexpected behaviour in the program.

- Global variable can be hard to manage as the code base grows. It is hard keep track what varibles were used in global so we do accidentally change the values.

### 5. How to extract certain properties from an array of objects to create a new array ?

**Ans:** We can use the Array.map() method to extract out some of the properties from input array of object and create a new array out of it.

### 6. Difference between charAt() and at() method in js?

**Ans:** The charAt() method returns the character at a specified index in a string. It works on zero based indexing. If the index is present in the string then this method return an empty string.
Whereas, at() method is new method released in ES13(2022) which returns the character at a specified index in a string. It also works with negative indexing and If the index is present in the string then this method returns undefined.

### 7. How to reset initial or 1st commit in git, if its possible?

**Ans:** It is not possible to reset initial or 1st commit. First we would need to create a new branch and switch to that using `git checkout -b <newBranch>`. Then commit on the new branch and delete the old branch using `git branch -d <oldBranch>`.

### 8. console.log(typeof []) returns 'object', then why can not we use (.) operator in array to accesss its values just like objects,where we use (.) operator in objects for accessing key and values

**Ans:** Eventhough type of array is object in Javascript. However, to access properties of object we use dot(.) notation. However, inside an array it is indexed collection of elements where we can access the elements of an array using bracket notation.

### 9. Why 'forEach' loop skips 'not defined' whereas 'for' loop gives 'undefined'?

**Ans:** The forEach() loop was designed in such a way that it skips the missing and undefined values. It does not execute its callback on missing elements or undefined elements in the array. Whereas a for loop will iterate over all the element whether it is missing or undefined since it travels index by index.

### 10. How can we mimic the action Array.splice and 'Array.slice' on objects?

**Ans:** There is no in-built method in javascript objects which could mimic Array.splice and 'Array.slice' on objects. However, we can create our custom function and use of Object.keys() to create array of keys to perform the slice or splice operations on the array.

```
function objectSlice(obj, start, end) {
    const keys = Object.keys(obj);
    const slicedKeys = keys.slice(start, end);

    let result = {};
    slicedKeys.forEach(key => {
        result[key] = obj[key];
    });

    return result;
}
```

### 11. What is "Callback Hell" problem and how to avoid it?

**Ans:** The callback hell in JavaScript is referred to as a situation where an excessive amount of nested callback functions are being executed. It reduces code readability and maintenance. The callback hell situation typically occurs when dealing with asynchronous request operations, such as making multiple API requests.
One of the ways by which callback hell can be avoided in when dealing with asynchronous request operations is by using promises or async-await.

### 12.

```
//file1.js
let ar = [1,2,3];
console.log("Hello");
module.exports.ar = ar;
```

```
//file2.js
const {ar} = require('file1.js');
let print = ar;
console.log(print);
```

```
Output: "Hello"
[1,2,3]
```

### why "Hello" is also printing ? when we have exported array('ar') only!

The require function in Node.js does not just import the values which are exported from a node module but also runs the entire node module while importing.
Therefore, to export specific values and avoid executing certain code during the require process, we need to wrap the inside a function block and export it and then use it in the module wherever needed.
