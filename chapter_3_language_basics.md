# Chapter 3: Language Basics

* The first character of identifiers could be a dollar sign ($). Letters in an identifier may include extended ASCII or Unicode letter characters such as À and Æ.
* There are five simple data types (primitive types): Undefined, Null, Boolean, Number, and String. There is also one complex data type called Object.
* `typeof null` will return `object`, as the special value `null` is considered to be an empty object reference.
* Referring undeclared variable will cause an error. Only `typeof` can be called on an undeclared variable. The `typeof` operator will both return `undefined` when called on uninitialized or undeclared variable.
* `null == undefined` will return `true`
* Some conversions tips:
  1. Any nonempty string => `true`, ""(empty string) => `false`
  2. Any nonzero number (including `infinity`) => true, `0, NaN` => `false`
  3. Any object => `true`
* `Number.MIN_VALUE` => `5e-324`, `Number.MAX_VALUE` => `1.7976931348623157e+308`
* Any negative number that can't be represented is `-Infinity`, and any positive number that can't be represented is `Infinity`. If a calculation returns either positive or negative `Infinity`, that value cannot be used in any further calculations. 
* To determine if a value is finite, use `isFinite()` function.
* `Number.NEGATIVE_INFINITY` => `-Infinity`, `Number.POSITIVE_INFINITY` => `Infinity`
* Any operation involving `NaN` always returns `NaN`, `NaN` is not equal to any value, including `NaN`
* `0/0` => `NaN`, `1/0` => `Infinity`, `(-1)/0` => `-Infinity`
* `isNaN()` is used to determine if the value is "not a number", it will attempt to convert argument into a number. `isNaN` can be applied to objects. The object's `valueOf()` method is first called to determine if the returned value can be converted into a number. If not, the `toString()` method is called.
* `Number` function conversion rules:
  1. When applied to `null`, `Number()` returns `0`
  2. When applied to `undefined`, `Number()` returns `NaN`
  3. `011` => `11` (leading zeros are ignored)
  4. When applied to objects, the `valueOf` method is called and the returned value is converted based on the previously described rules. If that conversion results in `NaN`, the `toString()` method is called and the rules for converting strings are applied.
* `ParseInt` conversion rules:
  1. `parseInt("1234blue")` => `1234`
  2. `parseInt("")` => `NaN`
  3. `parseInt("070")` => `70` (ECMAScript 5)
* `parseFloat()` parses only decimal values. If the string represents a whole number (no decimal point or only a zero after the decimal point), `parseFloat()` returns an integer. `parseFloat("1234blue")` => `1234`
* Character literals such as `\n` `\unnnn` will be interpreted as if they were a single character.
* `toString()` is not available for `null` and `undefined`.
* `String(null)` => `"null"`, `String(undefined)` => `"undefined"`
* Rules for increment and decrement operators:
  1. When used on a string that is a valid representation of a number, convert to a number and apply the change. The variable is changed from a string to a number.
  2. When used on a string that is not a valid number, the variable's value is set to `NaN`. The variable is changed from a string to a number.
* When the unary plus is applied to a nonnumeric value, it performs the same conversion as the `Number()` casting function.
* All numbers in ECMAScript are stored in IEEE-754 64-bit format, but the bitwise operations don't work directly on the 64-bit representations. Instead, the value is converted into a 32-bit integer, the operation takes place, and the result is converted back into 64 bits.
* When outputting a negative number as a binary string, you get the binary code of the absolute value preceded by a minus sign, `-18.toString(2)` => `"-10010"`
* By default, all integers are represented as singed in ECMAScript.
* `NaN` and `Infinity` are treated as equivalent to 0 when used in bitwise operations.
* Bitwise NOT: negates the number and substracts 1.
* Left shift preserves the sign of the number it's operating on. `-2 << 5` => `-64`
* ECMAScript fills empty bits produced by signed right shift with the value in the sign bit to create a complete number, while fills them with zeros when unsigned right shifting.
* The unsigned-right-shift operator considers the binary representation of the negative number to be representative of a positive number instead. Negative number is the two's complement of its absolute value.
* `!!` => `Boolean()`
* Logical AND rules:
  1. If the first operand is an object, then the second operand is always returned.
  2. If the second operand is an object, then the object is returned only if the first operand evaluates to `true`.
  3. If both operands are objects, then the second operand is returned.
* Multiplicative operators rules:
  1. `Infinity * 0` => `NaN`
  2. `Infinity/Infinity` => `NaN`
  3. If `Infinity` is divided by any nonzero number, the result is either `Infinity` or `-Infinity`, depending on the sign of the second operand.
* Modulus rules
  1. If the dividend is an infinite number and the divisor is a finite number, the result is `NaN`
  2. If the dividend is a finite number and the divisor is 0, the result is `NaN`
  3. `Infinity%Infinity` => `NaN`
  4. If the dividend is a finite number and the divisor is an infinite number, then the result is the dividend
* Additive operators rules
  1. `Infinity + (-Infinity)` => `NaN`
  2. `(+0) + (-0)` => `+0`
* Relational operators rules
  1. If two operands are strings, compare the character codes of each corresponding character in the string
  2. If one operand is a number, convert the other operand to a number and perform a numeric comparison
  3. The result of any relational operation with `NaN` is `false`
* Equal operators rules
  1. If an operand is a Boolean value, convert it into a numeric value before checking for equality. `false` => `0`, `true` => `1`, `true == 2` => `false`
  2. `null == undefined` => `true`, `null === undefined` => `false`
  3. Values of `null` and `undefined` cannot be converted into any other values for equality checking, `undefined == 0` => `false`
  4. If either operand is `NaN`, the equal operator returns `false` and the not-equal operator returns `true`
  5. If both operands are objects, then they are compared to see if they point to the same object
* The `for-in` is used to enumerate the properties of an object, the order in which property names are returned cannot necessarily be predicted.
* It's possible to label statements for later use
* The `switch` statement compares values using the identically equal operators, so no type coercion occurs.
* The values of `arguments` always stay in sync with the values of the corresponding named parameters. This doesn't mean that both access the same memory space, though; their memory spaces are separate but happen to be kept in sync. The length of the `arguments` object is set based on the number of arguments passed in, not the number of named arguments listed for the function.
* All arguments in ECMAScript are passed by value, it's not possible to pass arguments by reference.