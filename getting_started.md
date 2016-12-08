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

The `{` starts the root level query and `}` finishes it off. Within these brackets can be sub-queries defined by the root level query. The root query exposes every capability for WP GraphQL as a field. In the above example the hello field on the root query will resolve to our hello message. The WP GraphQL endpoint will translate the resolved PHP data and encode it as JSON for our response. It should look something like this.

```
{
  data: {
    hello: "Welcome to WP GraphQL, I hope that you will enjoy this adventure!"
  }
}
```

Our response looks almost identical to our query. Unlike our query, the response is actually valid JSON! JSON is a great data format and you can use it in pretty much any programming language. The response has one root level node; data. Within the data node will be matching fields for the query. We queried for hello and we got back a hello field in our response with the matching value.

Let's move on to something more WordPress oriented. [Getting a post](getting_a_post.md) is up next.