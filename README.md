# Express.js Route Handler Missing Error Handling for Invalid User IDs

This repository demonstrates a common error in Express.js route handlers: insufficient error handling for invalid input.  Specifically, the example shows a route that fetches a user by ID but lacks proper checks to handle cases where the ID is not a valid integer.

## Bug Description
The `/users/:id` route attempts to find a user based on the provided ID.  However, it doesn't handle the scenario where `req.params.id` is not a valid integer.  If the ID is not an integer, `parseInt(userId)` will return `NaN`, causing the `find()` method to fail silently and potentially throwing an error or returning an unexpected result.

## Solution
The solution involves adding explicit error handling to check if `parseInt(userId)` successfully converts the ID to an integer and to handle the case where the user is not found.