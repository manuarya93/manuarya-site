# Getting manuarya.com live — step by step

This site is a static site (built with Eleventy) with a real content dashboard (Decap CMS)
built in. No coding needed after this point — everything below is clicking through
free web dashboards (GitHub, Netlify, GoDaddy).

Total time: ~30-45 minutes. You only do this once.

---

## 1. Push the site to GitHub

1. Go to https://github.com and sign in (or create a free account).
2. Click **New repository**. Name it `manuarya-site` (private or public, your choice).
3. Don't initialize with a README (we already have one).
4. On your computer, open a terminal in this project folder and run:

   ```
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/manuarya-site.git
   git push -u origin main
   ```

   Replace `YOUR-USERNAME` with your GitHub username. GitHub will show you this
   exact command on the empty repo page too — you can copy it from there instead.

---

## 2. Connect it to Netlify (free hosting)

1. Go to https://app.netlify.com and sign up / log in (you can use "Sign up with GitHub").
2. Click **Add new site → Import an existing project → GitHub**.
3. Pick the `manuarya-site` repository.
4. Build settings should auto-detect from `netlify.toml`:
   - Build command: `npm run build`
   - Publish directory: `_site`
5. Click **Deploy site**. In ~1 minute you'll get a live URL like
   `random-name-123.netlify.app` — open it and confirm the site loads.

---

## 3. Turn on the content dashboard (Decap CMS)

Decap CMS is already built into the site at `/admin`. To let you log in and
edit content, turn on two free Netlify features:

1. In your Netlify site dashboard: **Site configuration → Identity → Enable Identity**.
2. Under Identity settings, set **Registration** to "Invite only" (so no one else
   can sign up).
3. Still under Identity, scroll to **Services → Git Gateway → Enable Git Gateway**.
   This lets the CMS save changes back to GitHub on your behalf.
4. Go to the **Identity** tab (top nav of your Netlify site) → **Invite users** →
   enter your own email (manuarya93@gmail.com) → send invite.
5. Check your email, click the invite link — it'll ask you to set a password on
   your live site.
6. Now visit `https://YOUR-SITE.netlify.app/admin/`, log in with that email/password,
   and you'll see the dashboard: Home Page, About Page, Work/Projects, Writing/Blog,
   Contact Page, Site Settings. Every text field, image, and blog/project entry is
   editable there — no code required.

**Uploading photos:** In the CMS, any "Image" field has an upload button. Download
the photo from Google Photos to your computer first, then upload it there — it gets
committed straight into the site and appears live after ~1 minute rebuild.

---

## 4. Point manuarya.com (GoDaddy) at Netlify

1. Back in Netlify: **Site configuration → Domain management → Add a domain** →
   enter `manuarya.com` → follow the prompts.
2. Netlify will show you DNS records to add. The simplest path is usually:
   - Log into GoDaddy → **My Products → DNS** for manuarya.com.
   - Add an **A record**: Host `@`, Value `75.2.60.5` (Netlify's load balancer IP —
     Netlify's domain screen will confirm the current value to use).
   - Add a **CNAME record**: Host `www`, Value `YOUR-SITE.netlify.app`.
   - Remove any conflicting default GoDaddy "parked domain" A/CNAME records.
3. DNS changes can take anywhere from a few minutes to a few hours to propagate.
4. Back in Netlify, once it detects the DNS, click **Verify DNS configuration**,
   then enable **HTTPS** (Netlify issues a free SSL certificate automatically).
5. Your site is now live at `https://manuarya.com`.

---

## Editing content going forward

You never need to touch code again for text/photo changes:

- Go to `manuarya.com/admin`, log in, edit anything, click **Publish**.
- Changes go live automatically (~1 minute) via Netlify rebuilding the site.

If you ever want a developer to add a new page type or redesign something, this
whole folder is the project — hand it to them as-is.

## Placeholder content

Everything marked "EDIT ME" throughout the site (bio, project descriptions,
blog posts) is draft placeholder text built from your LinkedIn headline and
what's known about your work (product/strategy consulting, startup investing,
renewable energy/EPC and SPV structuring). Go through the CMS and replace it
with your own words before sharing the link widely. Placeholder images are
abstract gradient graphics — swap them for real photos the same way.
