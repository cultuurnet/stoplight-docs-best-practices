# Authentication

APIs should use the authentication methods described in the public [Authentication docs](https://publiq.stoplight.io/docs/authentication).

## Client identification guidelines

When using client identification, APIs should support both the `x-client-id` header and `clientId` URL query parameter. If both are provided, preference should be given to the header.

## Token guidelines

When using tokens, endpoints should support both client and user access tokens wherever possible.

Examples of acceptable exceptions include endpoints like `/user` that provide info on the current user, based on a user access token.

## Scopes

To determine if a client has permission to use a specific API, the API should validate the [scopes](https://publiq.stoplight.io/docs/authentication/docs/scopes.md) of the client.

For example to access the UiTPAS API, the `https://api.publiq.be/auth/uitpas` scope is required.

When using client identification, the [client needs to be looked up on Auth0](https://auth0.com/docs/api/management/v2#!/Clients/get_clients_by_id) through the management API to check its scopes.

When using tokens, the required scope should be included in the token claims. For client access tokens, this is the `permissions` claim. For user access tokens this is the `scope` claim.

To check other permissions aside from accessing an API in general, see [Permissions](./permissions.md).
