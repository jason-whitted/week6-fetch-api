# Scenario

## Provided Functionality
Let's pretend we have been given an API with a `getFavoriteColor` function.

We'll pretend the `getFavoriteColor` function displays some amazing UI that allows the user to specify their favorite color.  Whenever the user selects their favorite color then a callback function is called.

### Syntax
```js
getFavoriteColor(callback);
```

#### Parameters
##### `callback`
A function to be executed after the user selects their favorite color.

The signature of this function is expected to be:
```js
function(color) {
}
```

#### Return Value
`undefined`

-----
## Example Solution
Imagine this implementation:

```js
var favoriteColor;

function storeFavoriteColor(color) {
  favoriteColor = color;
}

getFavoriteColor(storeFavoriteColor);
```

The callback function `storeFavoriteColor` will be called by `getFavoriteColor` as soon as the user selects their favorite color.

This will store the selected color in the `favoriteColor` global variable.

## New Requirement
Now, let's create a new function to log their favorite color to the console.
```js
function printFavoriteColor() {
  console.log("Favorite color is " + favoriteColor + "!!!");
}
```

We want to call this function immediately after the `storeFavoriteColor` function has been called.

## A Solution
We could modify the `storeFavoriteColor` function.
```js
var favoriteColor;

function printFavoriteColor() {
  console.log("Favorite color is " + favoriteColor + "!!!");
}

function storeFavoriteColor(color) {
  favoriteColor = color;
  printFavoriteColor();
}

getFavoriteColor(storeFavoriteColor);
```

But if we do this, we have now bastardized the `storeFavoriteColor` function.  It no longer is just storing the favorite color.  It's now also printing the favorite color.

Ideally we'd like to be able to run the `storeFavoriteColor` callback function and **THEN** run some other function.
