# ollamaclient.devart.solutions

Source code for [ollamaclient.devart.solutions](https://ollamaclient.devart.solutions) — the documentation site for the [OllamaClient](https://github.com/Dev-Art-Solutions/OllamaClient) .NET client library for [Ollama](https://github.com/ollama/ollama).

The site is a single static HTML page with no build step. All content lives in [`src/index.html`](src/index.html); assets and third-party libraries live under [`src/assets/`](src/assets/).

## Repository layout

```
src/
├── index.html              # the entire site
└── assets/
    ├── css/                # site stylesheet + colour themes
    ├── images/             # logo and favicon
    ├── js/                 # theme.js (sidebar scrollspy, back-to-top, etc.)
    ├── sass/               # Bootstrap source (not used at runtime)
    └── vendor/             # Bootstrap, FontAwesome, jQuery, highlight.js, Magnific Popup
```

## Preview locally

Any static file server will do. From the repository root:

```bash
# Python 3
python -m http.server 8080 --directory src

# Node
npx serve src

# .NET
dotnet serve -d src
```

Then open <http://localhost:8080/>.

## Editing the site

- **Content** — edit [`src/index.html`](src/index.html) directly. The sidebar (`.idocs-navigation`) and the page sections share IDs (`#idocs_*`); when you add a section, add the matching sidebar link so scrollspy keeps working.
- **Styles** — overrides go in [`src/assets/css/stylesheet.css`](src/assets/css/stylesheet.css). The `color-*.css` files are alternative accent themes shipped by the template — wire one in via `<link>` if you want to switch the accent colour.
- **Code samples** — wrap snippets in `<pre><code class="csharp">…</code></pre>` (or `bash`, `json`, etc.). `highlight.js` is initialised by [`src/assets/js/theme.js`](src/assets/js/theme.js) and picks up the language class automatically.

When the OllamaClient library changes, keep the following sections in sync with the library's [`README.md`](https://github.com/Dev-Art-Solutions/OllamaClient/blob/main/README.md) and [`CHANGELOG.md`](https://github.com/Dev-Art-Solutions/OllamaClient/blob/main/CHANGELOG.md):

- `#idocs_quickstart` — installation snippet and minimal usage
- `#idocs_api` — endpoint → method mapping table
- `#idocs_compatibility` — supported `.NET` / Ollama versions
- `#idocs_changelog` — release notes

## Deployment

The repository is served as-is from `src/`. Point your host (GitHub Pages, Netlify, Cloudflare Pages, Azure Static Web Apps, etc.) at the `src/` directory and the `main` branch.

## Related repositories

- [Dev-Art-Solutions/OllamaClient](https://github.com/Dev-Art-Solutions/OllamaClient) — the library this site documents
- [DevArt Solutions](https://devart.solutions) — the agency that maintains OllamaClient

## License

[MIT](LICENSE) © Dev-Art-Solutions
