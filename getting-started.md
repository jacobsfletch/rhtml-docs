# Getting Started

If you have not yet retrieved your [API key](./authentication.md), do that first and then come back here.

There are two distinct ways to use this API:
  1. Screenshot entire webpages, or parts of them, that exist on live domains. Read [Capturing By URL](./guides/capturing-url.md) for a detailed walk-through.
  2. Screenshot arbitrary HTML that you pass in, in bulk or with dynamic content. Read [Capturing HTML](./guides/capturing-html.md) or [Using HTML Templates](./guides/using-html-templates.md) for detailed walk-throughs.

All screenshots are returned as an [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) for you to parse and work with freely. Read [Parsing Response](./guides/parsing-the-response.md) for details, or see the [full response](./api.md#response).

## Quick Start

### Screenshot URL

Send a `POST` request with the `url` parameter to `https://rhtml.io`.

```bash
$ curl https://rhtml.io \
  -u USERNAME:API_KEY  \
  -h "Content-Type:application/json" \
  -x POST \
  -d '{"url": "https://google.com"}'
```

Or capture just part of the page by passing the `selector` param.

Read [Capturing URL](./guides/capturing-url.md) for more.

### Screenshot HTML

Send a `POST` request with the `html` parameter to `https://rhtml.io`.

```bash
$ curl \
  -h "Content-Type:application/json" \
  -d '{"html": ["<p>Hello, world!</p>"]}' \
  -x POST \
  https://rhtml.io
```

Read [Capturing HTML](./guides/capturing-html.md) for more.

### Additional Parameters

You can continue to customize your image with additional parameters, see the [API](./api.md) for a list of everything possible.

## Resources

#### Postman

Use [Postman](https://www.postman.com/)? Here's a [boilerplate collection](./postman-collection.json) for you.
