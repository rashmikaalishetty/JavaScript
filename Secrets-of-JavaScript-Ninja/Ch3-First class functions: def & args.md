### This chapter covers

- Why understanding functions is so crucial
- How functions are first-class objects
- The ways to define a function
- The secrets of how parameters are assigned

### Objects in JS:

objects in javascript possess certain capabilities.

- created via literals {} , assigned to the variables.

  - var ninja = {};

- assigned to array entries.

  - ninjaArray.push({})

- assigns a new object as a property of another object

  - ninja.data = {}

- Objects can be passed as an argument to the function
  ```note
  function hide(ninja){
    ninja.visibility = false;
  }
  ```
- Objects can be returned as values from the functions

  ```note
  function returnNewNinja(){
    return {};
  }
  ```

- Objects possess properties that can be dynamically created and assigned
  - var ninja = {};
    ninja.name = "Rashmika";

### Functions as first class objects

In JS, functions possess all the capabilities of objects and treated like any other objects in the language.

function ninjaFun(){}; - created via literals

var ninjaFun = function(){}; - assigns new func to a variable
ninjaArray.push(function(){}); - adds a new func to an array
ninja.data = function(){}; - assigns a new func as a property of another object

- Passed as an argument to another function
  ```note
  function call(ninjaFunc){
    ninjaFunc()
  }
  call(function(){})
  ```
- Returned as values from other functions

  ```note
  function returnNewNinjaFunc(){
    return function(){};
  }

  ```

- Possess properties that can be dynamically created and assigned

```note
var ninjaFunc = function(){};
ninjaFunc.name = "Rashmika";
```

**Functions are objects with just additional capability of being invoked, they must be called or invoked in order to perform an action.**

### Callback functions:

We're establishing the function that other code will later 'callback' at an appropriate point of execution.

Examples:

- executing code on button click
- receiving data from the server
- animating parts of your UI
- handling events

```note
function ninjaUseless(ninjaCallback){
  return ninjaCallback();
}

function getText(){
  return text;
}

assert(ninjaUseless(getText) == text, "Success")
```

The useless functions is called with getText as an argument.Within the body of useless function getText is referenced through ninjaCallback parameter then by calling the ninjaCallback, we cause the execution of the getText function.

Here, we called our own callback, but callbacks can also be called by the `browser`.

```note
document.body.eventListener("mousemove", function(){
  var second = document.getElemntById("second");
  addMessage(second, "Event:Mouse move");
});
```

Its also a callback function, but called by the browser when mouse move event occurs

**In what situations might callback functions be used syn-
chronously? Asynchronously?**

```note
synchronous callback
[1, 2, 3].forEach(num => console.log(num));
asynchronous callback
setTimeout(() => console.log("Hi"), 1000);
```

### Use of callback - sorting with a comparator

All javascript arrays have access to the sort method which requires us to decide comparison algorithm which tells sort algorithm how the values need to be ordered.

Callbacks helps here instead of us letting to know what values go before other values, we provide function that performs the comparison.

We will give sort algorithm access to this function as a callback

if callback returns positive number - reverse it, negative - if not, 0 - equal.
