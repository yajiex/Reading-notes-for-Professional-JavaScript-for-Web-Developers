# 5 Reference Types
* `length` is not read-only. By setting the `length` property, you can easily remove items from or add item to the end of the array. If the `length` were set to a number greater than the number of items in the array, the new items would each get filled with the value of `undefined`
* Use `Array.isArray` to detect arrays
* Three supported flags represent matching modes:
  1. `g`: global mode
  2. `i`: case-insensitive mode
  3. `m`: multiline mode
* All metacharacters must be double-escaped, such as `\n` (the `\` character, which is normally escaped in strings as `\\` becomes `\\\\` when used in a regular-expression string).
* The inherited methods of `toLocaleString()` and `toString()` each return the literal representation of the regular expression, regardless of how it was created. The `valueOf()` method for a regular expression returns the regular expression itself.
* Because functions are objects, function names are simply pointers to function objects.
* Function declarations are read and available in an execution context before any code is executed, whereas function expressions aren't complete until the execution reaches that line of code. As the code is being evaluated, the JavaScript engine does a first pass for function declarations and pulls them to the top of the source tree. So even though the function declaration appears after its usage in the actual source code, the engine changes this to boist the function declarations to the top.
* `arguments` object has a property named `called`, which is a pointer to the function that owns the arguments object.