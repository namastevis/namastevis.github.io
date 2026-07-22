# namastevis.in

Personal site, plain HTML/CSS/JS, no build step. Light, subtle theme. Portfolio landing, about, and blog.

Layout: every page uses a sticky header (name + tagline + nav) and sticky footer (socials), with only the middle content area scrolling. Works the same on mobile.

Each work card on the homepage has two link zones: the thumbnail image opens the project's GitHub repo, and the title/description area opens the live site. Both open in a new tab. There's no separate internal case-study page to maintain.

## Structure

```
index.html          portfolio landing (intro + Work grid, links out to live projects)
about.html           about me
blog/index.html      blog post list
blog/posts/*.html    individual posts
css/style.css        shared styles
CNAME                custom domain for GitHub Pages
```

## Deploy on GitHub Pages

1. Create a repo named exactly `namastevis.github.io` on GitHub.
2. Push these files to the `main` branch (root, not a subfolder).
3. In the repo, go to **Settings → Pages** and confirm the source is `main` / `/ (root)`.
4. Your site will be live at `https://namastevis.github.io` within a few minutes.

## Point namastevis.in at it

1. Keep the `CNAME` file in the repo root (already set to `namastevis.in`). GitHub Pages uses it to know your custom domain.
2. At your domain registrar's DNS settings for `namastevis.in`, add:
   - Four **A records** for the apex domain (`@`) pointing to GitHub Pages' IPs:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - Optionally a **CNAME record** for `www` pointing to `namastevis.github.io`.
3. Back in **Settings → Pages**, enter `namastevis.in` as the custom domain and save. Wait for DNS to propagate (can take up to a few hours), then enable **Enforce HTTPS**.

## Editing content

- **Intro**: edit the `.intro` section in `index.html`.
- **About page**: edit the sections in `about.html`.
- **Add a project**: copy a `.work-card` block inside `.work-grid` in `index.html`. It has two links: `.work-thumb` (the image, `href` to the GitHub repo) and `.work-body` (the title/description, `href` to the live site). Update both URLs, the thumbnail image, title, description, and tag. The grid reflows automatically as cards are added, no layout changes needed.
- **Add a blog post**: copy `blog/posts/hello-world.html`, rename it, update the title/date/content, then add a link to it at the top of `blog/index.html`.
- **Socials**: the footer is repeated on every page. Update all handles in the `.footer-inner` block across `index.html`, `about.html`, and `blog/**/*.html` if they ever change.

## Local preview

No build tools needed, just open `index.html` in a browser, or serve the folder:

```
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.
