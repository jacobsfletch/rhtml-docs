# Contributing

### Technical

#### Routes

Routes are dynamically generated based on the contents of the `src` directory as `/docs/:topic/:doc`. Add a new document to an existing topic, or create a new one if necessary.

#### Links

All markdown links `[label](url)` are piped through `next/router` when rendered. Any absolute paths are automatically opened in a new tab. All other links should use relative paths (`./` and `../`).
