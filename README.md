# Waiting for our Engagement! 💍

A single-page countdown site for Ayman & Dalia's engagement, with:
- A live countdown to **Aug 29, 2026, 7:00 PM**
- A **Yes** button that reveals the save-the-date invitation with a little heart animation
- A **No** button that runs away from your cursor/finger and can't be pressed

Everything lives in one file: `index.html` (fonts load from Google Fonts, everything else is self-contained — no build step, no dependencies).

## Deploy to GitHub Pages

**Option A — web browser only, no git required**
1. Go to https://github.com/new, name the repo (e.g. `ayman-dalia-engagement`), set it to **Public**, click **Create repository**
2. On the new repo page, click **"uploading an existing file"**
3. Drag in `index.html`, `README.md`, `.nojekyll`, and the `assets` folder (most browsers accept a dragged folder here; if yours doesn't, click "choose your files" and select `assets/invitation.jpg` — GitHub will recreate the `assets/` folder for you)
4. Commit the files
5. Go to **Settings → Pages**, under "Build and deployment" set **Source: Deploy from a branch**, **Branch: main**, folder **/(root)**, click **Save**
6. Wait ~1 minute, then your site is live at `https://<your-username>.github.io/<repo-name>/`

**Option B — git command line**
```bash
cd engagement-site
git init
git add .
git commit -m "Engagement countdown site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```
Then enable Pages the same way as step 5 above.

## Deploy to Netlify instead (drag & drop)

1. Go to https://app.netlify.com/drop
2. Drag the whole folder (or this zip file — Netlify accepts both) onto the page
3. Netlify gives you a live URL in a few seconds
4. Optional: in Site settings → Domain management, click "Options" → "Edit site name" to get a nicer URL, or add a custom domain

Note: some ISPs and DNS filters occasionally block the shared `*.netlify.app` domain (see the section below on custom domains) — GitHub Pages (`*.github.io`) is a good fallback since it's a different, widely-trusted domain.

## Customizing

Open `index.html` in any text editor:

- **Countdown target date** — near the top of the `<script>` block:
  ```js
  var target = new Date('2026-08-29T19:00:00+02:00').getTime();
  ```
  The `+02:00` assumes Cairo time. Change the date/time or offset if needed.

- **Names, venue, hall, time** — inside the `<section class="invite-card">` block (search for `Ayman`, `Dalia`, `EGYPT VIEW`, `LATOYA`, `7:00 pm`).

- **Colors** — at the top of the `<style>` block, under `:root`, e.g. `--rose` (Yes button), `--beige-btn` (No button), `--bg` (background).

- **How close the cursor needs to get before "No" runs away** — search for `95` (mouse) and `85` (touch) in the script (the `distanceToButton(...) < 95` checks).
