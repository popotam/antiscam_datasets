# reddit_2014-02-19

A dataset of non-spam comments scrapped from reddit.com on 2014-02-19.

Bot starts with [Top topics page](http://www.reddit.com/top.json?sort=top&t=year) and enters each topic in order.
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
  "spam": "<boolean>"
}
```

If any other fields are present, they should be ignored.
