# Working with menus.

We won't cover each type of menu related thing in WP GraphQL. Instead, we will cover the three at once to show how menus can be queried for in WP GraphQL.  The three types relating to menus are \`MenuLocation\`, \`Menu\`, \`MenuItem\`.  Let's breakdown what each of these is.

## MenuLocation

\`MenuLocation\` is a type that will resolve to the registered navigation menu.  Navigation menus in WordPress are typically registered by the active theme and can be set up by using \`register\_nav\_menu\(\)\`.  Let's quickly look at how to query for a registered navigation menu location.

```
{
  menu_location(slug: "top") {
    name
  }
}
```

We will get back:

```
{
  "data": {
    "menu_location": {
      "name": "Top Menu"
    }
  }
}
```

This is not super useful let's look at the next type.

## Menu

A menu in WordPress can be created and exist without being assigned to a menu location.  This allows you to store menus and swap them in and out.  You could possibly do A/B testing etc. by using different menus.  In WordPress world, a menu is an object term under the \`nav\_menu\` taxonomy.

