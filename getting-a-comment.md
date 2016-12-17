# Getting a comment.

Comments in WordPress are typically used for user to user interactions.  Comments are a really exciting part of WordPress and have many use cases.  Let's look at some basic comment examples.

## Querying for a comment.

```
{
  comment(id: 1) {
    content,
    date,
    author {
      name,
      avatar(size: 96) {
        url
      }
    }
    post {
      title
    }
  }
}
```

This will fetch a single comment, its content, posted date, and the author's name and avatar, along with the post title the comment was posted on.

On it's surface querying by a comment seems pretty trivial but when the full scope of GraphQL is brought into light, a single comment could bring you to entire networks of data through edges.

