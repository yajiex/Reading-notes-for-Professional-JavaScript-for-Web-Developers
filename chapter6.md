# 6 Object-Oriented Programming
* Data properties have four attributes describing their behavior:
  1. `Configurable`: indicates if the property may be redefined by removing the property via `delete`, changing the property's attributes, or changing the property into an accessor property.
  2. `Enumerable`: indicates if the property will be returned in a `for-in` loop.
  3. `Writable`: indicates if the property's value can be changed.
  4. `Value`: 
* To change any of the default property attributes, use `Object.defineProperty()`
* Once a property has been defined as nonconfigurable, it cannot become configurable again. Any attempt to call `Object.defineProperty()` and change any attribute other than `writable` causes an error.
* `Object.defineProperties()`: define more than one property on an object
* `Object.getOwnPropertyDescriptor()`: retrieve the property descriptor for a given property
* In the following Constructor Pattern sample, `person1` and `person2` both have a `contructor` property that points back to `Person`. The major downside to constructors is that methods are created once for each instance.    
      function Person(name, age) {
          this.name = name;
          this.age = age;
      }
      var person1 = new Person("Nicholas", 29);
      var person2 = new Person("Greg", 27);
* In the following Prototype Pattern sample, `Person.prototype` points to the prototype object but `Person.prototype.constructor` points back to `Person`.
      function Person() {}
      Person.prototype.name = "Nicholas";
      var person1 = new Person();
      person1.name = "Greg";
      delete person1.name;
      alert(person1.name); // Nicholas - from the prototype
   Once a property is added to the object instance, it shadows any properties of the same name on the prototype, which means that it blocks access to the property on the prototype without altering it. Setting the property to `null` only sets the property on the instance and doesn't restore the link to the prototype. The `delete` operator, however, completely removes the instance property and allows the `prototype` property to be accessed again.
* `isPrototypeOf()`: determine if this relationship exists between objects
* `Object.getPrototypeOf()`: return the value of `Prototype`.
* `Object.getOwnPropertyDescriptor()` works only on instance properties; to retrieve the descriptor of a prototype property, call `Object.getOwnPropertyDescriptor()` on the prototype object directly.
* For `in` operator, when used on its own, the `in` operator returns `true` when a property of the given name is accessible by the object, which is to say that the property may exist on the instance or on the prototype.
* `Object.keys()`: return an array of strings containing the names of all enumerable properties
* `Object.getOwnPropertyNames()`: return all instance properties, whether enumerable or not
* In the following example, the `constructor` property no longer points to `Person`. `constructor` property is equal to that of a completely new object (the `Object` constructor) instead of the function itself.
      function Person(){}
      Person.prototype = {
          name: "Nicholas"
      };
* 