# Getting a user

A user in WordPress can be an author, a subscriber, an editor, and administrator, or anything really.  Remember that the user data and user object represent a real person \(in most cases, could be a robot\).  WordPress in its current iteration is a very post centric design and GraphQL, will enable a more fluid shift towards a user centric design.  Using user data comes with many responsibilities, a responsibility to uphold individual privacy, a responsibility to accommodate many different kinds of people, and a responsibility to make the experience enjoyable.

## Querying for a user

Let's grab a user.  In this case we will pretend the user is an author of ten posts.

```
{
  user(id: 10) {
    name,
    avatar(size: 96) {
      url
    }
    posts(first: 10) {
      title,
      content
    }
  }
}
```

And the response will look something like this.

```
{
  "data": {
    "user": {
      "name": "Tom",
      "avatar": {
        "url": "http://2.gravatar.com/avatar/bc11b699a2e59027c7c8ce4e90dfc4a1?s=96&d=mm&r=g"
      },
      "posts": [
        {
          "title": "Post 101",
          "content": "Sample text"
        },
        {
          "title": "Post 100",
          "content": "Howdy, howdy."
        },
        {
          "title": "Post 99",
          "content": "Capital P dangit!"
        },
        {
          "title": "Post 98",
          "content": "Yolo"
        },
        {
          "title": "Post 97",
          "content": "Beyond Yolo"
        },
        {
          "title": "Post 96",
          "content": "The build has failed ¯\_(ツ)_/¯"
        },
        {
          "title": "Post 95",
          "content": "The build has passed :)"
        },
        {
          "title": "Post 94",
          "content": "Is GraphQL good? ¯\_(ツ)_/¯"
        },
        {
          "title": "Hello World!",
          "content": "Hello World!"
        },
        {
          "title": "Post 92",
          "content": "Clean code"
        }
      ]
    },
  }
}
```

Tom appears to be a person of few words.

## Privacy & Security

\(WP GraphQL currently has no security mechanisms in place as it is not meant for production use yet.\)

Grabbing data beyond this enters into the realm of potentially private data. In some cases, this already has.  It is always important to consider the privacy implications surrounding your code.  WP GraphQL will be designed to mirror the distinctions between private and public data in WordPress, potentially with some minor adjustments \(most likely not\).  When the security features for WP GraphQL are built in there will also be the ability for developers to override WP GraphQL's configurations, allowing you to either expand the data that is publicly available, further restrict it, or add a different layer of authentication/authorization.

