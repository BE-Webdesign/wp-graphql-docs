# Using WP GraphQL

You can send GraphQL requests like you would any old AJAX requests but there is
an incredibly awesome tool GraphiQL that has been created by Facebook. If you
want to play around in GraphQL there is no better way at the moment. GraphiQL
comes highly recommended!

## Make sure WP GraphQL is running

Before diving in deeper, make sure that the WP GraphQL endpoint is running properly. The WP GraphQL endpoint will be located at your WordPress's base url followed by `/graphql`. If your site is running at `http://wow.graphql-isawesome.com/` then the WP GraphQL endpoint will live here: `http://wow.graphql-isawesome.com/graphql`. If everything is running propery you will be greeted by a friendly welcoming message:

```js
{
  data: {
    hello: "Welcome to WP GraphQL, I hope that you will enjoy this adventure!"
  }
}
```

If you do not see the message make sure the WP GraphQL plugin is activated for your WordPress install.
It is also possible that other plugins are conflicting with WP GraphQL. If you use plugins that modify WP Rewrite rules heavily it may be possible that it will somehow break WP GraphQL. In most cases as long as the WP GraphQL plugin is activated and you are running WordPress 4.7+ and PHP 5.4+, then WP GraphQL will work as intended.

## GraphiQL
GraphiQL is a tool that makes working with GraphQL incredibly easy. It features the ability to write queries, see the response and to view the schema backing GraphQL. To use GraphiQL in the browser install this [chrome extension; ChromieQL](https://chrome.google.com/webstore/detail/chromeiql/fkkiamalmpiidkljmicmjfbieiclmeij). Once ChromieQL is installed.

You will want to set the endpoint area to `http://local.mywordpress.dev/graphql`. 

All this is really doing is sending the GraphQL query string as HTTP request data which is then parsed and executed by the WP GraphQL plugin.

## JavaScript Fetch API
To use WP GraphQL in a JavaScript app you can use the Fetch API or good old XMLHTTPRequest. Here is a basic example using the Fetch API. (The example below is put in es5, for the sake of compatibility, but it looks even better in es6!) The example below is very rough, and is only intended as a working demonstration:

```js
// Our endpoint change the address to match your domain.
var graphqlEndpoint = "http://local.graphql.dev/graphql";

// This query fetches the title, content, and author name of post number 1. It is equivalent to below:
/*
{
  post(id: 1) {
    title,
    content,
    author {
      name
    }
  }
}
*/
var query = "{post(id:1){title,content,author{name}}}";

// Build query string.
var queryString = "?query=" + query;

// Combine the endpoint with the query string.
var someUrl = graphqlEndpoint + queryString;

// Fetch the url.
fetch(someUrl)
    // When the promise resolves return the response as parsed json.
    .then( function( response ) {
        return response.json();
    })
    .then( function( response ) {
        // Log the data in the console and return it.
        console.log( "WooooWEEE that's some nice GraphQL", response.data );
        return response.data;
    });
```

### Future Client Library
When the server side portion of GraphQL is more developed and features proper authentication, security measures, and better infrastructure, a JavaScript client library will be developed to make it quick and easy to use WP GraphQL client side in JavaScript. Alternatively, Relay can be used once WP GraphQL is Relay compliant.