# Chapter 22: Advanced Techniques
* The `instanceof` operator is problematic in that it's difficult to use when multiple global scopes are present, such as when there are multiple frames. The classic example of this problem is attempting to identify an object as an array using the following code: `var isArray = value instanceof Array;` This code returns `true` only if value is an array and was created in the same global scope as the `Array` constructor. (Remember, Array is a property of window.) If value is an array from another frame, this code returns false.
* The native `toString()` method of Object can be called with any value to return a string in the format `"[object NativeConstructorName]"`. Each object has an internal `[[Class]]` property that specifies the constructor name that is returned as part of this string.
* Function currying creates functions that have one or more arguments already set (also called partial function application). 
      function curry(fn){
        var args = Array.prototype.slice.call(arguments, 1);
        return function(){
          var innerArgs = Array.prototype.slice.call(arguments),
          finalArgs = args.concat(innerArgs);
          return fn.apply(null, finalArgs);
        };
      }
* `Object.preventExtensions()` => new properties and methods cannot be added to the object.
* `Object.isExtensible()` => determine that an object can't have extensions
* Sealed objects aren't extensible and existing object members have their `[[Configurable]]` attribute set to false. This means properties and methods can't be deleted as data properties cannot be changed to accessor properties or vice versa using `Object.defineProperty()`. Property values can still be changed. You can seal an object by using the `Object.seal()` method. You can determine if an object is sealed by using `Object.isSealed()`.
* The strictest type of tamper-proof object is a frozen object. Frozen objects aren't extensible and are sealed, and also data properties have their `[[Writable]]` attribute set to false. Accessor properties may still be written to but only if a `[[Set]]` function has been defined. ECMAScript 5 defines `Object.freeze()` to allow freezing of objects.
* There is also an `Object.isFrozen()` method to detect frozen objects
* Each browser window, tab, or frame has its own code execution queue. This means that the timing of cross-frame or cross-window JavaScript calls may result in race conditions when code is executed synchronously.
