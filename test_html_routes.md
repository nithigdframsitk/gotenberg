# Test HTML Routes

This document describes how to test the new HTML routes added to Gotenberg.

## New Routes Added

1. `POST /forms/chromium/html/url` - Get rendered HTML from a URL
2. `POST /forms/chromium/html/html` - Get rendered HTML from an HTML file
3. `POST /forms/chromium/html/markdown` - Get rendered HTML from Markdown files

## How to Test

### 1. URL to HTML
```bash
curl -X POST \
  http://localhost:3000/forms/chromium/html/url \
  -F 'url=https://example.com' \
  --output rendered.html
```

### 2. HTML file to rendered HTML
```bash
curl -X POST \
  http://localhost:3000/forms/chromium/html/html \
  -F 'files=@index.html' \
  --output rendered.html
```

### 3. Markdown to HTML
```bash
curl -X POST \
  http://localhost:3000/forms/chromium/html/markdown \
  -F 'files=@index.html' \
  -F 'files=@content.md' \
  --output rendered.html
```

## Supported Options

All routes support the same options as the screenshot routes:

- `skipNetworkIdleEvent`
- `failOnHttpStatusCodes`
- `failOnResourceHttpStatusCodes`
- `failOnResourceLoadingFailed`
- `failOnConsoleExceptions`
- `waitDelay`
- `waitWindowStatus`
- `waitForExpression`
- `cookies`
- `userAgent`
- `extraHttpHeaders`
- `emulatedMediaType`
- `omitBackground`

Example with options:
```bash
curl -X POST \
  http://localhost:3000/forms/chromium/html/url \
  -F 'url=https://example.com' \
  -F 'waitDelay=2s' \
  -F 'emulatedMediaType=print' \
  --output rendered.html
```
