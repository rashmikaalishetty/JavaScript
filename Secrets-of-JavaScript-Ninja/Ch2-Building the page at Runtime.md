### This chapter covers

- Steps in the lifecycle of a web application
- Processing HTML code to produce a web page
- Order of executing JavaScript code
- Achieving interactivity with events
- The event loop

```note
Does the browser always build the page exactly according
to the given HTML?

No, browser doesn't always build the page exactly to your HTML. It

- Autocorrects the errors in the HTML (like missing the closing tags)
- CSS & JS can change the structure
- DevTools show the corrected sturcture
```

### Client side web application life cycle overview

`Step 1:` User enters the url in the browser or clicks on any link

`Step 2:` On behalf on user, browser sends the req to the server

`Step 3:` The server sends the response to the client(has HTML,CSS,JS code)

`Step 4:` The client processes the response code and builds the resulting page

`Step 5:` Enters event handling loop and waits for the events and start invoking the event handlers.

`Step 6:` The lifecycle ends when user closes or leaves the web page.

### Page Building phase

After the server has sent the response to the browser, the goal of this phase is to build the UI of the web application in 2 steps

1. Parsing the HTML and building DOM (while parsing html code)
2. Executing JS code (when encountered script tag) - whenever it encounters the script tag, browser pauses DOM and executes JS code by browsers JS engine.

**HTML code is a blueprint the browser follows while constructing the initial DOM.**

The browser provides an API through a global object that can
be used by the JavaScript engine to interact with and modify the page - `window object`

Through window object, all other global objects, global variables even the user defined one's, all browser API's are accessible.

### What is the main property of global object window which represents the DOM of the currect page ?

`document`

2 types of JS code which defines when that code is executed

- Global code
- Function code

`Global code:` Executed automatically by the JS engine line by line as it is encountered.

`Function code:` In order to be executed, has to be called by either the global code, or by other functions or by the browser.

```note
JS can't select or modify the elements that hasn't been created yet, that's the reason people put their script tag at the bottom of the page
```

**Global state of JS code persists which means, all user defined global variables created in one script is accessible to JS code in other script, bcoz of the global window object stores all global variables during the entire lifecycle**

After Page Building phase -> Event handling phase

### Event Handling

Client side web apps are GUI apps - they react to diff kinds of events : mousemoves, clicks, keyboard presses and so on.

Single threaded execution - single piece of code is executed at once.
JS has Window object (one teller) - events are processed one at a time as their turn occurs.

Whenever an event occurs, browser execute the associated even handler

Browser keeps track of all the events in the event queue

### Flowchart of event handling process

- The browser checks the head of the event queue.
- If there are no events, the browser keeps checking.
- If there’s an event at the head of the event queue,the browser takes it and executes the associated handler (if one exists).

During this execution, the rest of
the events patiently wait in the event queue for their turn to be processed.

```note
Browser itself is responsible for detecting events using its own internal processes, which is external to the page building and event handling phases of JS engine
```

Events are asynchronous - When you register an event handler, it doesn't run right away and doesn't block rest of the code, it runs when event actually happens.

Types of events:

- `Browser events:` Page finised loading or when it's unloaded.
- `Network events:` responses coming from server(AJAX events, server side events)

- `User events:` Mouse clicks, mouse moves, key presses.

- `Timer events:` when timeout expires, or an interval fires

### Registering event handlers

Event handlers are functions that we want executed whenever a particular event occurs.In order to happen this, we need to register first.

#### 2 types in registering the events

- **By assigning functions to special properties** :
  window.onload = function(){}; - assigns function to the special onload property of the window global object.

  - (An event handler for the load event is registered when DOM is built fully and ready to load)

**Not recommended as we can register only one function handler for a particular event, easy to overwrite the previous event handler functions**

- **Using built in addEventListener method** :

```note
  document.body.eventListener("mousemove", function(){
  var second = document.getElementById("second);
  addMessage(second, "Event:mousemove");
  })
```

- uses eventListener method on HTML element by specifind type of event and event handler function

### Exercises

- **1 What are the two phases in the lifecycle of a client-side web application?**

  - Page Building phase
  - Event handling phase

- **2 What is the main advantage of using the addEventListener method to register an event handler versus assigning a handler to a specific element property?**

  - Multiple event handlers can be attached to the same event, same element using eventListener method, in contrast using property like element.onclick will overwrite existing handler

- **3 How many events can be processed at once?**

  - Only one event is processed at a time, other events must wait until call stack is emply

- **4 In what order are events from the event queue processed?**

  - Events are processes first come, first serve basis sequentially in which they are occured in the event queue.
