# Getting a post.

Posts are the lifeblood of a WordPress blog. In standard WordPress themeing, `WP_Query` retrieves post data while The Loop is running. During The Loop your template files will be set up to display the data. The Loop has often been criticized and sometimes rightly so. To me The Loop is somewhat over complicated. It confused me when I first started using WordPress. I did not realize that the internal state was changing on every pass of the loop. Even when you are grabbing a single view like `single-post.php` The Loop will run. Let's rethink how we could design a single post view using WP GraphQL.

## The post query.

The post title and post content are arguably the two most important things to display in a single post view. Here is the WP GraphQL query for a post's title and content.

```
{
  post(id: 1) {
    title,
    content
  }
}
```

At our root query level we are querying for post. Within that post query we want the title and content fields. Notice how we pass an id argument to the post field. This enables WP GraphQL to fetch the post matching id 1. Our response might look something like this.

```
{
  data: {
    post: {
      title: "WP GraphQL seems pretty neat!",
      content: "Wow this will enable me to make some amazing experiences in WordPress."
    }
  }
}
```

## Impact of field ordering.

If we switch around the ordering of the fields in our query our response will change to match that as well. This won't have too large of an impact on your work but it is still cool nonetheless.

```
{
  post(id: 1) {
    content,
    title
  }
}
```

Now the response will match the change.

```
{
  data: {
    post: {
      content: "Wow this will enable me to make some amazing experiences in WordPress.",
      title: "WP GraphQL seems pretty neat!"
    }
  }
}
```

## Objects within objects, the true power of GraphQL

One of the most compelling reasons to use WP GraphQL is that it exposes relationships among data easily. The name GraphQL stands for Graph Query Language. A graph in computer science is a particular type of data set. A graph marks the relations of nodes by something known as an edge. A node in WordPress might be a post, user, comment, or any singular resource. Let's look at grabbing a post some of its comments and the post author's name. Let's get the comments' authors names as well.

```
{
  post(id: 2) {
    content,
    title,
    author {
      name
    },
    comments(first: 10) {
      content,
      author {
        name
      }
    }
  }
}
```

The post field has a number of fields with in itself. We are grabbing the content and title, which are just basic properties of WP\_Post.  The next fields are where things get interesting.  The author field will resolve to the user matching the post author.  We can then query for any user fields within that scope. Here we are grabbing the display name.  Comments are up next. We will grab the ten most recent comments with this query.  In our response each comment will have the corresponding content and author name.

### Why does this matter?

If you have ever written an API driven front end, you have probably experienced either not having enough data, having too much data, or having to deal with data in an awkward format.  GraphQL solves this problem.  The above query fits a single post view pretty well, but what if we wanted a view based around an author.

## Errors

If you do not supply an argument to a field that requires one, WP GraphQL will handily return an error message explaining you need it. Let's look at what happens if we try to query for a post without the required id argument.

### Bad Query

Below is a bad query because we are not specifying the required ID argument for fetching the post.

```
{
  post {
    title,
    content,
    exceprt,
    id
  }
}
```

### Error Response

```
{
  "errors": [
    {
      "message": "Field \"post\" argument \"id\" of type \"ID!\" is required but not provided.",
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ]
    }
  ]
}
```

Notice how our root node is now errors instead of data. This is handy to be able to discern errors from successful responses. In a client you can always check for whether the response is data or errors. The rest of the error response is pretty straightforward and it will even report the offending line of code used for the query.

