# Diamant Games — Studio Website

Static website for [diamantgames.com](https://diamantgames.com), hosted on GitHub Pages.

## Files

- `index.html` — Landing page
- `privacy-policy.html` — Privacy policy (linked from Google Play listings)
- `ads.txt` — Ad authorization file for AdMob
- `CNAME` — Custom domain config for GitHub Pages

## Deployment

### 1. Create GitHub repo

```bash
cd diamantgames-site
git init
git add .
git commit -m "Initial site: landing page, privacy policy, ads.txt"
git branch -M main
git remote add origin git@github.com:cemlas/diamantgames-site.git
git push -u origin main
```

### 2. Enable GitHub Pages

1. Go to **github.com/cemlas/diamantgames-site** → Settings → Pages
2. Under "Source", select **Deploy from a branch**
3. Select **main** branch, **/ (root)** folder
4. Click Save

### 3. Configure DNS in Cloudflare

Go to your Cloudflare dashboard → diamantgames.com → DNS and add:

| Type  | Name | Content                    | Proxy |
|-------|------|----------------------------|-------|
| A     | @    | 185.199.108.153            | DNS only |
| A     | @    | 185.199.109.153            | DNS only |
| A     | @    | 185.199.110.153            | DNS only |
| A     | @    | 185.199.111.153            | DNS only |
| CNAME | www  | cemlas.github.io           | DNS only |

> **Important**: Set proxy status to "DNS only" (grey cloud), not "Proxied" (orange cloud).
> GitHub Pages needs to handle SSL directly to issue the Let's Encrypt certificate.

### 4. Enable HTTPS

Back in GitHub repo → Settings → Pages:
- Wait for DNS to propagate (can take up to 30 minutes)
- Check "Enforce HTTPS" once available

### 5. Update ads.txt

Replace `pub-XXXXXXXXXXXXXXXX` in `ads.txt` with your actual AdMob publisher ID.
Find it in AdMob → Settings → Account Information.

## Updating the site

Edit files locally, commit, and push. GitHub Pages deploys automatically.

```bash
git add .
git commit -m "Update: description of changes"
git push
```
