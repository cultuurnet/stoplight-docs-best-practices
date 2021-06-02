# Authentication

APIs should use the authentication methods described in the public [Authentication docs](https://publiq.stoplight.io/docs/authentication).

## Client identification guidelines

When using client identification, APIs should support both the `x-client-id` header and `clientId` URL query parameter. If both are provided, preference should be given to the header.

## Token guidelines

When using tokens, endpoints should support both client and user access tokens wherever possible.

Examples of acceptable exceptions include endpoints like `/user` that provide info on the current user, based on a user access token.
