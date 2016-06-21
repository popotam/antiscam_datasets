# reddit_2015-06-29

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
    "author": "<string>",
    "answer": "<html>"
  },
  "spam": "<boolean>",
  "meta": {
    "views": "<string>"
  }
}
```

If any other fields are present, they should be ignored.

When feed was collected on 2016-06-21 three links were visited (see base_urls.csv)
to gather a list of 105 most popular topics (topics.csv).
For each topic an overview, top answers and FAQ page was visited and a total of 2804
links to question pages were extracted (questions.csv).
Each question page was visited and top 5 answers were extracted for a total of 9520
documents.
