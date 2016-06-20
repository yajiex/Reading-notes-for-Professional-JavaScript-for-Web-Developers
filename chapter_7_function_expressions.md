# Chapter 7: Function Expressions

* Nonstandard `name` property on functions: return the identifier that immediately follows the `function` keyword
* Closures are functions that have access to variables from another function's scope.
* Anonymous functions are not bound to an object in this context, meaning the `this` object points to `window` unless executing in strict mode (where `this` is `undefined`). 
      var name = "The window";
      var object = {
          name: "My Object",
          getNameFunc: function() {
              return function() {
                  return this.name;
              };
          }
      };
      alert(object.getNameFunc()()); // "The window"
* In the following example, because the value of the assignment expression is the function itself, the `this` value is not maintained, and so `The window` is returned.
      var name = "The window";
      var object = {
          name: "My object",
          getName: function() {
              return this.name;
          }
      };
      (object.getName = object.getName)(); //"The window"
* JavaScript will never tell you if you've declared the same variable more than once; it simply ignores all subsequent declarations (though it will honor initializations).
* JavaScript sees the `function` keyword as the beginning of a function declaration, and function declarations cannot be followed by parentheses. Function expressions, however, can be followed by parentheses. So the following code causes errors:
      function() {
      }(); // error!