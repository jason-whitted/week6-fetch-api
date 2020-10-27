# Async Programming
JavaScript is single-threaded.  It handles small executions over time via the event loop.

Many long-running tasks spend much of their time idling -- waiting for a response.  We can break up these long-running tasks into two blocks of code: 
- the block before the idling
- the block after idling

A pattern that would allow this to work:
```js
function longRunningTask(done) {
  // before idling
  // idling
  // after idling we invoke the done function
  done();
}
```

In this example, the `done` function is a **callback function**.

# Callback Functions

> A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

## Examples
```js
setTimeout(fn, 1000);
```

```js
var button = document.getElementById("my-button");
button.addEventHandler("click", fn);
```

Here `setTimeout` and `addEventHandler` are APIs that allows some code to be ran at a later time.  The implementers of these functions did not (and could not) know what you wanted to execute ahead of time.

This is called **inversion of control**.

> In software engineering, **inversion of control** (IoC) is a programming principle. IoC inverts the flow of control as compared to traditional control flow.

