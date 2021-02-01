# Capturing HTML

This guide will walk you through the process of capturing a screenshot of arbitrary HTML.

Send a `POST` request with the `html` parameter.

```bash
$ curl https://rhtml.io -u USERNAME:API_KEY -h "Content-Type:application/json" -d '{"html": "<p>Hello, world!</p>"}'
```

### Why bulk?

- Consolidate number of requests
- Reduce individual request size
- Inject dynamic content

### Simple Array

The easiest way to generate images in bulk is to pass an array of strings to the `html` param. Each item in the array will be rendered individually and returned in the same order they came.

```json
{
  "html": [
    "<p>image 1</p>",
    "<p>image 2</p>"
  ]
}
```
