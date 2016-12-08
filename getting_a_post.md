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

At our root query level we are querying for post. Within that post query we want the title and content fields. Notice how we pass an id argument to the post field. This enables WP GraphQL to fetch the post matching id 1.