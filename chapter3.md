# 3 Language Basics
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
* `isNaN()` is used to determine if the value is "not a number", it will attemp to convert argument into a number. `isNaN` can be applied to objects. The object's `valueOf()` method is first called to determine if the returned value can be converted into a number. If not, the `toString()` method is called.
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
* 