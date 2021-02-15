# Capturing HTML

To create an image, send an array of HTML strings through the `html` parameter. Each image will be returned to you in the same order it came.

## HTML

```json
{
  "html": [
    "<p>image 1</p>",
    "<p>image 2</p>"
  ]
}
```

In reality these HTML strings are typically retrieved from markup written elsewhere:
  - `document.getElementById().outerHTML`
  - `ref.current.outerHTML` for React apps
  - static `JSX`
  - text with line-breaks

Wherever your markup is defined, just stringify and/or minimize  before sending the request:

```javascript
.replace(/\n\s+|\n/g, '');
```

If your HTML is not written with inline CSS (most aren't), you will need to get its corresponding stylesheet and send that through as well. See [CSS](#css).

### Width, Height, Padding, etc

To control the size of your image, wrap your markup with the `html` and `body` tags. Then, define the `width` and `height` using inline CSS.

If your image needs padding, this may also be a good place for that.

```json
{
  "html": [
    "<html><body style="width: 1900; height: 1080px; padding: 100px;"><p>image 1</p></body></html>",
  ]
}
```

Alternatively, you could size your image with a stylesheet in the `head` tag that adds style to the `body`. See [CSS](#css).
## CSS

If your CSS is written using external stylesheets (as most are), you will need to wrap your markup with the `html` and `body` tags, and attach your stylesheet(s) to the `head` of the document.

```javascript
const withCSS = `<html><head><style>${yourStylesheet}</style></head><body><p>image 1</p></body></html>`;
```

It is important that you don't bloat the request with irrelevant CSS, and only the CSS needed to style your markup. How you retrieve your stylesheet is largely dependent on your individual setup. Fortunately, the browser provides a [native API](https://developer.mozilla.org/en-US/docs/Web/API/StyleSheetList) that may work for you.

If your page's markup is already reduced to only what is required for your image, just get it all:

```javascript
const getAllCSS = () => {
  const allCSS = [...document.styleSheets].map((styleSheet) => {
    try {
      const cssAsText = [...styleSheet.cssRules].map((rule) => rule.cssText).join('');
      return cssAsText;
    } catch (e) {
      console.warn('Access to stylesheet %s is denied. Ignoring...', styleSheet.href);
    }
    return null;
  }).filter(Boolean).join('\n');

  return allCSS;
};

const allCSS = getAllCSS();
```

To further optimize the request, consider [Using HTML Templates](./using-html-templates.md) to share stylesheet(s) or markup across all of your images.

## Additional Parameters

You can continue to customize your image(s) with additional parameters, see the [API](../api.md) for a list of everything possible.

## Response

Here's the [Full Response](../api.md#response) that will be returned to you. Read [Parsing The Response](./parsing-the-response.md) for how to process it.
