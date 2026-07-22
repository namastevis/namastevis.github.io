# namastevis.in

Personal site — plain HTML/CSS/JS, no build step. Home, projects, and blog.

## Structure

```
index.html          home page
projects.html        project list
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

1. Keep the `CNAME` file in the repo root (already set to `namastevis.in`) — GitHub Pages uses it to know your custom domain.
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

- **Bio / links**: edit `index.html` — swap the placeholder bio and confirm the social links in the `.socials` block match your handles.
- **Add a project**: copy a `.card` block in `projects.html` and fill in the name, description, and repo link.
- **Add a blog post**: copy `blog/posts/hello-world.html`, rename it, update the title/date/content, then add a link to it at the top of `blog/index.html`.

## Local preview

No build tools needed — just open `index.html` in a browser, or serve the folder:

```
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.
