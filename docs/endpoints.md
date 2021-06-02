# Endpoints

This page explains how endpoints on publiq APIs should be named and structured.

publiq APIs follow the REST format. This means that your paths should be structured around resources and collections and you should avoid verbs to describe operations in path names by using the correct HTTP methods instead.

Resources usually have an id, but can also be singletons. For example a `GET /user` endpoint can be provided to retrieve info about the current user.

You can find a brief intro to REST [here](https://www.infoq.com/articles/rest-introduction/) for more info.

## Method

Every endpoint can support one or more HTTP methods.

### GET

Always use `GET` for requests that retrieve data, because it is the most optimal method for easy caching in browsers, proxy servers, etc. Note that `GET` requests must be [safe](https://developer.mozilla.org/en-US/docs/Glossary/Safe/HTTP) and should never alter server state.

### POST / PUT / PATCH

Always use `POST` for requests that create a new resource without a predefined id.

Always use `PUT` for requests that create a resource with a predefined id, or for requests that update resources _completely_ by their id. The id must in both cases be specified in the URL. The URL should be the same for the create and update. The API should just check if the resource exists already and if so update it, or otherwise create it.

Always use `PATCH` for requests that update resources partially by their id. The id must be specified in the URL.

### DELETE

Always use `DELETE` for requests that delete resources. The id must be specified in the URL.

## Path

### Predictability

The **#1 priority** in naming and structure of paths on publiq APIs is predictability, which is mostly achieved through consistency.

When deciding on the name and structure of a new path, try to keep existing and potential future paths in mind so that they make sense in a larger overview.

**✅ Example of predictable paths**

    GET /events
    GET /events/{eventId}
    GET /events/{eventId}/card-systems

**❌ Example of unpredictable paths**

    GET /events
    GET /event/{eventId}
    GET /card-systems/event/{eventId}

### Singular vs Plural

Always use plural for endpoints or parts of your path that represent collections. Only use singular for endpoints that represent a singleton.

**✅ Pluralize collections**

A collection:

    GET /events

An endpoint that returns a single resource, but is part of a higher-level collection:

    GET /events/{eventId} 

**✅ Use singular for singletons**

An endpoint that returns info about the current user (based on a token in the request):

    GET /user

An endpoint that allows an update of the audience type of an event which can only hold a single value:

    PUT /events/{eventId}/audience-type 

### Casing

*   Path names must be handled case-insensitively on the server
*   Always use lowercase in documentation of path names
*   Always use `-` to separate words in path names. Do **not** use `camelCase` for path names.

<!---->

    GET /good-example
    GET /badExample

### Path parameters

If your path has variable parameters, you must describe them using `{camelCase}` in documentation.

For example:

    GET /events/{eventId}/card-systems/{cardSystemId}

### Trailing slashes `/`

Paths on publiq APIs must never require a trailing slash, and have to be documented without trailing slash.

If a trailing slash is included in the request URL, ideally the API should ignore it and handle the request as if it did not include a trailing slash.
