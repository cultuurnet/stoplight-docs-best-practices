# Sorting

<!-- theme: danger -->

> This guideline is still a work in progress and the syntax is not finalized yet!

## Syntax

Endpoints that support sorting of multiple results based on field name(s) and order should use a `sort` query parameter with the following syntax:

```
?sort=field_name_1,desc,field_name_2,asc
```

In the example above, the results would first be sorted by `field_name_1` in a `desc` order, and then by `field_name_2` in an `asc` order.

## Case sensitivity

> The orders `asc` and `desc` MUST be case insensitive. So both `asc` or `ASC` should be accepted.

## Existing APIs

<!-- theme: danger -->

> This syntax was explicitly chosen to deviate from the `sort` syntax used in existing APIs like SAPI3, because that sort proved to be too hard to document in Open API docs and is also hard to implement in languages other than PHP.

Existing APIs that want to also provide support for this official sort syntax can also keep supporting their old sort syntax for backward compatibility.