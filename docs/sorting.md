# Sorting

## Multiple fields

Endpoints that support sorting based on multiple field names and order should use a `sort` query parameter with the following syntax:

    ?sort[field_name_1]=desc&sort[field_name_2]=asc

In the example above, the results would first be sorted by `field_name_1` in a `desc` order, and then by `field_name_2` in an `asc` order.

## Single field

Endpoints that only support sorting by a single field can also use the following simplified syntax:

    ?sort=field_name&order=asc

<!-- theme: danger -->

> ##### TODO: Finalize syntax
>
> The single-field sorting syntax has not been finalized yet!

<!-- theme: warning -->

> ##### Migrating from single-field sorting syntax to multi-field sorting syntax
>
> If your endpoint starts with single-field sorting syntax and later needs to add support for multi-field sorting syntax, make sure that you keep supporting the single-field sorting syntax as well for backward compatibility!

## Case sensitivity

The orders `asc` and `desc` should be handled case insensitively. So both `asc` or `ASC` should be accepted.
