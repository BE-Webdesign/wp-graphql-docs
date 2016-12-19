# Getting a term.

Terms are used to group various entities in WordPress, typically posts. Terms are members of a taxonomy. Post tags and categories are arguably the most common taxonomies in WordPress.  If you were to create a category, you are creating a term. If you create a tag, you are creating a term. Posts, pages, and many other entities can the be associated with a term.  If we are running a barbecue blog, we might have a bunch of categories: Memphis Style, Texas Style, Carolina Style, Kansas City Style.  An article about some delicious brisket might be categorized under Texas.  Let's take this example and look at some potential queries.

## Querying for a term.

```
{
  term(id: yolo)
}
```



