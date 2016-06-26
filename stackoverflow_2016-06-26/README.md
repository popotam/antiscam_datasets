# stackoverflow_2016-06-26

This folder contains two datasets of answers downloaded from stackoverflow.com on 2016-06-26.

Script used StackExchange API to download all answers to top rated questions on StackOverflow.
When feed was collected on 2016-06-21 a list of 68410 top rated questions was downloaded
via API and a total of 500000 answers were extracted and saved.

First dataset `stackoverflow_2016-06-26` contains all answers that were extracted.
Second dataset `stackoverflow_2016-06-26_upvoted` contains only answers that had score
greater or equal to 30. The dataset contains 101161 higly rated answers.

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

