# Paths

This page explains how paths on publiq APIs should be named and structured.

## Trailing slashes

Paths on publiq APIs should never require a trailing slash, and should be documented without trailing slash.

If a trailing slash is included in the request URL, ideally the API should ignore it and handle the request as if it did not include a trailing slash.
