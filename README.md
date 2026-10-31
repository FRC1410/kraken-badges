# Kraken proficiency pages

Each student gets a page at `yoursite/<slug>` showing every badge, with earned ones in color and the rest greyed out. Tapping a badge shows what it means and when it was earned. The bare site URL shows the roster.

## Files

- `index.html` is the page. You shouldn't need to touch it.
- `data.json` holds all badges and students. This is the only file you edit.
- `404.html` is a copy of `index.html` (needed for GitHub Pages, see below).
- `_redirects` sends every path to `index.html` (needed for Netlify).

## Awarding a badge

Open `data.json`, find the student, and add a line to `earned`:

    { "badge": "cad1", "date": "2026-11-04" }

## Adding a student

Add an entry to `students`. The `slug` is what goes in the URL and on their NFC sticker, so keep it short, lowercase, no spaces (`alexr`, not `Alex R`).

## Adding a badge

Add an entry to `badges`. `icon` can be an emoji or an image file path like `icons/cad1.png` (put the image in an `icons` folder). Badges are grouped on the page by `category`, in the order they appear in the file.

## Hosting

Works on any static host.

- **GitHub Pages:** push these files to a repo and turn on Pages. GitHub serves `404.html` for `/alex`, and that file is the same page, so it reads the name from the URL. If the site lives in a subfolder (`user.github.io/kraken-badges/`), add `<base href="/kraken-badges/">` inside `<head>` in both HTML files.
- **Netlify / Cloudflare Pages:** drag the folder in. `_redirects` handles routing.
- **Anywhere else:** `index.html?s=alex` always works without any routing setup.

Note: opening `index.html` straight from your computer won't load the data. It has to be served over http.

## NFC stickers

Write each student's URL (e.g. `https://kraken.org/alex`) to an NTAG213/215 sticker with the NFC Tools app, then lock it. Use anti-metal tags if the sticker sits on metal.
