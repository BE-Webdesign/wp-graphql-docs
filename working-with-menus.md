## Working with menus.

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

A menu in WordPress can be created and exist without being assigned to a menu location.  This allows you to store menus and swap them in and out.  You could possibly do A/B testing etc. by using different menus.  In WordPress world, a menu is an object term under the \`nav\_menu\` taxonomy.  A menu is really a special kind of group that menu items are placed into.  The following is an example query.

```
{
  menu(id: 17) {
    slug,
    name
  }
}
```

This will return the slug for the menu, and the name of it.  Menu's themselves aren't terribly useful without finding the associated menu items.  Let's look at menu items next.

## MenuItem

If you have ever clicked on a link in a WordPress navigation menu then you have used a menu item. Menu items in WordPress are actually just a custom post type.  The special information is stored in the post meta tables.  Let's look at how to query for a menu item.

```
{
  menu_item(id: 22) {
    title,
    type,
    object_id,
    object,
    target,
    xfn,
    url
  }
}
```

This will query for all of the fields on a menu item.  A major improvement for menu items in WP GraphQL would include the \`object\` & \`object\_id\` fields as an edge pointing to the actual resource.  Due to the very diverse possibilities it would be difficult to implement this in WP GraphQL, at some point this should exist though.  Querying for menu items in isolation isn't very useful.  Let's do something useful.

## Putting it all together.

What if we wanted to get all the information we need to create a view for the "Top Menu"?  Let's look at what the query would look life.

```
{
  menu_location(slug: "top") {
    name
    active_menu {
      items {
        title,
        type,
        object_id,
        object,
        target,
        xfn,
        url
      }
    }
  }
}
```

The response might look something like this.

```
{
  "data": {
    "menu_location": {
      "name": "Top Menu",
      "active_menu": {
        "items": [
          {
            "title": "Yolo",
            "type": "custom",
            "object_id": "4",
            "object": "custom",
            "target": "",
            "xfn": "",
            "url": "http://local.graphql.dev/"
          },
          {
            "title": "Sample Page",
            "type": "post_type",
            "object_id": "2",
            "object": "page",
            "target": "",
            "xfn": "",
            "url": "http://local.graphql.dev/sample-page/"
          }
        ]
      }
    }
  }
}
```

The \`active\_menu\` field resolves to the assigned \`Menu\` type and the items field within that resolves to a collection of \`MenuItem\` types.  This enables us to get complete menu data.  What if we wanted to get menu data for every registered menu?

```
{
  menu_locations {
    name
    active_menu {
      items {
        title,
        type,
        object_id,
        object,
        target,
        xfn,
        url
      }
    }
  }
}
```

Yup, it really is that simple. This query will retrieve each registered menu's name, and active menu's items. If the active menu has no items, the \`items\` field will resolve to \`null\` and if the registered menu does not have an active menu that field will resolve to \`null\`.  This inherent \`null\` in GraphQL is very useful.  You may be asking, "how do I get nested menu items", at this current time, WP GraphQL does not support those kind of queries.

