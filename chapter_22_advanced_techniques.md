# Chapter 22: Advanced Techniques
* The `instanceof` operator is problematic in that it's difficult to use when multiple global scopes are present, such as when there are multiple frames. The classic example of this problem is attempting to identify an object as an array using the following code: `var isArray = value instanceof Array;` This code returns `true` only if value is an array and was created in the same global scope as the `Array` constructor. (Remember, Array is a property of window.) If value is an array from another frame, this code returns false.
* The native `toString()` method of Object can be called with any value to return a string in the format `"[object NativeConstructorName]"`. Each object has an internal `[[Class]]` property that specifies the constructor name that is returned as part of this string.
* Function currying creates functions that have one or more arguments already set (also called partial function application).

