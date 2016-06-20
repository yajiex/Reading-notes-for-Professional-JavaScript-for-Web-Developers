# Chapter 5: Reference Types

* `length` is not read-only. By setting the `length` property, you can easily remove items from or add item to the end of the array. If the `length` were set to a number greater than the number of items in the array, the new items would each get filled with the value of `undefined`
* Use `Array.isArray` to detect arrays
* Three supported flags represent matching modes:
  1. `g`: global mode
  2. `i`: case-insensitive mode
  3. `m`: multiline mode
* All metacharacters must be double-escaped, such as `\n` (the `\` character, which is normally escaped in strings as `\\` becomes `\\\\` when used in a regular-expression string).
* The inherited methods of `toLocaleString()` and `toString()` each return the literal representation of the regular expression, regardless of how it was created. The `valueOf()` method for a regular expression returns the regular expression itself.
* Because functions are objects, function names are simply pointers to function objects. So the global `sayHello()` function and `o.sayHello()`point to the same function event though they execute in different contexts.
* Function declarations are read and available in an execution context before any code is executed, whereas function expressions aren't complete until the execution reaches that line of code. As the code is being evaluated, the JavaScript engine does a first pass for function declarations and pulls them to the top of the source tree. So even though the function declaration appears after its usage in the actual source code, the engine changes this to boist the function declarations to the top.
* `arguments` object has a property named `called`, which is a pointer to the function that owns the arguments object.
* ECMAScript 5 formalizes an additional property on a function object: `caller`, it contains a reference to the function that called this function or `null` of the function was called from the global scope.
* ECMAScript 5 also defines `arguments.caller`, which results in an error in strict mode and is always undefined outside of strict mode. This is to clear up confusion between `arguments.caller` and the `caller` property of functions.
* The `length` property of function indicates the number of named arguments that the function expects.
* Any time a string value is accessed in read mode, the following three steps occur:
  1. Create an instance of the `String` type
  2. Call the specified method on the instance
  3. Destroy the instance
* Automatically created primitive wrapper objects exist for only one line of code before they are destroyed. This means that properties and methods cannot be added at runtime. Take this for example:
      var s1 = "some test";
      s1.color = "red";
      alert(s1.color); //undefined
  `String` object that was created in the second line is destroyed by the time the third line is executed. The third line creates its own `String` object, which doesn't have the `color` property.
* Calling a primitive wrapper constructor using `new` is not the same as calling the casting function of the same name, for example:
      var value = "25";
      var number = Number(value);
      alert(typeof number); //"number"
      
      var obj = new Number(value);
      alert(typeof obj); //"object"
* A `Boolean` object is an instance of the `Boolean` type and will return `true` when used with the `instanceof` operator, whereas a primitive value returns `false`
* `toFixed()` method returns a string representation of a number with a specified number of decimal points. If the number has more than the given number of decimal places, the result is rounded to the nearest decimal place.
* `toExponential()` returns a string with the number formatted in exponential notation.
* `toPrecision()` returns either the fixed or the exponential representation of a number, depending on which makes the most sense. This method takes on argument, which is the total number of digits to use to represent the number (not including exponents).
* ECMAScript provides `replace()` method to simplify replacing substrings. If the first argument is a string, then only the first occurrence of the substring will be replaced. The only way to replace all instances of a substring is to provide a regular expression with the global flag specified.
* `encodeURI()` does not encode special characters that are part of a URI, such as the colon, forward slash, question mark, and pound sign, whereas `encodeURIComponent()` encodes every nonstandard character it finds.
* `Math.random()` returns a random number between 0(inclusive) and 1(exclusive).