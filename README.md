# Express.js Route Parameter Error Handling Bug

This repository demonstrates a common error in Express.js route handlers: the lack of proper error handling for invalid input parameters.  Specifically, the route `/users/:id` attempts to parse the `id` parameter as an integer without checking its validity.  This can lead to unexpected behavior or application crashes.

## Bug Description

The `bug.js` file contains the erroneous code.  It fetches a user based on their ID, but it doesn't handle cases where the `id` parameter is not a valid integer. This can result in `NaN` being used in the `find()` method which will not work properly and will not find a user even if there is one. This might lead to unexpected errors.

## Solution

The `bugSolution.js` file provides a corrected version of the code.  It adds input validation to ensure that the `id` parameter is a valid integer before attempting to access the user data.  This prevents errors and improves the application's robustness.

## How to Reproduce

1. Clone this repository.
2. Navigate to the directory.
3. Run `node bug.js` and then try to access `/users/abc` to see the error.
4. Run `node bugSolution.js` and then try to access `/users/abc` or `/users/1` to compare the results.  The solution will return 400 for invalid parameters and 404 if the user is not found. 