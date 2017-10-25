 # Javascript Notes
 
 ### Get Current Year in JS
 ```javascript
 var d = new Date();
 var y = d.getYear();
 ```
 
 ## SIMPLE MODULE PATTERN
 Create an enclosing function, from within that function it can return one or more inner properties or methods. The return statement provides a way to make only the properties and methods you want publically available so in the example below the ‘getBar’ method is considered the public API and it has access to the inner private scope e.g. it can access and return the ‘obj’ variable. This keeps your code tidy and only exposes the parts of the code publically that you want.

It is called a singleton because only one instance of the module is available to the application in the global scope.


  ## The REVEALING MODULE PATTERN SINGLETON
 ```javascript
var foo = function() {
  var obj = {
     bar: “bar”
  };
  function getBar() {
    console.log(obj.bar);
  }
  return {
    getBar: getBar
  };
}();
foo.getBar();
```

 ## The REVEALING MODULE PATTERN CONSTRUCTOR
 
 This works in a very similar way to the Singleton method above but it uses a constructor function pattern to allow you to create multiple instances of the module.
 
 ```javascript
 var Foo = function() {
  var obj = {
    bar: “bar”
  };
  function getBar() {
    console.log(obj.bar);
  }
  return {
    getBar: getBar
  };
};
var newFoo = new Foo(); // create a new instance of the Foo object
newFoo.getBar(); // access the getBar method on the new object
```

## Use Vanilla JS for document loaded like $(document).ready(function(){});

```javascript
document.addEventListener('DOMContentLoaded', function() {
    // STUFF HERE

}, false);

```