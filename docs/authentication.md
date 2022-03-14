# Authentication

APIs should use the authentication methods described in the public [Authentication docs](https://publiq.stoplight.io/docs/authentication).

## Client identification guidelines

When using client identification, APIs should support both the `x-client-id` header and `clientId` URL query parameter. If both are provided, preference should be given to the header.

The client id should be validated by [fetching the client from the Auth0 management API](https://auth0.com/docs/api/management/v2#!/Clients/get_clients_by_id).

You should also validate that the client has a metadata property indicating that it has access to your API.

For example a client can have the following metadata:

    {
      "client_id": "AaiyAPdpYdesoKnqjj8HJqRn4T5titww",
      ...
      "client_metadata": {
        "publiq-apis": "ups sapi entry"
        ...
      }
    }

The above example indicates that the client has access to UiTdatabank's Search API, the UiTPAS API, and UiTdatabank's Entry API.

> We use very short names for the APIs in the client metadata, because the `publiq-apis` property is limited to 255 characters. We also cannot use multiple properties because the metadata is limited to 10 properties.

## Token guidelines

When using tokens, endpoints should support both client and user access tokens wherever possible.

Examples of acceptable exceptions include endpoints like `/user` that provide info on the current user, based on a user access token.

To validate a token, check that:

*   The signature can be verified with the public key of our Auth0 tenant
*   The `nbf` claim is in the past
*   The `exp` claim is **not** in the past
*   The `aud` claim is equal to `https://api.publiq.be`
*   The `iss` claim is equal to either (depending on what environment your API is running on):
    *   `https://account.uitid.be/`
    *   `https://account-test.uitid.be/`
    *   `https://account-acc.uitid.be/`
*   The `https://publiq.be/publiq-apis` claim is present and contains a value representing your api

If the token has an invalid signature, is not usable yet, is expired, or has an invalid `aud` or `iss` claim you should return a [401 error (see authentication docs)](https://publiq.stoplight.io/docs/authentication/docs/errors.md#unauthorized)

If the token is not usable on your API, you should return a [403 error (see authentication docs)](https://publiq.stoplight.io/docs/authentication/docs/errors.md#forbidden). (The difference with the other checks being that the token is valid on *some* of our APIs, but forbidden on your specific API.)

The value of the `https://publiq.be/publiq-apis` claim is the same as the one in the client metadata of the client that requested the token. For example:

    {
      "sub": "auth0|...",
      "aud": "https://api.publiq.be",
      ...
      "https://publiq.be/publiq-apis": "ups sapi"
    }

The example above indicates that the token is usable on the UiTPAS API and UiTdatabank's Search API. Note that the claim can be missing, in which case it is considered to be empty.

## Permissions

User/client permissions to perform actions inside your API should be managed inside the API itself.

If the specific client or user cannot perform a requested action, you should return a [403 error (see authentication docs)](https://publiq.stoplight.io/docs/authentication/docs/errors.md#forbidden).

## Scopes

<!-- theme: warning -->

> Generally, scopes should not be used for determining access to or permissions on a publiq API. This section describes the only valid use case we see for scopes. If you intend to use scopes for something else, consider another solution.

Scopes should only ever be used for granting access to resources on an API if those resources belong to a specific user and that user should determine if a client can access them or not.

The reason for this is that end-users will see a list of permissions that they are granting the client the first time after they login on Auth0 with that specific (3rd party) client. So using scopes for granting access or permissions effectively moves the decision of granting a client access from publiq to the end-users.

![An example screenshot of the screen that the user will see after logging in for the first time through a client that requests scopes.](https://images.ctfassets.net/cdy7uua7fh8z/1te4FYRbu0aFcdohdXY2Rv/116bed5515eb2114c39374fb0a258912/consent-screen.png)

If you want to give this decision making to the end-users of your API, you can use scopes but should **also** still implement the API access checks described in the sections above so 3rd party clients can go through an approval process. This way we still maintain control over what 3rd party clients can access which APIs, while end users can gain some additional control over what information a client can access in their situation.

Suitable (fictional) examples of scopes could be:

*   Reading a user's events (`events:read`)
*   Updating a user's events (`events:update`)
*   Deleting a user's events (`events:delete`)
*   Reading a user's recommendations (`recommendations:read`)
*   Reading a user's likes (`likes:read`)
*   Updating a user's likes (`likes:update`)
*   Reading a user's newsletter subscriptions (`newsletters:read`)
*   Updating a user's newsletter subscriptions (`newsletters:update`)

> At the time of writing, no publiq APIs actually use scopes yet for this purpose. Only consider using scopes if granular access to a user's resources is required, *and* the user needs to be able to grant them themself.

<!-- theme: danger -->

> Do not use scopes for determining API access as we did in the past. While this was [suggested by Auth0](https://community.auth0.com/t/access-tokens-with-multiple-audiences/9911), this approach is not suited for our APIs because we want to control which client has access to which API ourselves. This decision should not be made by our end-users.
