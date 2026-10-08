# 升威 LE-RELAX — le-relax.co

A static website (plain HTML/CSS, no build step), ready for GitHub Pages.

| URL | Page |
|---|---|
| `/` | 香港主頁 (Traditional Chinese, default) |
| `/products/<series>/` | 9 product pages |
| `/glass/`, `/about/`, `/stores/` | 玻璃加工 · 關於升威 · 門市地址 |
| `/en/…` | English site (same structure, `contact/` instead of `stores/`) |

The old GoDaddy addresses (`/關於我們-about-us`, `/產品-products`, `/聯絡我們-contact-us`, `/68w`, etc.) are kept as redirect pages, so existing Google results and bookmarks still work.

---

## 1. Put it on GitHub (about 5 minutes)

1. Sign in at github.com → **New repository**. Name it `le-relax-website`, set it to **Public** and create it.
2. On the empty repo page, click **uploading an existing file**.
3. Drag in **everything inside this folder**, not the folder itself, so `index.html` sits at the top level. Click **Commit changes**.
   - The site has 128 files, and the browser uploader takes 100 at a time, so do it in two uploads:
     1. Everything **except** the `assets` folder (40 files). Commit.
     2. **Add file → Upload files** again, then drag in the `assets` folder itself (88 files). Commit.
   - Dragging a whole folder keeps its subfolders. Use Chrome or Edge, because Safari can flatten folders.
4. Go to **Settings → Pages**:
   - Source: *Deploy from a branch*
   - Branch: `main`, folder `/ (root)`. Save.
5. After about a minute, the site is live at `https://<your-username>.github.io/le-relax-website/`. Check it there before moving the domain.
   - Some links will look off on this temporary address. They will be fine on le-relax.co.

## 2. Move the domain from GoDaddy

**First, in GitHub:** go to Settings → Pages → Custom domain. Enter `le-relax.co` and save. The `CNAME` file in this folder already contains it.

**Then, in GoDaddy:** go to My Products → le-relax.co → **DNS**.

1. If the domain is attached to the GoDaddy Website Builder, remove that connection or unpublish the site first. Otherwise GoDaddy keeps overriding the records below.
2. Delete the existing **A** record(s) for `@` and the **CNAME** for `www`.
3. Add the following records:

| Type | Name | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | `<your-username>.github.io` |

4. **Do not touch MX / TXT records.** They run the company email.
5. Wait for DNS to update. This usually takes 15–60 minutes and can take up to 24 hours.
6. Back in GitHub Pages settings, tick **Enforce HTTPS** once it becomes available.

## 3. After launch

- **Google Search Console:** add `le-relax.co` and submit `https://le-relax.co/sitemap.xml`.
- **Google Business Profiles** for the three stores: set the website to `https://le-relax.co/stores/`.
- **English partner form:** it currently opens the visitor's email app, addressed to info@le-relax.hk. To receive enquiries without that step:
  1. Create a free form at formspree.io.
  2. In `en/index.html` and `en/contact/index.html`, replace `mailto:info@le-relax.hk?subject=…` in the `<form action="…">` with your Formspree URL.
  3. Delete `enctype="text/plain"`.

## 4. Editing later

Edit a page's `index.html` on GitHub (pencil icon) and commit. The live site updates in about a minute.

| What | Where |
|---|---|
| Phone numbers and WhatsApp links | Search the file for `wa.me/` or `tel:` |
| Images | `assets/img/` (`.webp`, with a `.jpg` fallback for social sharing) |
| Catalogues | `assets/docs/` |
| Shared styles | `assets/css/site.css` |
