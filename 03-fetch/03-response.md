# Response

> The `Response` interface of the Fetch API represents the response to a request.

## Properties
- `headers`
  - Object
  - The Headers object associated with the response.
- `ok`
  - Boolean
  - A boolean indicating whether the response was successful (status in the range 200–299) or not.
- `status`
  - Number
  - The status code of the response. (This will be 200 for a success).
- `statusText`
  - String
  - The status message corresponding to the status code. (e.g., `OK` for 200).

## Methods
  - `json()`
    - Promise
    - Takes a Response stream and reads it to completion. It returns a promise that resolves with the result of parsing the body text as a JSON, which is an object.
  - `text()`
    - Promise
    - Takes a Response stream and reads it to completion. It returns a promise that resolves with a string.