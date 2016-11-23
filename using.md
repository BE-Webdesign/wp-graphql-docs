# Using WP GraphQL

You can send GraphQL requests like you would any old AJAX requests but there is
an incredibly awesome tool GraphiQL that has been created by Facebook. If you
want to play around in GraphQL there is no better way at the moment. GraphiQL
comes highly recommended!

## GraphiQL
To use GraphiQL for PHP install this [chrome extension; ChromieQL](https://chrome.google.com/webstore/detail/chromeiql/fkkiamalmpiidkljmicmjfbieiclmeij)

You will want to set the endpoint area to `http://local.mywordpress.dev/graphql`.
Basically whatever url you are using for your WordPress install and `/graphql`.

All this is really doing is sending the GraphQL query string as a HTTP request
data which is then parsed by this plugin and executed by the GraphQL plugin.

## JavaScript Fetch API
To use WP GraphQL in a JavaScript app you can use the Fetch API or good old XMLHTTPRequest. Here is a basic example using the Fetch API. (The example below is put in es5, for the sake of compatability, but it looks even better in es6!) The example below is very rough, and is only intended as a working demonstration:

```js
// Our endpoint change the address to match your domain.
graphqlEndpoint = "http://local.graphql.dev/graphql";

// This query fetches the title, content, and author name of post number 1.
query = "{
  post(id: 1) {
    title,
    content,
    author {
      name
    }
  }
}";

// Strip out whitespace and set query param.
queryString = "?query=" + query.replace(/\s+/g, '');

// Combine the endpoint with the query string.
someUrl = graphqlEndpoint + queryString;

// Fetch the url.
fetch(someUrl)
    // When the promise resolves return the response as parsed json.
    .then( function( response ) {
        return response.json();
    })
    .then( function( response ) {
        // Log the data in the console and return it.
        console.log( 'WooooWEEE that's some nice GraphQL', response.data );
        return response.data;
    });
```