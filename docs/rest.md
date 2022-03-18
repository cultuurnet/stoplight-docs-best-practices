# REST

Every publiq API must follow the [Representational State Transfer (REST)](https://en.wikipedia.org/wiki/Representational_state_transfer) architectural style.

This architecture is more than just a styleguide. It also dictates how the API should behave in certain scenarios.

The term REST was introduced by Roy Fielding [in his doctoral dissertation](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm) in 2000.

This page includes a brief summary of the most important points of the REST architecture, as well as some conventions that must be followed in REST APIs built by/for publiq.

## HTTP

REST APIs that work over HTTP must follow the [HTTP specifications](https://developer.mozilla.org/en-US/docs/Web/HTTP/Resources_and_specifications) as closely as possible.

This way each API is ensured to work correctly with generic infrastructure like proxies, load balancers, and generic HTTP libraries in client apps.

For example, they must provide unique URLs for resources, use status codes in the `>=400` range for [error responses](./errors.md), use the `Authorization` header for [authentication](./authentication.md), follow the standardized behaviour for each HTTP method, and so on.

When in doubt and something is not covered by this page, always follow the HTTP specifcations as closely as possible.

## Resources

At its core, REST work with the concept of **resources**.

A resource is a representation of internal application state. It can be data that is stored in for example a database or filesystem, but it does not necessarily have to directly map to this data. It can also be a combination, calculation, or other representation of this data. **The underlying storage mechanism must not dictate the representation of the resources.**

An example of a resource can for example be `the current weather in Brussels`, while your database may store the weather information with a specific datetime.

A resource must always be **identifiable by a unique [Uniform Resource Identifier (URI)](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier)**. In practice, resources on REST APIs are almost always identified by **[Uniform Resource Locators (URLs)](https://en.wikipedia.org/wiki/URL)** which are a type of URI.

The example above could for example have the URI `https://api.ecma.org/weather-predictions/brussels/current`, which is a URL that also acts as a locator that conveys where the resource can be accessed.

Additionally, two resources can point to the same data but still be different identifiable resources that exist separately.

For example, the data for the resource `the current weather for my location`, which can have a URI like `https://api.ecma.org/weather-predictions/my-location/current`, can be exactly the same as the data for Brussels if the user is currently in Brussels. But they are still considered to be two different resources since they can change depending on the situation.

## Collections

Collections are a special type of resource, that contain multiple other resources of the same type. For example the collection `users` contains all `user` resources.

Like other resources, collections must have a unique URI.

For example a URI for the `users` collection could be `https://api.ecma.org/users`, while the URI for a specific user could be `https://api.ecma.org/users/iuwehgiwuig`.

## Naming conventions for URIs

The following conventions apply to URIs in APIs built by/for publiq.

*   URIs must always use `kebab-case`. ([Read why](https://stackoverflow.com/a/18450653/1317044))
*   Collections must be pluralized. For example `/weather-predictions`, `/users`, ...
*   Collections may support query parameters to filter them. For example `/users?postalCode=1000` could be the URI for all users that live in Brussels.
*   Individual resources may use a database ID as part of their URI, but do not need to. If they do, it is advised to not use incremental IDs to avoid "URI guessing", but to use [UUIDs](https://nl.wikipedia.org/wiki/Universally_unique_identifier) instead. For example `/users/foo` for the user with username `foo`, or `/users/550e8400-e29b-41d4-a716-446655440000` for the user with the database ID `550e8400-e29b-41d4-a716-446655440000`.
*   Individual resources inside a collection must be prefixed with that collection's URI, as seen in the examples above.
*   Individual resources may be a singular if only one instance exists. For example `/user` for the current user, or `/cities/brussels/weather` for the weather in Brussels.
*   Individual resources may support or even require query parameters as part of their URI. For example `/points?uitpasNumber=1234567890123` could be the URI to get the points for the UiTPAS with number `1234567890123`. However, preference is given to a structure like `/uitpasNumbers/1234567890123/points` instead when possible.

Note that query parameters, if used, are always part of the identifier of a resource. **Query parameters must not be used to transfer new/updated data!**

## Methods

Every resource must support one or more HTTP methods, which indicate the action that should be performed on the resource.

While the HTTP specifications allows for custom methods, publiq APIs must never use custom methods to ensure compatibility with generic HTTP tooling.

APIs built by/for publiq must always use the following methods, and respect their documented behaviour.

**POST**

**GET**

**PUT**

**PATCH**

**DELETE**

## Content-types

## Error codes

## Design principles

### Stateless

### Loose coupling
