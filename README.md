# arturekert — personal academic website

Plain static HTML + one stylesheet. No build step, no JavaScript, no dependencies.
GitHub Pages serves the files exactly as they are.

```
index.html          Home / About
lectures.html       C7.4 Introduction to Quantum Information
tutorials.html      Merton presentations + archive of past talks
writings.html       Writings (links into writings/)
404.html            Not-found page
assets/site.css     All styling (colours & fonts in :root at the top)
assets/fonts/       Cormorant Garamond + Lora, self-hosted woff2
assets/img/         Portrait
assets/favicon.svg  "AE" monogram
writings/           PDFs and standalone essays linked from writings.html
.nojekyll           Tells GitHub Pages to serve files as-is (skip Jekyll)
```

## Publish on GitHub Pages

1. Create an empty repository on GitHub, e.g. `arturekert.github.io`
   (this name gives the URL https://arturekert.github.io/ — any other name
   gives https://<user>.github.io/<repo>/; both work, all links are relative).
2. From this folder (Terminal: `cd ~/Documents/WWW/site`):
   ```sh
   git init -b main
   git add -A
   git commit -m "Initial site"
   git remote add origin https://github.com/<user>/<repo>.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   Branch **main**, folder **/ (root)** → Save. The site is live within a minute or two.

### Custom domain (optional, e.g. arturekert.org)
Settings → Pages → Custom domain → enter the domain (GitHub adds a `CNAME` file),
then at your DNS provider point the apex domain to GitHub's A records
(185.199.108.153, .109.153, .110.153, .111.153) and `www` as a CNAME to `<user>.github.io`.
Tick "Enforce HTTPS" once the certificate is issued.

## Everyday edits

- **Add a writing:** copy one `<li class="work">…</li>` block in `writings.html`,
  change title, link, venue, note. Put local files (PDF/HTML) in `writings/`.
- **New academic year of talks (tutorials.html):** move the talks under
  "This year's talks" into a new `<details>` block at the top of the archive
  (copy an existing year block, update the year and count), then add the new talks.
- **Change colours or fonts:** edit the variables at the top of `assets/site.css`.

Preview locally by opening `index.html` in a browser. Then:
```sh
git add -A && git commit -m "Update" && git push
```
