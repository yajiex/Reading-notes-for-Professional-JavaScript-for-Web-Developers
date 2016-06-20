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
* `isPrototypeOf()`: determine if this relationship exists between objects
* `Object.getPrototypeOf()`: return the value of `Prototype`.
* 