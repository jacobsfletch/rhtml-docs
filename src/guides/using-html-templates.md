# Using HTML Templates

Rasterize HTML uses [Handlebars](https://handlebarsjs.com/), a minimal templating language. If you're already familiar with it, this should feel intuitive to you.

## Dynamic Content

The concept is very simple and be thought of in two parts:

  1. Define a template, with [expressions](https://handlebarsjs.com/guide/#simple-expressions) that identify each piece of replaceable content
  2. Send it content, an array of objects whose keys are mapped to each expression defined in the template

### Template

To create a template, pass a string of HTML to the `htmlTemplate` param.

To identify replaceable content, use double-curly-braces `{{likeThis}}`, or with dot-notation `{{like.this}}`.

```json
{
  "htmlTemplate": "<div>Hello, {{name}}! Welcome to {{planet.name}}.</div>",
}
```
### Content

Then, pass an array of objects to the `html` param.

Each key will is mapped to the expressions defined in `htmlTemplate`.

```json
{
  "htmlTemplate": "<div>Hello, {{name}}! Welcome to {{planet.name}}.</div>",
  "html": [
    {
      "name": "Jane",
      "planet": {
        "name": "Earth"
      }
    },
    {
      "name": "John",
      "planet": {
        "name": "Mars"
      }
    }
  ],
}
```

## Additional Parameters

You can continue to customize your image(s) with additional parameters, see the [API](../api.md) for a list of everything possible.

## Response

Here's the [Full Response](../api.md#response) that will be returned to you. Read [Parsing The Response](./parsing-the-response.md) for how to process it.
