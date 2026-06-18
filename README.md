# vgab.eu — Vikstrom Group AB website

Company site for Vikstrom Group AB, a Swedish IT consultancy. The landing page
introduces the firm and lists the products it builds alongside client work
(currently Rún, a private messenger); Rún has its own product page plus a
privacy policy and support page. Plain HTML/CSS, no build step —
deployable on any static host.

```
index.html      → https://vgab.eu/              Vikstrom Group AB (company)
run.html        → https://vgab.eu/run.html       Rún — product page
privacy.html    → https://vgab.eu/privacy.html   Rún — privacy policy
support.html    → https://vgab.eu/support.html   Rún — support
style.css       shared styles
favicon.ico     "VG" favicon — multi-size (16/32/48/64/256)
favicon.svg     "VG" favicon — scalable (modern browsers)
CNAME           custom-domain marker for GitHub Pages (contains: vgab.eu)
```

## Deploy via GitHub Pages + custom domain

1. Create a new **public** GitHub repo, e.g. `vgab-site`.
2. From this folder, push the files:
   ```
   git init && git add -A && git commit -m "Vikstrom Group AB website"
   git branch -M main
   git remote add origin git@github.com:cptdad/vgab-site.git
   git push -u origin main
   ```
3. Repo → **Settings → Pages** → Source: *Deploy from a branch*, Branch: `main` / `/ (root)` → Save.
4. **Pages → Custom domain:** `vgab.eu` (the included `CNAME` file already sets this) → Save.
5. At your **domain registrar** (where vgab.eu is registered), add DNS for the apex:
   - **A records** (host `@`) → GitHub Pages:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - GitHub also publishes **AAAA (IPv6)** records — add them from GitHub's current Pages docs if you want IPv6.
   - Optional `www`: **CNAME** `www` → `cptdad.github.io.`
6. Wait for DNS to propagate (minutes–hours), then **Pages → Enforce HTTPS**.

Verify the apex IPs against GitHub's current docs ("Managing a custom domain for
your GitHub Pages site") before relying on them.

## Before going public
- Legal name **Vikstrom Group AB** is set throughout. Confirm it matches the
  registered entity exactly (including the Swedish **ö** if it is "Vikström
  Group AB"), and that the AB is actually registered, before relying on the
  Privacy Policy's data-controller line.
- Optionally move the contact address to one on `vgab.eu` (registrar email
  forwarding), then update the `mailto:` links + the Privacy/Support contact.
