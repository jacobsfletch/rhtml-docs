# Capturing HTML

This guide will walk you through the process of capturing a screenshot of arbitrary HTML.

Send a `POST` request with the `html` parameter.

```bash
$ curl https://rhtml.io -u USERNAME:API_KEY -h "Content-Type:application/json" -d '{"html": "<p>Hello, world!</p>"}'
```
