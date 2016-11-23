# Reference
This reference serves as a way to view the current capabilities of GraphQL and explore it's type system.  **The reference may be out of date and it is advised to go by the auto documentation provided by GraphiQL**

## Interpreting GraphQL Introspection
The following capabilities are listed using syntax related to GraphQL. Queries and fields are typically represented by camel cased strings. To follow WordPress coding standards queries and fields here are following snake casing. Types are capitalized like: MenuLocation. 

## WP GraphQL Capabilities

* post(id: ID!): Post
* posts(first: Int after: Int): [Post]
* user(id: ID!): User
* users(first: Int after: Int): [User]
* comment(id: ID!): Comment
* comments(first: Int after: Int): [Comment]
* term(id: ID!): Term
* terms(first: Int after: Int): [Term]
* taxonomy(name: String!): Taxonomy
* taxonomies(first: Int after: Int): [Taxonomy]
* menu_item(id: ID!): MenuItem
* menu(id: ID name: String slug: String): Menu
* menu_location(slug: String!): MenuLocation
* menu_locations: [MenuLocation]
* theme(slug: String!): Theme
* themes(first: Int after: Int): [Theme]
* plugin(slug: String!): Plugin
* plugins(first: Int after: Int): [Plugin]
* hello: String

### post(id: ID!): Post
Arguments: id: ID!


















