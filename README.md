<p align="center">
    <img src="https://user-images.githubusercontent.com/8983173/130322857-185831e2-f041-46eb-a17f-0a69d066c4e5.png" alt="Gotenberg Logo" width="150" height="150" />
    <h3 align="center">Gotenberg</h3>
    <p align="center">A containerized API for seamless PDF conversion</p>
    <p align="center">
        <a href="https://hub.docker.com/r/gotenberg/gotenberg"><img alt="Total downloads (gotenberg/gotenberg)" src="https://img.shields.io/docker/pulls/gotenberg/gotenberg"></a>
        <a href="https://hub.docker.com/r/thecodingmachine/gotenberg"><img alt="Total downloads (thecodingmachine/gotenberg)" src="https://img.shields.io/docker/pulls/thecodingmachine/gotenberg"></a>
        <a href="https://github.com/gotenberg/gotenberg/actions/workflows/continuous-integration.yml"><img alt="Continuous Integration" src="https://github.com/gotenberg/gotenberg/actions/workflows/continuous-integration.yml/badge.svg"></a>
        <a href="https://pkg.go.dev/github.com/gotenberg/gotenberg/v8"><img alt="Go Reference" src="https://pkg.go.dev/badge/github.com/gotenberg/gotenberg.svg"></a>
    </p>
    <p align="center">
        <a href="https://trendshift.io/repositories/2996"><img src="https://trendshift.io/api/badge/repositories/2996" alt="gotenberg%2Fgotenberg | Trendshift" style="width: 250px; height: 55px;" width="250" height="55"/></a>
    </p>
    <p align="center"><a href="https://gotenberg.dev/docs/getting-started/introduction">Documentation</a> &#183; <a href="https://gotenberg.dev/docs/getting-started/installation#live-demo-">Live Demo</a> 🔥</p>
</p>

---

**Gotenberg** provides a developer-friendly API to interact with powerful tools like Chromium and LibreOffice for converting
numerous document formats (HTML, Markdown, Word, Excel, etc.) into PDF files, and more!

## Quick Start

Open a terminal and run the following command:

```
docker run --rm -p 3000:3000 gotenberg/gotenberg:8
```

Alternatively, using the historic Docker repository from our sponsor [TheCodingMachine](https://www.thecodingmachine.com):

```
docker run --rm -p 3000:3000 thecodingmachine/gotenberg:8
```

The API is now available on your host at http://localhost:3000.

Head to the [documentation](https://gotenberg.dev/docs/getting-started/introduction) to learn how to interact with it 🚀

## New HTML Rendering APIs 🆕

Gotenberg now includes powerful HTML rendering endpoints that allow you to capture the rendered HTML content from various sources. These endpoints complement the existing PDF and screenshot generation capabilities.

### Available HTML Rendering Endpoints

#### 1. Render HTML from URL
**POST** `/forms/chromium/html/url`

Renders HTML content from a remote URL and returns the processed HTML source.

```bash
curl -X POST \
  -F "url=https://example.com" \
  http://localhost:3000/forms/chromium/html/url \
  --output rendered.html
```

#### 2. Render HTML from File Upload
**POST** `/forms/chromium/html/html`

Processes uploaded HTML files and returns the rendered HTML content.

```bash
curl -X POST \
  -F "index.html=@index.html" \
  http://localhost:3000/forms/chromium/html/html \
  --output rendered.html
```

#### 3. Render HTML from Markdown
**POST** `/forms/chromium/html/markdown`

Converts Markdown files to HTML and returns the rendered content.

```bash
curl -X POST \
  -F "index.html=@template.html" \
  -F "file.md=@content.md" \
  http://localhost:3000/forms/chromium/html/markdown \
  --output rendered.html
```

### Supported Options

All HTML rendering endpoints support the same powerful options as the PDF and screenshot endpoints:

- **Browser Options**: `waitDelay`, `waitForExpression`, `waitWindowStatus`
- **Network Options**: `skipNetworkIdleEvent`, `failOnHttpStatusCodes`
- **Headers & Authentication**: `extraHttpHeaders`, `cookies`, `userAgent`
- **Display Options**: `emulatedMediaType`, `omitBackground`

### Example with Options

```bash
curl -X POST \
  -F "url=https://example.com" \
  -F "waitDelay=2s" \
  -F "emulatedMediaType=screen" \
  -F "userAgent=Custom Bot 1.0" \
  http://localhost:3000/forms/chromium/html/url \
  --output rendered.html
```

### Use Cases

- **Web Scraping**: Extract fully-rendered HTML content after JavaScript execution
- **Content Processing**: Capture dynamic content for further analysis
- **Template Testing**: Validate HTML template rendering
- **SEO Analysis**: Get the complete rendered HTML as search engines see it
- **Content Archival**: Save fully-processed HTML snapshots

## Sponsors

<p align="center">
    <a href="https://thecodingmachine.com">
        <img src="https://user-images.githubusercontent.com/8983173/130324668-9d6e7b35-53a3-49c7-a574-38190d2bd6b0.png" alt="TheCodingMachine Logo" width="333" height="163" />
    </a>
    <a href="https://pdfme.com?utm_source=gotenberg_github&utm_medium=website" target="_blank">
        <img src="https://github.com/user-attachments/assets/2a75dd40-ca18-4d34-acd5-5dd474595168" alt="pdfme Logo" width="333" height="163" />
    </a>
</p>

Sponsorships help maintain and improve Gotenberg - [become a sponsor](https://github.com/sponsors/gulien) ❤️
