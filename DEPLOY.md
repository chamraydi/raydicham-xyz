# Deploy to Vercel — Step by Step

## What you need
- A free GitHub account → github.com
- A free Vercel account → vercel.com
- Git installed on your Mac/PC (check: open Terminal and type `git --version`)
  - If not installed: download from git-scm.com

---

## STEP 1 — Create a GitHub repository

1. Go to **github.com** → click the **+** button (top right) → **New repository**
2. Name it `raydicham-xyz` (or anything you like)
3. Set it to **Public**
4. Leave everything else unchecked — **don't** add a README
5. Click **Create repository**
6. Copy the repository URL shown — looks like:
   `https://github.com/YOUR-USERNAME/raydicham-xyz.git`

---

## STEP 2 — Push the site files to GitHub

Open **Terminal** (Mac) or **Git Bash** (Windows) and run these commands one by one:

```bash
# 1. Go into the project folder (adjust path to where you unzipped it)
cd ~/Downloads/raydicham

# 2. Initialise git
git init

# 3. Add all files
git add .

# 4. First commit
git commit -m "initial portfolio"

# 5. Connect to your GitHub repo (paste your URL from Step 1)
git remote add origin https://github.com/YOUR-USERNAME/raydicham-xyz.git

# 6. Push
git branch -M main
git push -u origin main
```

Refresh your GitHub page — you should see all the files there.

---

## STEP 3 — Deploy on Vercel

1. Go to **vercel.com** → click **Sign Up** → choose **Continue with GitHub**
2. Authorise Vercel to access your GitHub
3. On the Vercel dashboard click **Add New → Project**
4. Find `raydicham-xyz` in the list → click **Import**
5. On the configure screen:
   - **Framework Preset** → select **Other**
   - **Root Directory** → leave as `/`
   - **Build Command** → leave blank
   - **Output Directory** → leave blank
6. Click **Deploy**

Vercel builds in ~15 seconds. You'll get a live URL like:
`https://raydicham-xyz.vercel.app`

---

## STEP 4 — Connect your custom domain (raydicham.xyz)

1. In Vercel dashboard → click your project → **Settings → Domains**
2. Type `raydicham.xyz` → click **Add**
3. Vercel shows you two DNS records to add. Go to wherever you bought the domain (GoDaddy, Namecheap, etc.)
4. Find **DNS settings** → add the records Vercel gives you:
   - Usually an **A record** pointing to `76.76.21.21`
   - And a **CNAME** for `www` pointing to `cname.vercel-dns.com`
5. Wait 5–30 minutes for DNS to propagate
6. Vercel auto-provisions an SSL certificate — your site is live at `https://raydicham.xyz`

---

## STEP 5 — Adding / updating images later

When you want to swap in new artwork:

```bash
# 1. Drop your images into raydicham/images/carousel/
# 2. Open index.html and replace placeholder divs with real images
# 3. Then run:

cd ~/Downloads/raydicham
git add .
git commit -m "add artwork"
git push
```

Vercel auto-detects the push and redeploys in ~15 seconds. Done.

---

## Swapping carousel images in index.html

Find the comment `<!-- CAROUSEL SLIDES -->` and replace each placeholder:

```html
<!-- BEFORE -->
<div class="cs sp1"><span>Replace with artwork · 1280×720</span></div>

<!-- AFTER — image -->
<div class="cs"><img src="images/carousel/01.jpg" alt="Project name"></div>

<!-- AFTER — video -->
<div class="cs">
  <video autoplay muted loop playsinline>
    <source src="images/carousel/reel.mp4" type="video/mp4">
  </video>
</div>
```

Image size: **1280 × 720px** (16:9). JPG or PNG. Keep under 500KB each for fast loading.

