# Austin Real Pros — transition page (now with Live 512 Real Estate)

A single static page hosted on **GitHub Pages**. No WordPress, no hosting bill, no plugins to patch. The whole site is `index.html` plus a couple of images in `assets/`.

The page announces that Austin Real Pros has wound down as an independent brokerage and that Carrie York and Bill Evans have joined **Live 512 Real Estate**, then gives visitors a direct way to reach them.

---

## 1. Add the images

The page expects these in `assets/`. Grab the current broker photos from the live WordPress site before it's taken down:

| Save as (in `assets/`) | Download from |
|------------------------|---------------|
| `carrie-york.jpg`      | https://austinrealpros.com/wp-content/uploads/2016/12/broker-carrie.jpg |
| `bill-evans.jpg`       | https://austinrealpros.com/wp-content/uploads/2016/12/broker-bill.jpg |
| `favicon.png` *(optional)* | https://austinrealpros.com/wp-content/uploads/2016/09/cropped-arp-icon-270x270.png |

If a photo is missing, the page falls back to the person's initials in a circle, so it won't look broken. If Carrie has a newer Live 512 headshot she'd rather use, just save it as `carrie-york.jpg` and it drops right in.

## 2. Create the repo & deploy

1. Create a new GitHub repo (public or private both work with Pages).
2. Upload everything to the repo root: `index.html`, `CNAME`, `.nojekyll`, `README.md`, and the `assets/` folder.
3. Repo **Settings → Pages → Build and deployment** → Source **Deploy from a branch**, Branch **`main` / `(root)`**, Save.
4. It publishes at `https://<username>.github.io/<repo>/`, then switches to the custom domain once DNS is set.

## 3. Point the domain (keep www.austinrealpros.com)

`CNAME` is already set to `www.austinrealpros.com`. At the domain's DNS provider:

**www**
```
Type: CNAME   Host: www   Value: <username>.github.io
```
**apex → www** — use the registrar's redirect to `https://www.austinrealpros.com`, or point A records at GitHub:
```
Type: A   Host: @   Value: 185.199.108.153
Type: A   Host: @   Value: 185.199.109.153
Type: A   Host: @   Value: 185.199.110.153
Type: A   Host: @   Value: 185.199.111.153
```
Then **Settings → Pages → Custom domain**, confirm the green check and tick **Enforce HTTPS**.

> Changing DNS cuts the domain over from the WordPress host to GitHub Pages. Make the switch once the repo is live and images are in.

## 4. Editing later

Everything is in `index.html` — phone numbers, emails, and copy are plain text. Edit in GitHub's web editor, commit, and the site updates in under a minute. No build step.
