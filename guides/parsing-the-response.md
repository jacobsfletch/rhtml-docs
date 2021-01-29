# Parsing The Response

This guide will walk you through the process of parsing your image into a format you can more readily use.

### Stream to ArrayBuffer

When the fetch is successful, read the stream to completion using `arrayBuffer()`. It returns a promise that resolves to an [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer).

```javascript
const buffer = await res.arrayBuffer();
```

### ArrayBuffer to Base64

The `ArrayBuffer` can then be decoded to `Base64`, a format probably most familiar to you. Here's a fancy function save you from the trouble. Credit for this function belongs [here](https://stackoverflow.com/questions/9267899/arraybuffer-to-base64-encoded-string).

```javascript
const arrayBufferToBase64 = (buffer) => {
  let binary = '';
  const bytes = [].slice.call(new Uint8Array(buffer));
  bytes.forEach((b) => { binary += String.fromCharCode(b); });
  return window.btoa(binary);
}
```

Then just pass in the buffer through this function.

```javascript
const base64Image = arrayBufferToBase64(buffer)
```

### What to do now?

Rasterize HTML does not host your image. Once our servers respond with your image, it is entirely up to you to work with as needed. You could render the image onto a webpage, pass it around in memory, or save to disk.