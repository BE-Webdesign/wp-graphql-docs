# Welcome to WP GraphQL.
WP GraphQL is a plugin that enables a GraphQL API for your WordPress install. **It is not currently ready for production. Please do not enable this plugin where security is critical.** Once the plugin is brought into beta testing, it will most likely be secure-ish.

## What is GraphQL
GraphQL is a technical specification, developed by Facebook, for an application level query language. What does that mean? Basically GraphQL provides a consistent way to make declarative queries, which will enable you to more easily retrieve the data you want and the shape that you want it in. GraphQL can be implemented in any language and can cover a vast amount of use cases. WP GraphQL exposes a WordPress installation's data through a GraphQL endpoint. You can send a GraphQL query over HTTP and as a response you will get the matching JSON representation of your data.

## Why use GraphQL?
There are a number of reasons why you would want to use GraphQL, but one stands out among the rest; querying. GraphQL's queries are where it's power lies. A query string in GraphQL looks similar to JavaScript. Let's say we want to get all of the data for a single page view from WordPress. There is actually a lot of data that needs to be retrieved all of which interconnect with each other as well. Here is an example GraphQL query.

```
{
  menu_location(slug: "primary") {
    active_menu {
      items {
        url,
        title
      }
    }
  },
  post(id: 1) {
    title,
    content,
    date,
    featured_img(size: "thumbnail") {
      src
      alt
    }
    author {
      name,
      description,
      gravatar(size: 96) {
        src
        alt
      }
    },
    comments {
      content,
      date,
      author {
        name,
        gravatar(size: 48) {
          src
        }
      }
    }
  }
}
```

Here you can see the power of GraphQL querying. We declare what we want in the query and the response from the API will return the matching data. The query uses only one HTTP request. The query dictates the shape of our data, not the response. Notice how we also specify each field we want in the query and how each field can also be another type of data. This allows us to retrieve the data we need, whereas other types of APIs do not provide this flexibility. This makes GraphQL uniquely suited for any application that has a user interface.

## Why use GraphQL with WordPress
WordPress is an incredible tool for a huge variety of use cases. WordPress 4.7 ushered in a shiny new REST API, so why should we consider using WP GraphQL? GraphQL enables you to have the power over your responses and fetch the data you want. There is only one endpoint; `mysite.com/graphql`. The simplicity of GraphQL is what makes it so appealing. GraphQL is designed to easily expose the relations of your data. To replicate these types of complicated queries via SQL, the WP REST API, admin-ajax, or any other API in WordPress, you will end up writing a lot of complex code. With GraphQL, you create your query string and the GraphQL endpoint will handle the complex joins and relations of your data.

## Contributors and Sources
WP GraphQL piggybacks on top of WebOnyx's GraphQL PHP implementation, which borrows from Facebook's reference implementation in JavaScript. Please head to the [wp-graphql github repo](https://github.com/BE-Webdesign/wp-graphql) to help contribute.

## Support or Contact
Check out the [WP GraphQL](https://github.com/BE-Webdesign/wp-graphql/issues) repository. [Issue 23](https://github.com/BE-Webdesign/wp-graphql/issues/23) is open for you to introduce yourself.