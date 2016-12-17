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
    
    }
  }
}
```





