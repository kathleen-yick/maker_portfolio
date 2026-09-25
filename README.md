# Kathleen Yick — portfolio

A one-file portfolio site: **About Me · Resume · Projects · Life**.
`index.html` is the whole site. There is nothing to install and nothing to build:
edit the file, commit, push, and GitHub Pages serves it.

```
portfolio_website/
├── index.html      the site (content + styles + script, in four labelled parts)
├── images/         put photos here, e.g. images/gripper-1.jpg
├── resume.pdf      (add this yourself) shown on the Resume tab
├── .nojekyll       tells GitHub to serve the file as-is
└── README.md       this file
```

## Editing the site

Open `index.html` in any text editor. It is split into four parts, each with a
banner comment:

| Part | What it is | Touch it? |
| --- | --- | --- |
| **1 · Your content** | Title, bio, info rows, resume file, projects, life page | **Yes, this is the whole job** |
| 2 · Styles | The `THEME` block at the top holds colours and font | Colours and font only |
| 3 · Page skeleton | Empty containers the script fills | No |
| 4 · Script | Builds the page from Part 1 | No |

Part 1 is plain JavaScript data. The rules that matter:

- Text sits inside `"quotes"` or `` `backticks` ``. Backticks can span many lines,
  and a blank line inside them becomes a new paragraph.
- **Every line inside `{ }` or `[ ]` ends with a comma.** A missing comma is the
  usual reason the page goes blank. If that happens, a red box at the top of the
  page reports the browser's error message.
- Leave a value as `""` to hide it.

### Adding a project

Inside `const PROJECTS = [ ... ]` there is a boxed template in a comment. Copy
it, paste it into the list, and fill in the fields:

```js
{
  title: "Project name",
  category: "engineering",      // engineering | design | personal
  year: "2026",
  blurb: "One or two sentences shown under the thumbnail.",
  description: `
The full write-up, shown when the project is opened.

Blank line = new paragraph.
  `,
  images: ["images/name-1.jpg", "images/name-2.jpg"],
  role: "What you did",
  tools: "Software, materials, languages",
  link: "",                     // optional URL
  featured: false,              // true = also on the About page (first three shown)
},
```

Only `title`, `category` and `blurb` are required. Several images make a
slideshow with arrows; the first image is the thumbnail. Projects are sorted
newest year first unless you set `projectsNewestFirst: false` in `SITE`.

### Photos

- Save them in `images/`, lower-case names, no spaces: `images/gripper-1.jpg`.
- Resize before adding. Around 1600 px on the long side and under 400 KB each
  keeps the site fast. Preview or any image editor can export at that size.
- Reference them by path: `"images/gripper-1.jpg"`.

### Resume

Save the PDF next to `index.html` as `resume.pdf`, then set
`file: "resume.pdf"` in `RESUME`. Until then the tab shows the `note` text.

### Colours and font

In the `THEME` block near the top of Part 2 every colour is a named variable
with a comment saying where it is used. The font is loaded from Google Fonts
in the `<head>`; to change it, swap the family name there and in `--font`.

## Checking your changes

Double-click `index.html` to open it in a browser. Everything works from a
local file. If the resume PDF refuses to show that way, serve the folder
instead:

```
python3 -m http.server 8000
```

and open <http://localhost:8000>.

Every tab has its own address, so pages are linkable: `#about`, `#resume`,
`#projects`, `#projects/design`, `#life`.

## Publishing

```
git add index.html images resume.pdf
git commit -m "Add <project name>"
git push
```

GitHub Pages redeploys within a minute or two.

First-time setup, once the repo is on GitHub: **Settings → Pages → Source:
Deploy from a branch → Branch `main`, folder `/ (root)` → Save.** The site
appears at `https://<username>.github.io/<repo>/`. Naming the repo exactly
`<username>.github.io` serves it from `https://<username>.github.io/` instead.

### Custom domain

Add a file named `CNAME` containing just the domain (`kathleenyick.com`), point
the domain's DNS at GitHub Pages, and set the domain under Settings → Pages.

## Dependencies

One: the Google Fonts stylesheet for Exo 2. Everything else is in the file.
