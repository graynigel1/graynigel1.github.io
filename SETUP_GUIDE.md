# Setup Guide: Getting Your Quarto Website Live on GitHub Pages

---

## What you have

Your site has these files:
```
_quarto.yml         ← site config (navbar, theme, etc.)
index.qmd           ← home page ✅
about.qmd           ← bio page ✅
research.qmd        ← publications ✅
teaching.qmd        ← teaching history ✅
cv.qmd              ← CV page (updated ✅)
projects.qmd        ← projects page (updated ✅)
html/custom.scss    ← your styling (updated ✅)
```

---

## Step 1 — Set up your local folder

Make sure all your files are in **one folder** on your computer, organized like this:

```
my-website/
├── _quarto.yml
├── index.qmd
├── about.qmd
├── research.qmd
├── teaching.qmd
├── cv.qmd
├── projects.qmd
├── html/
│   └── custom.scss
├── Images/
│   └── nigel.jpg        ← your profile photo
└── files/
    └── cv/
        └── nigel-gray-cv.pdf   ← YOUR CV PDF goes here
```

> **Note:** The folder `html/` must exist and contain `custom.scss` because  
> `_quarto.yml` references it as `html/custom.scss`.

---

## Step 2 — Update `_quarto.yml` (one small fix)

In your `_quarto.yml`, the theme line currently says:
```yaml
theme: [cosmo, html/custom.scss]
```
This is correct — no change needed as long as your `custom.scss` is inside a folder called `html/`.

---

## Step 3 — Add your CV PDF to the repo

1. In your website folder, create these subfolders: `files/cv/`
2. Place your CV PDF inside and name it `nigel-gray-cv.pdf`
   (or change the filename in `cv.qmd` to match yours)

---

## Step 4 — Build the site in RStudio

1. Open RStudio
2. Open the folder as a project: **File → Open Project** → navigate to your website folder
3. In the Terminal tab (bottom of RStudio), run:

```bash
quarto render
```

This builds your site into a folder called `docs/` (as set in `_quarto.yml`).  
You should see no errors. If you do, paste them and I can help fix them.

To preview it locally before pushing:
```bash
quarto preview
```
This opens a live preview in your browser.

---

## Step 5 — Push to GitHub

If you haven't connected your folder to GitHub yet:

```bash
git init
git remote add origin https://github.com/graynigel1/graynigel1.github.io
git add .
git commit -m "Initial site"
git push -u origin main
```

If already connected, just:
```bash
git add .
git commit -m "Update site"
git push
```

---

## Step 6 — Enable GitHub Pages

1. Go to your GitHub repo in your browser
2. Click **Settings** → **Pages** (left sidebar)
3. Under "Source", set it to: **Deploy from a branch**
4. Branch: `main` | Folder: `/docs`
5. Click **Save**

Your site will be live at `https://graynigel1.github.io` within ~2 minutes.

---

## What to fill in on projects.qmd

The `projects.qmd` file has placeholder text. Replace it with your real projects.  
For each tool or project, use this format:

```markdown
::: publication
### Your Tool Name

**Language**: R  
**Description**: What it does.  
**Repository**: [{{< fa brands github >}}](https://github.com/graynigel1/your-repo)
:::
```

---

## Common issues

| Problem | Fix |
|---|---|
| Site renders but looks unstyled | Make sure `html/custom.scss` exists in the right path |
| CV PDF shows blank | Double-check the path: `files/cv/nigel-gray-cv.pdf` |
| Profile photo missing | Make sure `Images/nigel.jpg` exists (capital I) |
| Icons (fa-*) not showing | The FontAwesome extension needs to be installed — run `quarto add quarto-ext/fontawesome` in Terminal |

---

## Questions?

Paste any error messages you get and I'll help debug them.
