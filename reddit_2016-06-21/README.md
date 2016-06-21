# reddit_2016-06-21

A dataset of non-spam comments scrapped from reddit.com on 2016-06-21.

Bot starts with [Top topics page](http://www.reddit.com/top.json?sort=top&t=all) and enters each topic in order.
On each topic page single comments are scrapped.
Comments are considered valid if the following conditions are met:

* Comment is parsed correctly according to Reddit API docs
* Comment is ranked positivelly (number_of_thumbs_up - number_of_thumbs_down) > 5
* Comment is not too short (length > 1000)
* Comment is not reported as offensive by any user

Each document conforms to the following schema:

```json
{
  "id": "<unique string>",
  "content": {
    "comment": "<html>",
    "author": "<string>"
  },
  "spam": "<boolean>",
  "meta": {
    "ups": "<integer>",
    "downs": "<integer>"
  }
}
```

If any other fields are present, they should be ignored.

When feed was collected on 2016-06-21 a total of 6521 topic pages were visited.
529158 comments were parsed.
Among them 130604 were rejected because they had the ups/downs balance lower than 5.
176688 comments were considered too short (less than 100 characters).
Finally, 221866 were collected and included in the feed data.
