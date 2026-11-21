# Zola + Sveltia CMS Local Demo

Simple static blog built with [Zola](https://www.getzola.org/) and a browser-based
[Sveltia CMS](https://github.com/sveltia/sveltia-cms) editor. No PostgreSQL, no
Supabase, no Node.js backend — just one static-site-generator binary and one
static HTML page for the CMS UI.

## Prerequisites

- [Zola](https://www.getzola.org/documentation/getting-started/installation/) v0.17+ installed and on `PATH`.
- A modern browser (Sveltia CMS runs entirely client-side).
- [ngrok](https://ngrok.com/) (optional) only if you want to expose the local
  server for the CMS to be reachable from elsewhere, e.g. for demoing on
  another device.

## Project layout

- `zola.toml` — site config (base URL, title, search index, RSS feed).
- `content/` — Markdown content with TOML frontmatter (`content/blog/` holds
  the three sample articles).
- `templates/` — Tera templates: `base.html`, `index.html`, `section.html`,
  `page.html`.
- `static/style.css` — site stylesheet.
- `static/admin/index.html` — loads Sveltia CMS.
- `static/admin/config.yml` — CMS collection/field config for the `blog`
  collection.

## Validate the content and templates

```bash
zola check
```

This parses every piece of content and every template and verifies internal
links, without writing anything to disk. Run it after editing content or
templates and before serving.

## Run the site locally

```bash
zola serve --interface 127.0.0.1 --port 1111 --base-url /
```

- Site: http://127.0.0.1:1111/
- Blog index: http://127.0.0.1:1111/blog/
- RSS feed: http://127.0.0.1:1111/rss.xml
- Search index: generated automatically into `public/search_index.*.json`
  (built, not served live under `zola serve`'s in-memory mode).

## Open the CMS editor

Visit:

```
http://127.0.0.1:1111/admin/
```

Sveltia CMS loads from the unpkg CDN script in `static/admin/index.html` and
reads its collection config from `static/admin/config.yml`.

### Backend used here: `test-repo`

This demo config sets:

```yaml
backend:
  name: test-repo
```

`test-repo` is Sveltia/Netlify CMS's local testing backend. It does **not**
write back to the Markdown files in `content/blog/` and does **not** talk to
GitHub, GitLab, or any git host. Every edit, new entry, and delete you make
in the `/admin/` UI is persisted only in your browser's local storage. Reload
the page in the same browser and your changes are still there; open the site
in a different browser, clear site data, or deploy the real Markdown files
elsewhere, and none of those CMS edits travel with it. This is intentional
for this demo — it lets you try the full editing UI, including the
rich-text body field, without wiring up a real git backend or auth.

## Expose the server externally (optional)

If you want to reach this local instance from another machine or device
(e.g. to demo the CMS on a phone), tunnel port 1111:

```bash
ngrok http 1111
```

Use the `https://*.ngrok-free.app` (or similar) URL ngrok gives you in place
of `http://127.0.0.1:1111` — append `/admin/` to reach the CMS the same way.
Note `zola.toml`'s `base_url` stays `http://localhost:1111`; for a real
deployment behind ngrok/HTTPS you'd normally override `base_url` to match,
but for this local demo it is left as-is.

## Build a static output (optional)

```bash
zola build
```

Outputs the full static site to `public/`, ready to be served by any static
file host.
