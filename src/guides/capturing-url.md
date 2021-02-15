# Capturing URL

Take a screenshot of a webpage, or part of it.

### URL

Pass any publicly available website to the `url` parameter.

```json
{
  "url": "https://google.com"
}
```

### CSS Selector

To capture only part of the page, pass any valid [CSS Selector](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) to the `selector` parameter.

```json
{
  "url": "https://google.com",
  "selector": "div#id.class"
}
```

## Additional Parameters

You can continue to customize your image(s) with additional parameters, see the [API](../api.md) for a list of everything possible.

## Response

Here's the [Full Response](../api.md#response) that will be returned to you. Read [Parsing The Response](./parsing-the-response.md) for how to process it.
