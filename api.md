# API

Either `url` _or_ `html` are required, but not both.

| Key | Type | Default | Description |
| - | - | - | - |
| `url`<span style="color:red">*</span> | `string` | `undefined` | |
| `selector` | `string` | `undefined` | Any valid [CSS Selector](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors), scoped to `url` |
| `html`<span style="color:red">*</span> | `string` &#124;&#124; `array` | `undefined` | Any valid [HTML](https://developer.mozilla.org/en-US/docs/Web/HTML) |
| `htmlTemplate` | `string` | `undefined` | See [templates](./templates.md) |
| `type` | `jpg` &#124;&#124; `png` | `png` |  | 
| `transparent` | `boolean` | `true` | Only if `type` is `png` | 
| `quality` | `number` | `1` | Between 0 and 1 | 
| `beforeScreenshot` | `function` | `undefined` | Returns the page to you for further processing | 
| `screenshotOptions` | `object` | `undefined` | Additional options to send through Puppeteer's [screenshot([options])](https://pptr.dev/#?product=Puppeteer&version=v5.5.0&show=api-pagescreenshotoptions) | 
