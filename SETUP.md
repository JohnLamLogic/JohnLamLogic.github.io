# GitHub Pages Setup & Domain Migration Guide

## Step 1 — Create the GitHub Repo

1. Go to https://github.com/new
2. Name it exactly: `JohnLamLogic.github.io`
3. Set it to **Public**
4. Do NOT initialize with a README (you'll push local files)
5. Click **Create repository**

---

## Step 2 — Push This Folder to GitHub

Open Terminal, then:

```bash
cd /Users/johnathonlamoreaux/Documents/GitHub/JohnLamLogic.github.io

git init
git add .
git commit -m "Initial portfolio site"
git branch -M main
git remote add origin https://github.com/JohnLamLogic/JohnLamLogic.github.io.git
git push -u origin main
```

---

## Step 3 — Enable GitHub Pages

1. Go to your repo on GitHub → **Settings** → **Pages**
2. Under "Branch", select `main` and `/ (root)`, click **Save**
3. Your site will be live at: `https://johnlamlogic.github.io`

---

## Step 4 — Set Your Custom Domain (johnlam.tech)

### In GitHub:
1. In **Settings → Pages → Custom domain**, type: `johnlam.tech`
2. Check **Enforce HTTPS** (may take a few minutes to activate)
3. GitHub will detect the `CNAME` file already in the repo

### In Your DNS Provider (wherever johnlam.tech is registered):
You need to point your domain at GitHub's servers.

**Add these A records** (delete any existing A records for `@` first):
```
Type: A    Host: @    Value: 185.199.108.153
Type: A    Host: @    Value: 185.199.109.153
Type: A    Host: @    Value: 185.199.110.153
Type: A    Host: @    Value: 185.199.111.153
```

**Add this CNAME record** for www:
```
Type: CNAME    Host: www    Value: johnlamlogic.github.io.
```

DNS changes propagate in 5–60 minutes. Once live, both `johnlam.tech`
and `www.johnlam.tech` will load your GitHub Pages portfolio.

---

## Files in This Repo

| File | Purpose |
|------|---------|
| `index.html` | Full portfolio site (single page) |
| `CNAME` | Tells GitHub Pages your custom domain |
| `_config.yml` | Jekyll metadata / SEO tags |
| `SETUP.md` | This guide |

---

## Updating the Site Later

Edit `index.html` locally, then:
```bash
git add index.html
git commit -m "Update projects section"
git push
```
GitHub Pages rebuilds automatically within ~1 minute.
