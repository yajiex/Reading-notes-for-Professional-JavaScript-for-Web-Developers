# Chapter 20: JSON
* There is no trailing semicolon (not needed since this isn't a JavaScript statement). Once again, the quotes around the property name are required to be valid JSON.
* When serializing a JavaScript object, all functions and prototype members are intentionally omitted from the result. Additionally, any property whose value is undefined is also skipped. You're left with just a representation of the instance properties that are one of the JSON data types.
* The `JSON.stringify()` method actually accepts two arguments in addition to the object to serialize. These arguments allow you to specify alternate ways to serialize a JavaScript object. The first argument is a filter, which can be either an array or a function, and the second argument is an option for indenting the resulting JSON string. 
* If the argument is an array, then `JSON.stringify()` will include only object properties that are listed in the array. 
* When the second argument is a function, the behavior is slightly different. The provided function receives two arguments: the property key name and the property value. In order to change the serialization of the object, return the value that should be included for that key. Keep in mind that returning undefined will result in the property being omitted from the result.
* The third argument of `JSON.stringify()` controls indentation and white space. When this argument is a number, it represents the number of spaces to indent each level. `JSON.stringify()` also inserts new lines into the JSON string for easier reading. This happens for all valid indentation argument values. The maximum numeric indentation value is 10; passing in a value larger than 10 automatically sets the value to 10. If the indentation argument is a string instead of a number, then the string is used as the indentation character for the JSON string instead of a space. There is a ten-character limit on the indentation string to use. If a string longer than ten characters is used, then it is truncated to the first ten characters.
* you can add a `toJSON()` method to the object and have it return the proper JSON representation for itself.
* When an object is passed into `JSON.stringify()`, the following steps are taken:
  1. Call the `toJSON()` method if it's available to retrieve the actual value. Use the default serialization otherwise.
  2. If the second argument is provided, apply the filter. The value that is passed into a filter function will be the value returned from step 1.
  3. Each value from step 2 is serialized appropriately.
  4. If the third argument is provided, format appropriately. It's important to understand this order when deciding whether to create
* The `JSON.parse()` method also accepts an additional argument, which is a function that is called on each key-value pair. The function is called a `reviver` function. If the `reviver` function returns `undefined`, then the key is removed from the result; if it returns any other value, that value is inserted into the result.
* 

