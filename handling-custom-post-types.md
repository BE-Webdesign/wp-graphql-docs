# Handling custom post types.

Custom post types hold a special place in WordPress development.  They are often used to define all sorts of data types within WordPress.  To register your custom post types with WP GraphQL follow along with the example below.

```
/**
 * Register a book post type.
 */
function my_prefix_register_book() {
    $args = array(
        'public'                => true,
        'label'                 => __( 'Books', 'textdomain' ),
        'show_in_graphql'       => true,
        'graphql_name'          => 'book',
        'graphql_plural_name'   => 'books',
        'graphql_singular_type' => 'Book',
        'graphql_plural_type'   => 'Books',
    );

    register_post_type( 'book', $args );
}

add_action( 'init', 'my_prefix_register_book' );
```

Each WP GraphQL parameter is an internal non user facing name, do not use translation strings here as they are not appropriate.

## Show in graphql.

\`show\_in\_graphql\` is a pretty straightforward addition.  If you want this post type to be present in the API simply set it to \`show\_in\_graphql\` true.  Any value other than a boolean true will hide the post type from the API.

## GraphQL name.

\`graphql\_name\` is important.  This is the field that will become the singular field in the root level query.  What does that mean? In our example above we registered book.  If we make a query with WP GraphQL we can now do \`{ book\(id: 7\){ title } }\`.  This will retrieve the title for the custom book post with an id of 7.

## GraphQL plural name.

\`graphql\_plural\_name\` is similar to the above parameter.  It will add the plural field to the to level query.  Using the above example when we query for \`{ books\(first: 10\) { title } }\`, we will get back the first ten books and their titles.  Why is this important? Well posts are kind of crazy in WordPress and you need to query by \`post\_type\` to get the actual type you want since all of them are stored in the same database table.  By registering the plural name you are telling WP GraphQL what the top level query field name should be if we set \`graphql\_plural\_name\` to \`tacos\` then we would query for book post types by this query \`{ tacos\(first: 10\) { title } }\`.

## GraphQL singular type.

## GraphQL plural type.





