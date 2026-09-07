# Kathleen Yick — portfolio

A one-file portfolio site: About, Résumé, Projects, Life. `index.html` is the
entire thing — markup, styles, content and photos all live in that single file,
so there is nothing to build and nothing to install.

## Navigation

The four sections are tabs, not one long scroll — the top bar switches between
them. The open tab lives in the URL hash, so any page is linkable:
`#about`, `#resume`, `#projects`, `#life`. Add `/edit` to open the editor on
that page (`#projects/edit`); plain `#edit` works too.

## How the content is stored

All of the content sits in one JSON block inside `index.html`:

```html
<script type="application/json" id="portfolio-data"> … </script>
```

The page reads that block on load and renders itself from it. Photos and the
résumé PDF are stored inside it as data URIs, which is why the site needs no
asset folder — and why the file grows as you add images.

## Editing

**The editor is built into the page.** Open the site and click **Editor** in the
footer, or add `#edit` to the URL. A panel opens with every field: header, bio,
additional info rows, résumé PDF, projects (add / delete / reorder / categorise /
feature), and the Life section.

There are two ways to save what you change, depending on where you opened it:

| Where you opened the page | Save button | What it does |
| --- | --- | --- |
| The Claude-hosted copy | **Publish changes** | Saves a new version at the same URL, live immediately |
| A copy served from GitHub Pages (or opened locally) | **Export index.html** | Downloads the updated file — commit it and push |

The Claude-hosted copy is the comfortable place to edit, because Publish is one
click. The GitHub copy is the one employers see.

**The round trip:** edit on the Claude copy → Publish → **Export index.html** →
replace this repo's `index.html` with the downloaded file → commit and push.

Edits are also autosaved to your browser as you type, so a stray reload will not
lose work. Only Publish or Export makes them permanent.

## Publishing to GitHub Pages

Once this repo is on GitHub:

1. Repo **Settings → Pages**
2. **Source: Deploy from a branch**
3. **Branch: `main`**, folder **`/ (root)`**, then Save

The site goes live at `https://<username>.github.io/<repo>/` within a minute or
two. If you name the repo exactly `<username>.github.io`, it is served from
`https://<username>.github.io/` instead, with no path.

`.nojekyll` is here so GitHub serves the file as-is rather than running it
through Jekyll.

### Custom domain

Add a file named `CNAME` containing just your domain:

```
kathleenyick.com
```

Then point the domain's DNS at GitHub Pages (four `A` records for the apex, or a
`CNAME` record for `www`), and set the domain under Settings → Pages.

## Keeping the file small

Photos are resized to 1500 px and JPEG-compressed automatically when you add
them, and the editor footer shows the running page size. If it starts climbing
past a few megabytes, use **Add by URL** in the editor instead: upload the images
somewhere (including this repo, next to `index.html`) and reference them by
address, so they load separately rather than riding inside the page.

## External dependencies

One: the Google Fonts stylesheet for Archivo, Karla and DM Mono. Everything else
— the layout, the editor, the placeholder artwork — is in the file. If you ever
want the site to work with no external requests at all, the fonts can be inlined.
