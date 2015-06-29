# reddit_2015-06-29

A dataset of non-spam comments scrapped from reddit.com on 2015-06-29.

Bot starts with [Top topics page](http://www.reddit.com/top.json) and enters each topic in order.
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

When feed was collected on 2015-05-29 a total of 2804 topic pages were visited.
234168 comments were parsed.
Among them 56443 were rejected because they had the ups/downs balance lower than 5.
77716 comments were considered too short (less than 100 characters).
Finally, 100009 were collected and included in the feed data.
