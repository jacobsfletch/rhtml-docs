# API

## Params

Either `url` _or_ `html` are required, but not both.

| Key | Type | Default | Description |
| - | - | - | - |
| `url`<span style="color:red">*</span> | `string` | `undefined` | |
| `selector` | `string` | `undefined` | any valid [CSS Selector](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors), scoped to `url` |
| `html`<span style="color:red">*</span> | `array` &#124;&#124; `object` | `undefined` | array of HTML strings, or an object if using `htmlTemplate`, [details here](./guides/using-html-templates.md)|
| `htmlTemplate` | `string` | `undefined` | HTML string, [details here](./guides/using-html-templates.md) |
| `type` | `'jpg'` &#124;&#124; `'png'` | `png` |  |
| `pdf` | `boolean` | `undefined` | injects your images into a PDF document, [details here](./guides/creating-pdf.md) |
| `pdfOptions` | `object` | `undefined` | only if `pdf` is `true`, see [PDF Options](#pdf-options) for shape |
| `transparent` | `boolean` | `true` | only if `type` is `png` |
| `quality` | `number` | `1` | between 0 and 1 |
| `beforeScreenshot` | `function` | `undefined` | a hook that returns the [Page](https://pptr.dev/#?product=Puppeteer&version=v5.5.0&show=api-class-page) before continuing |
| `screenshotOptions` | `object` | `undefined` | additional options to send through Puppeteer's [screenshot([options])](https://pptr.dev/#?product=Puppeteer&version=v5.5.0&show=api-pagescreenshotoptions) |

#### PDF Options

Only applies if `pdf` is `true`.

| Key | Type | Default | Description |
| - | - | - | - |
| `orientation` | `'portrait'` &#124;&#124; `'landscape'` | `portrait` | |
| `width` | `number`  | `undefined` | in PDF points (72 per inch), overrides `size` |
| `height` | `number`  | `undefined` | in PDF points (72 per inch), overrides `size` |

## Response

| Property | Type | Description |
| - | - | - |
| `totalImages` | `number` | total number of images generated |
| `images` | `array` | images generated, in same order as received, see [Document](#document) for shape |
| `pdf` | `object` | if `pdf` is `true`, see [Document](#document) for shape |

#### Document

| Property | Type | Description |
| - | - | - |
| `mimeType` | `'image/png'` &#124;&#124; `'image/jpeg'` &#124;&#124; `'application/pdf'` | [MIME Type](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types) |
| `size` | `number` | in bytes |
| `totalPages` | `number` | if `type` is `application/pdf` |
| `document` | `buffer` | see [Parsing The Response](./guides/parsing-the-response.md) for how to work with buffers |

#### `200 OK`

```json
{
  "totalImages": 1,
  "images": [{
    "mimeType": "image/png",
    "size": 871,
    "document": {
      "type": "Buffer",
      "data": [127, 11, ...]
    }
  }],
  "pdf": {
    "mimeType": "application/pdf",
    "size": 1003,
    "totalPages": 1,
    "document": {
      "type": "Buffer",
      "data": [99, 02, ...]
    }
  },
}
```

#### `500 Error`

```json
{
  "errors": [{
    "message": "You must provide either the url or the html property."
  }]
}
```
