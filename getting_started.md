# Getting started.

The key to understanding how to use WP GraphQL lies in understanding GraphQL query syntax. It looks alot like JSON and JavaScript but is neither. Here is the most basic type of GraphQL query supported in WP GraphQL.

```
{
  hello
}
```

You can also remove the whitespace.

```
{hello}
```

The `{` starts the root level query and `}` finishes it off. Within these brackets can be sub-queries defined by the root level query. The root query exposes every capability for WP GraphQL.