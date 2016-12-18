# Getting comments.

Conversation rarely comes in isolation.  Comment collections can help define the conversation around a specific topic. Let's look at querying for comments.

## Querying for comments.

```
{
  comments(first: 10) {
    content,
  }
}
```

This query will return a response like this:

```
{
  "data": {
    "comments": [
      {
        "content": "WordPress woohoo!",
      },
      {
        "name": "OMG you use WP!? That's awesome!",
      },
      {
        "name": "Proudly powered by WordPress",
      },
      {
        "name": "What if we had a thread and a blog -- as one?",
      },
      {
        "name": "Throgging?",
      },
      {
        "name": "This has already been done!",
      },
      {
        "name": "70% of the web is still closed source :(",
      },
      {
        "name": "Emoji, emoji, emoji.",
      },
      {
        "name": "Hi great article, the topic was riveting. I think you would be interested in using this new product that causes immense headaches and serves no purpose at all. Follow the link below to download a million viruses. Akismet didn't block me ;).",
      },
      {
        "name": "PHP is a toy language: said many people many times :(",
      },
    ]
  }
}
```

Comments can tell a story.  When comments are fully let loose an order of chaos that is unimaginable ensues.  Comments like posts, users and really any type of data in WordPress can contain sensitive information.  Make sure that you understand this and use WP GraphQL in a way that suits the needs of those using your WordPress installation.

