# Contributing

## Roadmap

A loose plan in an order that I think makes sense: feel free to chime in with
your thoughts! I am probably missing some important items as well.

1. ~~Get basic WordPress data types supported.~~
2. Add descriptions for type system. Clean up type system code.
2. Improve the infrastructure around serving requests.
3. Implement Authentication for WP GraphQL. Basic Auth at first, so
proper authorization can be built out for the project and security will be in a
decent starting place.
4. Make Relay compliant collection types.
5. Add hooks and filters for extending.
5. Start backporting the library and plugin to PHP 5.2 if necessary ( maybe WordPress will have version bumped! ).
6. Do a thorough audit and see if it is ready for the WordPress.org plugin repository.

Things that will happen at all points in project:

Improve TypeSystem/Schema, Improve Documentation, Improve Test Suite. For every
improvement/change we will want test coverage and documentation coverage. By
bonding documentation to testing to the actual changes being made we can create
a very clean final product.

### Documentation

Inline documentation is great. Please use it when tricky things are going on in the code that someone may be unfamiliar with. Inline documentation to describe the intent of the code and document any decisions.

For project level documentation, use the [WP GraphQL Docs repository](https://github.com/BE-Webdesign/wp-graphql-docs).

### Test Coverage

We use [PHPUnit](https://phpunit.de/index.html) for our unit testing. PHPUnit will be installed when you run
composer. The tests are located in the `tests` directory of this plugin. To run
the test suite, find the wp-graphql directory via your command line and type in

```
phpunit
```

The test runner will start and display output in your command line. If anything failed you will get a nice error report to help understand what went wrong. If you are using VVV, phpunit will already be
installed. To run the suite against multisite type in the following.

```
phpunit -c multisite.xml
```

This will load the configuration file for a multisite test suite.

#### Continuous Integration

The Github Repo handles continuous integration via TravisCI. When you make a pull Request against WP GraphQL the test suite will automatically run against the new commit. This process helps maintain compatibility between particular versions of WordPress, PHP, and WP GraphQL. To make amendments to the TravisCI build process, you need to edit the `travis.yml` file.

## Code of Conduct

Be kind, polite, and respectful of others. Have fun!

### Introduce yourself!

[Post a comment here and introduce yourself!](https://github.com/BE-Webdesign/wp-graphql/issues/23)