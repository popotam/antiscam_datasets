# spam_trap_2014-02-06

A dataset of spam comments collected by honeypot farm of WordPress instances from 2013-06-01 to 2014-02-06.

Each document conforms to the following schema:

```json
{
  "id": "<unique string>",
  "content": {
    "comment": "<wordpress_markup>",
    "author": "<string>",
    "email": "<email>",
    "url": "<url>"
  },
  "spam": "<boolean>",
  "meta": {
      "server_plugin_time": "<timestamp>",
      "request_data": {
          "<HTTP header name>": "<HTTP header value>"
      }
  }
}
```

If any other fields are present, they should be ignored.
