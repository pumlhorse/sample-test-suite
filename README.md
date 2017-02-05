# Pumlhorse Sample Test Suite

This is a sample test suite written in Pumlhorse. It has a set of integration tests to run against the (trivial) Recipe API.

The recipe API is hosted on [GoMix](https://gomix.com) and is written in [ExpressJs](http://expressjs.com). The source code
for the API is available on [GitHub](https://github.com/pumlhorse/sample-recipe-api). Recipes are stored based on API key
(i.e. you only access the values that were added with the given API key). They will also timeout after 10 minutes.

## Tested endpoints

* GET /recipes - Lists all recipes
* GET /recipes/:recipeId - Gets the recipe with the given ID (returns 404 if it doesn't exist)
* POST /recipes - Adds a new recipe (schema below)
* PUT /recipes/:recipeId - Updates an existing recipe (returns 404 if it doesn't exist)
* DELETE /recipes/:recipeId - Deletes a recipe (returns 404 if it doesn't exist)

### Recipe schema

```json
{
    "id": <string - UUID>,
    "name": <string>,
    "description": <string>,
    "author": <string>,
    "rating": <integer from 1 to 5>
}
```

### Authorization header

All calls must provide an `Authorization` header. The header value should be a unique value.
For example: `Authorization: 82df6064-9ffc-434c-9100-e940a6c58197`

The `recipeHelpers.js` module contains a function `getApiKey` that will auto generate a unique ID.

## Tools

In addition to the integration tests, there is a `tools` folder. The `dumpCache.puml` script 
prints out all the stored data.