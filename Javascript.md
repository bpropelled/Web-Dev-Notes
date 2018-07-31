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

## Different Ways to Get Elements in Dom
These all return either a single element or collection of elements, but get them different ways:

- querySelector returns the first single element in the document that matches the CSS-type selector
- querySelectorAll returns a collection of all elements in the document that match the selector
- getElementsByClassName returns a collection of elements that have the specified class (not a selector)
- getElementById*returns the single element in the document that has the specified ID (there can only be one)
- getElementsbyTagName returns a collection of elements that have the specified tag name (type)

## Convert Nodelist from querySelectorAll to an Array
Rather than working with the NodeList that querySelectorAll provides, here is a neat trick to convert it into an array
```javascript
let x = Array.from(document.querySelectorAll('li'));
```

## Defer loading of non-critical scripts.

What it does is simple: it’s a bullet-proof way to ensure that these scripts begin loading only after the main page is done.
```javascript
  function insert(src, id){
    var d = document;
    var js, fjs = d.getElementsByTagName('script')[0];
    if (d.getElementById(id)) return;
    js = d.createElement('script'); 
    js.id = id;
    js.src = src;
    fjs.parentNode.insertBefore(js, fjs);
  }
  function defer() {
    insert("/path/to/stuff.js", "defered");
  }
  if (window.addEventListener)
    window.addEventListener("load", defer, false);
  else if (window.attachEvent)
    window.attachEvent("onload", defer);
  else window.onload = defer;

  ```