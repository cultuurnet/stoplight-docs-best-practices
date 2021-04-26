# Documenting HTTP examples

To document example HTTP requests or responses in Markdown files, use the [HTTP message format](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages) instead of `curl` examples.

Additionally, make sure to indicate that your codeblock is a HTTP message by putting `http` after the backticks!

#### GET example

```
```http
GET /path HTTP/1.1
Host: https://example.com
Accept: application/json
\```
```

(Without `\` at the end)

Becomes 👇

```http
GET /path HTTP/1.1
Host: https://example.com
Accept: application/json
```

#### POST example

```
```http
POST /path HTTP/1.1
Host: https://example.com
Content-Type: application/json

{"foo":"bar"}
\```
```

(Without `\` at the end)

Becomes 👇

```http
POST /path HTTP/1.1
Host: https://example.com
Content-Type: application/json

{"foo":"bar"}
```

#### Response example

```
```http
HTTP/1.1 200 OK
Content-Type: application/json

{"foo":"bar"}
\```
```

(Without `\` at the end)

Becomes 👇

```http
HTTP/1.1 200 OK
Content-Type: application/json

{"foo":"bar"}
```

To make the example actionable, you can include a "try it" block using the [HTTP request maker functionality](https://meta.stoplight.io/docs/studio/docs/Documentation/03a-stoplight-flavored-markdown.md#http-request-maker) provided by Stoplight.
