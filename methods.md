# Reference
This reference serves as a way to view the current capabilities of GraphQL and explore it's type system.  **The reference may be out of date and it is advised to go by the auto documentation provided by GraphiQL**

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
* taxonomies(first: Intafter: Int): [Taxonomy]
* menu_item(id: ID!): MenuItem
* menu(id: IDname: Stringslug: String): Menu
* menu_location(slug: String!): MenuLocation
* menu_locations: [MenuLocation]
* theme(slug: String!): Theme
* themes(first: Intafter: Int): [Theme]
* plugin(slug: String!): Plugin
* plugins(first: Intafter: Int): [Plugin]
* hello: String




















