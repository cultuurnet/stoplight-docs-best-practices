# CORS

Because we spend a lot of time debugging CORS issues between frontends and our APIs, every API should respond with the following headers to `OPTIONS` requests:

    Access-Control-Allow-Origin: *

    Access-Control-Allow-Headers: <echo back headers in Access-Control-Request-Headers header from request>

    Allow: <echo back Access-Control-Request-Method header from request>

This way, CORS requests are allowed from every origin for every HTTP method and for every HTTP header, except for cookies and other authorization headers like basic username and password.

The `Authorization` header used to include a token in API requests is allowed with this approach.

## How to implement

At the time of writing every API should implement this logic itself. However we are looking into a solution to provide this for every API automatically so it doesn't need to be re-implemented constantly.

## Security implications

Because our APIs are not running on an intranet or using cookies, we can safely allow every possible origin in CORS requests.

The biggest reason not to allow every possible origin in CORS requests is because browsers automatically include relevant cookies for the domain that the request is made to. So if our APIs used cookies to authenticate, then a malicious website could make a request to our API in name of the unsuspecting visitor that is also logged in on our APIs, which we obviously don't want.

Another reason is that if a website is running on an intranet, you don't want to expose access to it from other websites. So if a user is connected to a VPN and they visit a malicious website, that website should not be able to make a request to the intranet website. However our APIs don't run on an intranet and are publicly accessible.
