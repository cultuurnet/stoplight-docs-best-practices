# REST

This page gives a brief overview of the REST architecture, and gives more detailed guidelines and conventions that must be followed on every one of publiq's APIs, for example how URLs must be structured.

## Introduction

Every publiq API must follow the [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) architectural style.

This architecture is more than just a styleguide, but also dictates how the API should behave in certain scenarios.

At its core, a REST API works with the concepts of resources and collections (of said resources), which must each always be identifiable by a unique URL. These resources and collections are representations of internal application state.

However, a resource or collection does not need to map directly to an entity in a database or filesystem. A resource can for example also be `the current weather in Brussels`. Additionally, two resources can point to the same data but still be semantically different. For example, `the current weather in Brussels` and `the current weather for my location` can be exactly the same if the user is in Brussels, but they are still considered to be two different resources since they can change depending on the situation.

In general, these resources and collections should always be transfered as a content-type like `application/json` or `application/xml` in request and response bodies. On publiq APIs we almost always use `application/json` and/or `application/ld+json`.

Every resource or collection should also support one or more operations, which are performed using a specific HTTP method like `GET`, `PUT`, ... Each of these HTTP methods provides specific behaviour that should be the same in any REST API. For example, `GET` should always be used for reading data and should be safe. It should not alter the application state.

In general, REST APIs should also follow the [HTTP specifications](https://developer.mozilla.org/en-US/docs/Web/HTTP/Resources_and_specifications) as closely as possible. For example, they must use a status code in the `>=400` range for [error responses](./errors.md), use the `Authorization` header for [authentication](./authentication.md), and so on.

By following the HTTP specifications as closely as possible, each API is ensured to work correctly with generic infrastructure like proxies, load balancers, and generic HTTP libraries in client apps.

## 
