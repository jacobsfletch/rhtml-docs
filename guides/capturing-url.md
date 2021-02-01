### Capturing URL

This guide will walk you through the process of capturing a screenshot of a webpage, or part of it.

Send a `POST` request with the  `url` parameter.

```bash
$ curl https://rhtml.io -u USERNAME:API_KEY -h "Content-Type:application/json" -d '{"url": "https://google.com"}'
```

Or capture just part of the page by passing any valid [CSS Selector](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) to the `selector` param.

## Additional Parameters

You can continue to customize your image(s) with additional parameters, see the [API](./api.md) for a list of everything possible.

## Response

Here's the [Full Response](./api.md#response) that will be returned to you. Read [Parsing The Response](./guides/parsing-the-response.md) for how to process it.
