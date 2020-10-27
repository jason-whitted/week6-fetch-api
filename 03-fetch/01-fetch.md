# Fetch

As a developer, you frequently need a script to call off to a server and retrieve a resource.  The resources could be anything really -- images, text, HTML, JSON, etc.

> The Fetch API provides an interface for fetching resources.

## Syntax
```js
var responsePromise = fetch(resource[, init]);
```

### Parameters
- `resource`
  - String
  - The URL of the resource you want to fetch.
- `init`
  - Object _(optional)_
  - An object containing any custom settings that you want to apply to the request. Some possible options are:
    - `method`
      - String
      - The request method, e.g., `GET`, `POST`.
    - `headers`
      - Object
      - Any headers you want to add to your request.
    - `body`
      - String
      - Any body that you want to add to your request.

### Return Value
A `Promise` that resolves to a `Response` object.
