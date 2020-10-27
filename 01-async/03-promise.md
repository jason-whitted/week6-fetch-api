# Scenario

Let's pretend we have been given an API with a `getFavoriteColor` function that returns a `Promise`.

We'll pretend the `getFavoriteColor` function displays some amazing UI that allows the user to specify their favorite color.  Whenever the user selects a value then the promise is resolved with their favorite color.

### Syntax
```js
getFavoriteColor();
```

#### Return Value
A `Promise` object

## Promise
> A `Promise` is a proxy for a value not necessarily known when the promise is created. It allows you to associate handlers with an asynchronous action's eventual success value or failure reason.

A promise object contains a few methods.

### Promise.`then(onResolved)`
The `then()` method allows the `onResolved` callback function to be executed whenever the promise resolves successfully.

The signature for `then()` is:
```js
(Function) -> Promise
```

The signature for the `onResolved` callback function is:
```js
function(value) {
  // fulfillment

  // Want to continue as a failure?
  throw error; // throw new Error();

  // Want to continue as a success?
  return newValue;
}
```

### Promise.`catch(onRejected)`
The `catch()` method allows the `onRejected` callback function to be executed whenever the promise fails.

The signature for `catch()` is:
```js
(Function) -> Promise
```

The signature for the `onRejected` callback function is:
```js
function(error) {
  // fulfillment

  // Want to continue as a failure?
  throw error; // throw new Error();

  // Want to continue as a success?
  return newValue;
}
```

### Example
```js
var favoriteColor;

function storeFavoriteColor(color) {
  favoriteColor = color;
}

function printFavoriteColor() {
  console.log("Favorite color is " + favoriteColor + "!!!");
}

var promise = getFavoriteColor()
promise = promise.then(storeFavoriteColor)
promise = promise.then(printFavoriteColor);
```

### Chaining
Because the `then` and `catch` functions both return a `Promise` object, you can chain `then` and `catch` functions together.

In the previous example the `promise` variable was unused; therefore, it is unnecessary.  If we removed that variable and used chaining, we would end up with.

```js
var favoriteColor;

function storeFavoriteColor(color) {
  favoriteColor = color;
}

function printFavoriteColor() {
  console.log("Favorite color is " + favoriteColor + "!!!");
}

getFavoriteColor()
  .then(storeFavoriteColor)
  .then(printFavoriteColor);
```

### Error Handling
We could incorporate error handling with `catch` and default their favorite color to `"light tan"`.

```js
getFavoriteColor()
  .catch(function(error) {
    console.log("An error occurred", error);
    return "light tan";
  })
  .then(storeFavoriteColor)
  .then(printFavoriteColor);
```

### Aside
I have purposefuly not shown how to create a new promise object.  This will be covered in the future.  For now we only need to concern ourselves with how to use a Promise object (via `then(fn)` and `catch(fn)` methods).
