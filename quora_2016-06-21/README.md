# quora_2016-06-21

A dataset of non-spam answers scrapped from quora.com on 2016-06-21.

Bot starts with links in base_urls.csv and extract top topics (topics.csv).
From topic pages it extracts links to question pages (questions.csv).
On each question page top answers are scrapped.

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
