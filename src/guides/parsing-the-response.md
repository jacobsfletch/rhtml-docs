# Parsing The Response

If you are not yet familiar with the [Full Response](./api.md#response), do that first and then come back here.

Each `document` of the response is an [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) which needs to be parsed into something more readily useable.

Rasterize HTML does not host your image. Once our servers respond with your `document`, so it is up to you to render on screen, keep in memory, or save to disk.

## ArrayBuffer To Base64

The `ArrayBuffer` can be decoded to `Base64`, a format probably most familiar to you. Fortunately this can be done with a basic function ([credit to this post](https://stackoverflow.com/questions/9267899/arraybuffer-to-base64-encoded-string)):

```javascript
const arrayBufferToBase64 = (arrayBuffer) => {
  let binary = '';
  const bytes = [].slice.call(new Uint8Array(arrayBuffer));
  bytes.forEach((b) => { binary += String.fromCharCode(b); });
  return window.btoa(binary);
}

const base64 = arrayBufferToBase64(document);
```

#### Data URL

Many times you'll want to use your `Base64` data as a [Data URL](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Data_URIs):

```javascript
const dataURL = `data:${MIME_TYPE};base64,${base64}`;
```

Just replace `MIME_TYPE` with the [`mimeType`](../api.md#document) of your document.
