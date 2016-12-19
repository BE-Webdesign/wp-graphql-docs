# Getting taxonomies.

Taxonomies are classifications of groups. Terms are assigned to taxonomies. More about taxonomies coming soon.

## Querying for taxonomies.

```
{
  taxonomies(first: 10) {
    name,
    slug
  }
}
```

And the response might look like this.

```
{
  "data": {
    "taxonomies": [
      {
        "name": "Categories",
        "slug": "category",
      },
      {
        "name": "Tags",
        "slug": "post_tag",
      },
    ]
  }
}
```

More to come on taxonomies.

