# Capturing Raw HTML

This guide will walk you through the process of capturing a screenshot or arbitrary HTML.

Send a `POST` request with the `html` parameter.

```bash
$ curl https://rhtml.io -u USERNAME:API_KEY -h "Content-Type:application/json" -d '{"html": "<p>Hello, world!</p>"}'
```

Read the [Capturing HTML](./guides/capturing-raw-html.md) guide for a detailed walk-through.