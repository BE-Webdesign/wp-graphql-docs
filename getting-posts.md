# Getting posts.

What would WordPress be without post collections? Posts are pretty fundamental to the conventional uses of WordPress or any CMS.  In WordPress, posts are the main content, they are the driving force behind a blog/website. When you are reading an article or see a list of them, you are interacting with them.  In some cases posts are taken beyond their intended use with custom post types.  Custom post types in WordPress, are meant to be custom types of well -- a post, page, things that match up with the format/schema of a post.  Often times, post types that don't fully fit the mold of a post and would be better off stored in custom database tables.  That is neither here nor there but is worth understanding in WordPress, because posts seem to take on this huge central focus in development.

## Querying for posts.

Here is an example query for posts in WP GraphQL.

```
{
  posts(first: 3) {
    title,
    content,
    author {
      name,
      avatar(size: 96) {
        url,
        width,
        height
      }
    }
  }
}
```

And the result will look something like this:

```
{
  "data": {
    "posts": [
      {
        "title": "Just a post",
        "content": "Just some content",
        "author": {
          "name": "Alice",
          "avatar": {
            "url": "http://0.gravatar.com/avatar/923ce2eabca923f9a8e4da2a31997715?s=96&d=mm&r=g"
          }
        }
      },
      {
        "title": "Just another post",
        "content": "Hopefully there are no men in the middle.",
        "author": {
          "name": "Bob",
          "avatar": {
            "url": "http://0.gravatar.com/avatar/923ce2eabca923f9a8e4da2a31997715?s=96&d=mm&r=g"
          }
        }
      }
    ]
  }
}
```

Pretty cool. Notice how only two posts were returned even though we asked for the first three posts. This is because there are only two posts on this WordPress installation. If you fetch more posts than exist you will simply get as many as you can. This also brings up an important concept _Pagination_.

## Pagination.

Pagination is an important part to any application because it is a gigantic scalability, performance concern.  What if we try to get 1,000,000 posts at once, your database is probably not going to like that, but what if 100 users at the same time wanted that same query, uh oh.  Pagination helps us break things down into smaller parts, in WP GraphQL there are currently two pagination parameters, first and after.

### First.

First is very similar to a \`per\_page\` value or a \`LIMIT\` query in SQL, 

### After.



