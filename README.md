# edhensel.github.io

Official author website for Ed Hensel — author of *A Map, Not a Mystery: What the Bible Really Says About the End Times*.

**Live site:** https://edhensel.com
**Hosting:** GitHub Pages, served from the `main` branch. The custom domain is set by the `CNAME` file.

---

## Files

| File | Purpose |
|---|---|
| `index.html` | Home page — hero, three key ideas, author teaser, cross-link to Vanessa Hensel's book |
| `about.html` | Ed's bio and speaking call-to-action |
| `book.html` | Book detail page — showcase, description, "What You'll Discover", small-group note |
| `contact.html` | Contact form and contact info |
| `styles.css` | All site styling (single stylesheet, no build step) |
| `book-cover.jpg` | Flat cover, 1000×1499 — **social sharing only** |
| `book-cover-3d.png` | 3D mockup with transparent background — **on-page display only** |
| `ed-hensel.jpg` | Author photo |
| `favicon.svg` | Site icon |
| `sitemap.xml` | Search engine sitemap — update `lastmod` when pages change |
| `robots.txt` | Crawler directives |
| `CNAME` | Custom domain (`edhensel.com`) |

---

## Conventions

These are easy to get wrong. Read before editing.

### Two cover images, two jobs

- **`book-cover-3d.png`** is what visitors see on `index.html` and `book.html`. It has a transparent background, so it sits correctly on both the dark hero and lighter sections. Its drop shadow is baked into the image — **do not** add a CSS `box-shadow` or `border-radius` to it, or you'll get a rectangular shadow behind a non-rectangular book.
- **`book-cover.jpg`** is the flat 1000×1499 portrait cover. It is referenced only by the Open Graph, Twitter Card, and JSON-LD tags. Social platforms expect a clean book-cover ratio; the 3D mockup crops badly in link previews. **Leave the meta tags pointing at the flat cover.**

### Cache-busting the stylesheet

Every page loads the stylesheet as:

```html
<link rel="stylesheet" href="styles.css?v=YYYYMMDD">
```

Browsers cache CSS aggressively. **When you change `styles.css`, bump that date in all four HTML files**, or returning visitors will keep seeing the old styling and it will look like your change didn't deploy.

### Copy style

Visible page copy avoids insider theological labels. The three frameworks are described by what they claim, not by their technical names:

- "Much Was Already Fulfilled"
- "Christ Reigns Now"
- "God Keeps His Promises to Israel"

The technical terms are deliberately retained in the SEO metadata (`<meta name="description">`, Open Graph, Twitter, JSON-LD) so the site still surfaces for readers searching those terms. This split is intentional — don't "fix" it in either direction without meaning to.

### Contact form

`contact.html` posts to Formspree (`https://formspree.io/f/mbdpqqwb`). No server-side code, which is why it works on GitHub Pages. Submissions route through the Formspree account, not through any address published on the site — the site intentionally lists no email address.

---

## Deploying

There is no build step. Edit, commit, push:

```bash
git add -A
git commit -m "Describe the change"
git push origin main
```

GitHub Pages rebuilds in roughly a minute. If the change doesn't appear, hard-refresh (`Cmd+Shift+R`) before assuming the deploy failed — and if it was a CSS change, confirm you bumped the `?v=` date.

### Before you push

The working copy of this site also lives in a local project folder. **Those two can drift apart.** Pull first and diff before overwriting repo files with local copies, or you can silently delete sections that were added directly to the repo.

```bash
git pull
git diff
```

---

## Maintenance checklist

When you change page content:

- [ ] Update `lastmod` in `sitemap.xml` to today's date
- [ ] If you changed `styles.css`, bump `?v=` in all four HTML files
- [ ] If you changed a page title or description, check the matching Open Graph and Twitter tags
- [ ] Hard-refresh to verify, rather than trusting a normal reload
