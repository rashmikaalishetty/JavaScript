`Babel:`
It is a javascript compiler which converts code written in newer version into a format that older browsers understand.
Ex:

```note
new version code:
// ES6 code
const greet = (name) => {
console.log(`Hello, ${name}!`);
}

greet('Rashmika');
```

`transpiled code by babel:`
// Transpiled ES5 code

```note
'use strict';

var greet = function greet(name) {
console.log('Hello, ' + name + '!');
};

greet('Rashmika');
```

Some new features that most developers use everyday but not supported by older browsers are: Arrow functions, classes, let &
const, template literals, spread syntax, promises, modules etc

### Functions are first class objects

They are just treated like any other value, like numbers,literals or strings.They can be asigned to variables, pass as an argument in the function, returned from other functions and can have properties.

`DOM:` Document Object Model is an object which is a structural representation of web page you see in the browser

- The browser constructs the DOM when you load the web page and structures all the elements in the tree like datastructure and
  all elements are nodes in the tree
- javascript can access the DOM to dynamically alter the content, structure and style of the web page

### Debugging JS tools:

Firebug - Firefox extension

Chrome Dev Tools - Chrome

F12 Developer Tools - Internet Explorer

Webkit Inspector - Safari

Offer functionalities like exploring the DOM, debugging JS, editing CSS styles, tracking network events etc

### Testing

primary tool we use for testing is the `assert` function, whose functions is to assert that the premise is either true of false

assert(condition, msg);
