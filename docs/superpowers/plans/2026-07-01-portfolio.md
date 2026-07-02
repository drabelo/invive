# dailton.com Portfolio Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the Invive landing page with a minimal centered personal-card portfolio for Dailton Rabelo, served by GitHub Pages at https://dailton.com.

**Architecture:** A single static `index.html` with inline CSS, no JavaScript, no build step. GitHub Pages serves the repo root on the `main` branch with a `CNAME` file for the custom domain.

**Tech Stack:** Plain HTML/CSS. Inter font from Google Fonts (only external asset).

## Global Constraints

- No JavaScript anywhere on the page.
- Total page weight under ~5 KB excluding the font.
- Exactly one external font: Inter from Google Fonts.
- Keep the `CNAME` file (contains `dailton.com`) — GitHub Pages needs it.
- Content is exactly: name, subtitle "Senior Software Engineer at Garner Health · New York", and three links (email `contact@dailton.com`, GitHub `https://github.com/drabelo`, LinkedIn `https://www.linkedin.com/in/drab-a2208562/`).

---

### Task 1: Sync remote CNAME commit

**Files:**
- None created; pulls `CNAME` committed by GitHub when the custom domain was set.

**Interfaces:**
- Produces: working tree containing `CNAME` with content `dailton.com`, up to date with `origin/main`.

- [ ] **Step 1: Pull from origin**

```bash
git pull --rebase origin main
```

Expected: fast-forward or rebase bringing in a commit that adds `CNAME`.

- [ ] **Step 2: Verify CNAME exists and is correct**

```bash
cat CNAME
```

Expected output: `dailton.com`

If `CNAME` does not exist after the pull (GitHub sometimes only stores the domain in settings), create it:

```bash
printf 'dailton.com\n' > CNAME
git add CNAME
git commit -m "chore: add CNAME for dailton.com"
```

### Task 2: Replace index.html with portfolio page

**Files:**
- Modify: `index.html` (full replacement)

**Interfaces:**
- Consumes: nothing from other tasks.
- Produces: the final page served at dailton.com.

- [ ] **Step 1: Replace the entire contents of `index.html` with:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Dailton Rabelo — Senior Software Engineer</title>
  <meta name="description" content="Dailton Rabelo is a senior software engineer at Garner Health in New York." />
  <meta property="og:title" content="Dailton Rabelo — Senior Software Engineer" />
  <meta property="og:description" content="Senior software engineer at Garner Health in New York." />
  <meta property="og:url" content="https://dailton.com" />
  <meta property="og:type" content="website" />
  <link rel="canonical" href="https://dailton.com" />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg:     #FAFAF8;
      --text:   #1A1A1A;
      --muted:  #6B6B66;
      --accent: #2456E6;
    }

    body {
      font-family: 'Inter', system-ui, -apple-system, sans-serif;
      background: var(--bg);
      color: var(--text);
      min-height: 100svh;
      display: grid;
      place-items: center;
      padding: 24px;
      -webkit-font-smoothing: antialiased;
    }

    main { text-align: center; }

    h1 {
      font-size: clamp(2rem, 6vw, 3rem);
      font-weight: 700;
      letter-spacing: -0.02em;
    }

    .subtitle {
      margin-top: 12px;
      font-size: clamp(1rem, 2.5vw, 1.125rem);
      color: var(--muted);
    }

    nav {
      margin-top: 36px;
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 8px 28px;
    }

    nav a {
      color: var(--text);
      font-weight: 500;
      text-decoration: none;
      border-bottom: 1px solid transparent;
      padding-bottom: 2px;
      transition: color .15s ease, border-color .15s ease;
    }

    nav a:hover, nav a:focus-visible {
      color: var(--accent);
      border-color: var(--accent);
    }
  </style>
</head>
<body>
  <main>
    <h1>Dailton Rabelo</h1>
    <p class="subtitle">Senior Software Engineer at Garner Health&nbsp;&middot;&nbsp;New York</p>
    <nav aria-label="Contact links">
      <a href="mailto:contact@dailton.com">Email</a>
      <a href="https://github.com/drabelo">GitHub</a>
      <a href="https://www.linkedin.com/in/drab-a2208562/">LinkedIn</a>
    </nav>
  </main>
</body>
</html>
```

- [ ] **Step 2: Verify in a browser**

```bash
open index.html
```

Check: content centered on desktop width; narrow the window to ~375px — no horizontal scroll, links wrap gracefully. All three links point to the right targets (hover to check status bar).

- [ ] **Step 3: Check page weight**

```bash
wc -c index.html
```

Expected: under 5000 bytes.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: replace Invive landing page with personal portfolio"
```

### Task 3: Remove old Invive design docs

**Files:**
- Delete: everything under `docs/superpowers/` that predates the portfolio work (old Invive specs/plans), keeping `docs/superpowers/specs/2026-07-01-portfolio-design.md` and `docs/superpowers/plans/2026-07-01-portfolio.md`.

**Interfaces:**
- Consumes/Produces: nothing shared.

- [ ] **Step 1: Remove old Invive docs and stray .DS_Store files (keep the two 2026-07-01 portfolio docs)**

```bash
git rm --quiet docs/superpowers/specs/2026-06-28-invive-landing-design.md docs/superpowers/plans/2026-06-28-invive-landing.md
find . -name .DS_Store -delete
```

- [ ] **Step 2: Commit**

```bash
git commit -m "chore: remove Invive design docs"
```

### Task 4: Push and verify live

**Files:** none.

- [ ] **Step 1: Push**

```bash
git push origin main
```

Note: the local `gh` token was reported invalid earlier. `git push` may use separate credentials and work fine; if it fails with an auth error, ask the user to run `gh auth login`.

- [ ] **Step 2: Wait for Pages build, then verify**

```bash
sleep 90 && curl -s https://dailton.com | grep -o '<title>[^<]*</title>'
```

Expected: `<title>Dailton Rabelo — Senior Software Engineer</title>` (if HTTPS cert still pending, use `curl -s http://dailton.com`).
