# Creating A PDF

If you have not yet created images, [do that first](../getting-started.md) and then come back here.

Each image corresponds to one page within the generated PDF, which can be sized and oriented. Each image will be placed

## Opt-in

To have your images injected into a multi-page PDF document, just pass the `pdf` parameter as `true`:

```json
{
  "pdf": true
}
```

### Global Options

By default every page in your PDF will be sized as `letter` in `portrait` orientation. You can override this and more by passing the `pdfOptions` object:

```json
{
  "pdf": true,
  "pdfOptions": {
    "orientation": "landscape",
    "width": 612, // 8.5 inches in PDF points (72 per inch)
    "height": 792, // 11 inches in PDF points (72 per inch)
  }
}
```

### Page Options

**Note**: This feature not yet released, here's a glimpse into what the API _might_ look like.

Individual pages can be controlled just the same with the `pages` array. You can also determine individual image size and placement on the each page using [these options](http://pdfkit.org/docs/images.html).

```json
{
  "pdf": true,
  "pdfOptions": {
    "pages": [{
      "orientation": "portrait",
      "width": 612,
      "height": 792,
      "imageSize": {
        "width": 612,
        "height": 792,
        "fit": true
      }
    }],
  }
}
```
## Additional Parameters

You can continue to customize your PDF with additional parameters, see the [API](./api.md) for a list of everything possible.

## Response

Here's the [Full Response](./api.md#response) that will be returned to you. Read [Parsing The Response](./guides/parsing-the-response.md) for how to process it.
