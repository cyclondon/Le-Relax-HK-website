# 升威 LE-RELAX — le-relax.co

A static website (plain HTML/CSS, no build step), ready for GitHub Pages.

| URL | Page |
|---|---|
| `/` | 香港主頁 (Traditional Chinese, default) |
| `/products/<series>/` | 9 product pages |
| `/glass/`, `/about/`, `/stores/` | 玻璃加工 · 關於升威 · 門市地址 |
| `/en/…` | English version for English speakers in Hong Kong (same pages, translated) |

The old GoDaddy addresses (`/關於我們-about-us`, `/產品-products`, `/聯絡我們-contact-us`, `/68w`, etc.) are kept as redirect pages, so existing Google results and bookmarks still work.

---

## 1. Put it on GitHub (about 5 minutes)

1. Sign in at github.com → **New repository**. Name it `le-relax-website`, set it to **Public** and create it.
2. On the empty repo page, click **uploading an existing file**.
3. Drag in **everything inside this folder**, not the folder itself, so `index.html` sits at the top level. Click **Commit changes**.
   - The site has about 140 files, and the browser uploader takes 100 at a time, so do it in two uploads:
     1. Everything **except** the `assets` folder (about 40 files). Commit.
     2. **Add file → Upload files** again, then drag in the `assets` folder itself (about 97 files). Commit.
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

## 3. After launch: get found on Google

Do these on launch day. Google shows the logo and site name only after it has crawled the new site, which usually takes a few days to a few weeks.

1. **Google Search Console** (search.google.com/search-console)
   - Add the property as a *Domain* (`le-relax.co`) and verify it with the TXT record it gives you. Add that record in GoDaddy DNS.
   - Under **Sitemaps**, submit `https://le-relax.co/sitemap.xml`.
   - Use **URL inspection** on the home page, then click *Request indexing*. This speeds up the logo and site name appearing.
2. **Google Business Profile**, one for each of the three stores (business.google.com):
   - Set the website to `https://le-relax.co/stores/`.
   - Add the hours (Mon–Fri 9–5, Sat 9–3, closed Sun and public holidays), photos and the main products.
   - Ask happy customers to leave a review. Reviews are the biggest factor for "near me" and district searches.
   - Rename the Tai Kok Tsui listing from "B D HOUSE LIMITED" to 升威 LE-RELAX if possible.
3. **Bing Webmaster Tools** (bing.com/webmasters): import from Search Console in one click. This also covers Yahoo and DuckDuckGo.
4. **Links from other sites:** ask the association, WACKER/KCC (distributor listings) and any trade directories to link to `https://le-relax.co/`.
5. **Check back in 4 weeks:** Search Console → *Performance* shows the actual searches you appear for.

**Already built in:**
- Page titles and descriptions written around the searches people make
- Logo and site name markup, so Google can show the 升威 logo next to your results
- Store locations, hours and map pins for Google
- FAQ and page-trail data, the sitemap, and links between the Chinese and English versions

## 4. Editing later

Edit a page's `index.html` on GitHub (pencil icon) and commit. The live site updates in about a minute.

| What | Where |
|---|---|
| Phone numbers and WhatsApp links | Search the file for `wa.me/` or `tel:` |
| Images | `assets/img/` (`.webp`, with a `.jpg` fallback for social sharing) |
| Catalogues | `assets/docs/` |
| Shared styles | `assets/css/site.css` |
