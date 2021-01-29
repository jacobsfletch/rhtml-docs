# Getting Started

If you have not yet retrieved your [API key](./authentication.md), do that and come back. Read the [Authentication](./guides/authentication.md) guide if need any help.

There are two distinct ways to use this API:
  1. Screenshot entire webpages, or parts of them, that exist on live domains. Read [Capturing By URL](./guides/capturing-by-url.md).
  2. Screenshot arbitrary HTML that you pass in. Read [Capturing HTML](./guides/capturing-raw-html.md).

If you are here to capture images in bulk, that falls under the second category. Read the [Capturing In Bulk](./guides/capturing-in-bulk.md) guide for more information.

All responses return an [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) for you to parse and work with freely. For help with that, read the [Parsing Response](./guides/capturing-in-bulk.md) guide for help there.

## Quick Start

### Screenshot by URL

Send a `POST` request with the  `url` parameter to `https://rhtml.io`.

```bash
$ curl https://rhtml.io -u USERNAME:API_KEY -h "Content-Type:application/json" -d '{"url": "https://google.com"}'
```

Or capture just part of the page by passing any valid [CSS Selector](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) to the `selector` param.

Read the [Capturing URL](./guides/capturing-by-url.md) guide for a detailed walk-through.

### Screenshot by HTML

Send a `POST` request with the  `html` parameter to `https://rhtml.io`.

```bash
$ curl https://rhtml.io -u USERNAME:API_KEY -h "Content-Type:application/json" -d '{"html": "<p>Hello, world!</p>"}'
```

Read the [Capturing HTML](./guides/capturing-raw-html.md) guide for a detailed walk-through.

### Parameters

You can continue to customize your image with additional parameters, see the [API](./api.md) for a list of everything possible.

## Resources

#### Postman

Use [Postman](https://www.postman.com/)? Here's a [boilerplate collection](./postman-collection.json) for you.