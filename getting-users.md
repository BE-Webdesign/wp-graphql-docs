# Getting users.

Currently WP GraphQL does not feature any security measures so listing users requires no authentication. **DO NOT SET UP WP GRAPHQL ON A PRODUCTION WEBSITE!** Sometimes it is necessary to query for multiple users at once.  Let's look at how to achieve this in WP GraphQL.

## Querying for users in WP GraphQL.

```
{
  users(first: 10) {
    name
  }
}
```

This query will return a response like this:

```
{
  "data": {
    "users": [
      {
        "name": "Carl",
      },
      {
        "name": "Sally",
      },
      {
        "name": "Masako",
      },
      {
        "name": "Ahmed",
      },
      {
        "name": "Tom",
      },
      {
        "name": "Aadhya",
      },
      {
        "name": "Jim",
      },
      {
        "name": "Jessica",
      },
      {
        "name": "Xizhou",
      },
      {
        "name": "Carl",
      },
    ]
  }
}
```

## Nifty ideas.

A lot of more interesting querying becomes possible with GraphQL in place.

```
{
  users(first: 10, roles: ["author"]) {
    name,
    post(first: 1) {
      title,
      exceprt
    },
    avatar(size:192) {
      url,
      width,
      height
    }
  }
}
```

This query will grab the first ten authors and expose their name, their most recent post's title and excerpt, and their avatar.  This could make an interesting author centric view.  Instead of having the blog roll be post based it could centered around the people who actually wrote the post, and their most recent posts.

