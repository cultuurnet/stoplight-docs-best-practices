# Documenting HTTP examples

To document example HTTP requests or responses in Markdown files, use the [HTTP message format](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages) instead of `curl` examples.

For example for a `GET` request:

```
GET /path HTTP/1.1
Host: https://example.com
Accept: application/json
```

For example for a `POST` request:

```
POST /path HTTP/1.1
Host: https://example.com
Content-Type: application/json

{"foo":"bar"}
```

For example for a `200` response:
```
HTTP/1.1 200 OK
Content-Type: application/json

{"foo":"bar"}
```

To make the example actionable, you can include a "try it" block using the [HTTP request maker functionality](https://meta.stoplight.io/docs/studio/docs/Documentation/03a-stoplight-flavored-markdown.md#http-request-maker) provided by Stoplight.
