# Getting a taxonomy.

Taxonomies are classifications of groups. Terms are assigned to taxonomies. More about taxonomies coming soon.

## Querying for a taxonomy.

```
{
  taxonomy(name: "BBQ") {
    name,
    slug,
    description,
  }
}
```

And the response might look like this.

```
{
  "data": {
    "taxonomy": {
      "name": "BBQ",
      "slug": "bbq",
      "description": "Barbecue, is an artform."
    }
  }
}
```

More to come on taxonomies.

