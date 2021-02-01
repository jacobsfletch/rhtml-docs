# API

### Params

Either `url` _or_ `html` are required, but not both.

| Key | Type | Default | Description |
| - | - | - | - |
| `url`<span style="color:red">*</span> | `string` | `undefined` | |
| `selector` | `string` | `undefined` | any valid [CSS Selector](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors), scoped to `url` |
| `html`<span style="color:red">*</span> | `array` &#124;&#124; `object` | `undefined` | array of HTML strings, or an object if using `htmlTemplate`, [details here](./guides/using-html-templates.md)|
| `htmlTemplate` | `string` | `undefined` | HTML string, [details here](./guides/using-html-templates.md) |
| `type` | `'jpg'` &#124;&#124; `'png'` | `png` |  |
| `pdf` | `boolean` | `undefined` | injects your images into a PDF document |
| `transparent` | `boolean` | `true` | only if `type` is `png` |
| `quality` | `number` | `1` | between 0 and 1 |
| `beforeScreenshot` | `function` | `undefined` | a hook that returns the [Page](https://pptr.dev/#?product=Puppeteer&version=v5.5.0&show=api-class-page) before continuing |
| `screenshotOptions` | `object` | `undefined` | additional options to send through Puppeteer's [screenshot([options])](https://pptr.dev/#?product=Puppeteer&version=v5.5.0&show=api-pagescreenshotoptions) |

### Response

| Property | Type | Description |
| - | - | - |
| `totalImages` | `number` | total number of images generated |
| `images` | `array` | images generated, in same order as received |
| `pdf` | `object` | only if the `pdf` param was passed in |

#### `200 OK`

```json
{
  "totalImages": 1,
  "images": [{
    "type": "image/png",
    "size": 871,
    "document": {
      "type": "Buffer",
      "data": [127, 11, ...]
    }
  }],
  "pdf": {
    "type": "application/pdf",
    "size": 1003,
    "totalPages": 1,
    "document": {
      "type": "Buffer",
      "data": [99, 02, ...]
    }
  },
}
```

Read the [Parsing The Response](./guides/parsing-the-response.md) guide for how to process the document.

#### `500 Error`

```json
{
  "errors": [{
    "message": "You must provide either the url or the html property."
  }]
}
```
