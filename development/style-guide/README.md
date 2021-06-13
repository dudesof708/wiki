# Dudes of 708 Style Guide

-----

[Back to homepage](../..) • [software development](..)

-----

## Table of Contents

Please select the relevant programming language below.

* [C/C++](#c)
* [ES6 (Javascript)](#javascript)
* [Python](#python)

## C

The official C style guide is coming soon. For now, please contact our engineering manager Gideon Tong <[gideon@dudesof708.com](mailto:gideon@dudesof708.com)> for guidelines on writing C.

## Javascript

Our Javascript style guide is adapted from [Airbnb's Internal ES6 Style Guide](https://github.com/airbnb/javascript). Listed below are the most important resources, but for more style guidelines and interpretations, see the Airbnb style guideline link above.

### Javascript: Table of Contents

* [Types](#javascript-types)
* [Objects](#javascript-objects)
* [Arrays](#javascript-arrays)
* [Functions](#javascript-functions)
* [Syntax](#javascript-syntax)

[Back to top](#table-of-contents)

### Javascript: Types

1. Keep your references as `const` and avoid using `var`, if necessary, use `let` for scoping.

[Back to top (Javascript)](#javascript-table-of-contents)

### Javascript: Objects

1. Initialize objects by using literal syntax. Example:

   ```js
   const item = new Object();
   ```

2. Only quote object properties are are invalid identifiers. Example:

   ```js
   const object = {
       foo: 3,
       bar: 4,
       'data-blah': 5
   };
   ```

3. Do not call `Object.prototype` methods directly, instead use the prototype. Example:

   ```js
   // do this
   Object.prototype.hasOwnProperty.call(object, key));

   // not this
   object.hasOwnProperty(key);
   ```

[Back to top (Javascript)](#javascript-table-of-contents)

### Javascript: Arrays

1. Use `Array.from` instead of `Array.map`. Example:

   ```js
   Array.from(foo, bar);
   ```

2. Use `Array.forEach` rather than for loops or another iterable. This prevents mutating the original array. Example:

   ```js
   array.forEach((item) => {
       // do something cool
   });
   ```

[Back to top (Javascript)](#javascript-table-of-contents)

### Javascript: Functions

1. Avoid self-invoking functions. If you choose to use one, wrap one in parenthesis. Example:

   ```js
   (function() {
       // do something cool
   })());
   ```

2. Avoid reassigning parameters.
3. Use arrow function notation for an anonymous callback. Example:

   ```js
   const myArray = new Array();
   myArray.forEach((item) => {
       // do something cool
   });
   ```

[Back to top (Javascript)](#javascript-table-of-contents)

### Javascript: Syntax

1. Use multiline imports. Example:

   ```js
   import {
       moduleA,
       module B,
       module C
   } from 'package';
   ```

[Back to top (Javascript)](#javascript-table-of-contents)

## Python

The official Python style guide is coming soon. For now, please contact our engineering manager Gideon Tong <[gideon@dudesof708.com](mailto:gideon@dudesof708.com)> for guidelines on writing Python.
