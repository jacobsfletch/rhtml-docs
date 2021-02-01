### Capturing URL

This guide will walk you through the process of capturing a screenshot of a webpage, or part of it.

Send a `POST` request with the  `url` parameter.

```bash
$ curl https://rhtml.io -u USERNAME:API_KEY -h "Content-Type:application/json" -d '{"url": "https://google.com"}'
```

Or capture just part of the page by passing any valid [CSS Selector](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) to the `selector` param.
