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

```note
function ninjaFun(){}; - created via literals

var ninjaFun = function(){}; - assigns new func to a variable
ninjaArray.push(function(){}); - adds a new func to an array
ninja.data = function(){}; - assigns a new func as a property of another object
```

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

### Fun with functions as objects

`Storing Functions:` Storing functions in a collection allows us to easily manage related functions.

Ex: Callbacks are stored in a collection when an event occurs

`Challenge:` We can't determine which is new function and should be added and which is not, bcoz we don't want any duplicates as single event would result in multiple calls to the same callback.

`Naive sol`: Storing functions in an array, loop through the array and check for the duplicates.

By tacking a property onto a function,
we can keep track of it. In that way, we can be sure
that our function has been added only once.

`Self memoization functions:` It is the process of building a function that is capable of storing its previously computer result.

It means whenever a function computes its result, we store the result alongside the function arguments, in this way whenever another invocation occurs for the same set of arguments, we can return the previously stored result, instead of calculating anew.

```note
`Usage:` 1.While performing calculations for animations.
2.Searching data that doesn't change that often.
3.Any time consuming math.
```

### Defining Functions: 4 ways

- `Function Declaration & function expressions: `function myFun(){ return 1;}

- `Arrow Functions:` often called as lambda functions, with less syntactic clutter

  - myArg => myArg\*2

- `Function constructors:` dynamically constructs a new function from a string that's also generated dynamically

  - new Function('a', 'b', 'return a + b')

- `Generator Functions:` Unlike normal functions, can be exited and reentered later in the application execution, while keeping the values of the variables across these re-entrances.
  - function\* myGen(){ yield 1; }

**The way in which a func-
tion is defined significantly influences when the function is available to be invoked
and how it behaves, as well as on which object the function can be invoked.**

### Function declarations & function expression:

The function declaration starts on its own.

```note
function rashmika() {
return "rashmika here";
}
```

Function defined within another functions:

```note
function ninja() {
function hiddenNinja() {
return "ninja here";
}
return hiddenNinja();
}
```

### Function expressions:

functions that are always part of another statement.

Ex:as the right side of function expression or as an argument to another function or as a function return value

Since functions are first class objects, they can be treated like any other expressions.

```note
Number literals:
var a = 3;
myFunction(4);

We can use function literals in the same location as like literals:
var a = function() {};
myFunction(function(){});
```

**Function declarations are separate statements but can be contained within the body of another function , in contrast function expressions are always part of other statements**

**Function name is mandatory in function declaration(coz theu stand on their own) whereas optional in function expressions.(if a function expression is assigned to a variable, we can use that variable to invoke the function)**

var doNothing = function(){};
doNothing();

Or, if it’s an argument to another function, we can invoke it within that function
through the matching parameter name:

function doSomething(action) {

action();

}
