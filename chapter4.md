# 4 Variables, Scope, and Memory
* Primitive values can't have properties added to them.
* When a primitive value is assigned from one variable to another, the value stored on the variable object is created and copied into the location for the new variable. These values are completely separated.
* When a reference value is assigned from one variable to another, two variables point to exactly the same object, so changes to one are reflected on the other.
* `typeof` works well for primitive values, while `instanceof` is used for reference type. If `instanceof` is used with a primitive value, it will always return `false`, because primitives aren't objects.
