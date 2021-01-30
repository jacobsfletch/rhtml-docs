# Capturing In Bulk

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

### HTML Templating

To generate images with dynamic content, add the `htmlTemplate` param.

Rasterize HTML uses [Handlebars](https://handlebarsjs.com/) templating. Pass an array of objects to the `html` param. Each key of these objects will be mapped to variable names made available in the `htmlTemplate`.

Just use double-curly-braces `{{likeThis}}`. Or dot-notation `{{like.this}}` for deeply nested objects.

```json
{
  "htmlTemplate": "<div>Planet {{name}}</div>",
  "html": [
    {
      "name": "Mars"
    },
    {
      "name": "<b>Earth</b>",
    }
  ]
}
```
