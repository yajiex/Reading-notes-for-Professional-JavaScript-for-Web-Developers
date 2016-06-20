# 5 Reference Types
* `length` is not read-only. By setting the `length` property, you can easily remove items from or add item to the end of the array. If the `length` were set to a number greater than the number of items in the array, the new items would each get filled with the value of `undefined`
* Use `Array.isArray` to detect arrays
* Three supported flags represent matching modes:
  1. `g`: global mode
  2. `i`: case-insensitive mode
  3. `m`: multiline mode
* All metacharacters must be double-escaped, such as `\n` (the `\` character, which is normally escaped in strings as `\\` becomes `\\\\` when used in a regular-expression string).
* The inherited methods of `toLocaleString()` and `toString()` each return the literal representation of the regular expression, regardless of how it was created. The `valueOf()` method for a regular expression returns the regular expression itself.